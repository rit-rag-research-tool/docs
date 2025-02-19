## File Upload:

Frontend -> Backend: File is hashed.
Backend checks hash in KeyDB.
If found, update metadata; if not, store the file in S3 (or local storage) and KeyDB.
Embedding Generation:

Trigger child process or task queue for embedding.
Return immediate success to the user with embedding job ID.
User Management:

Use SQL relationships to manage books, chapters, and access permissions.
Include roles (admin, contributor, viewer) for better access control.



## File Upload & Hashing:

Files are hashed (e.g., using SHA-256 or similar) to create a unique fingerprint.
The hash is used as a key in a KeyDB instance to store metadata about the file.
Metadata Storage in KeyDB:

The metadata JSON contains details like upload time, the server storing the file, and a list of user IDs who have access.
If the file already exists (hash found in KeyDB), you append the user ID and update the JSON.
Embedding and Metadata Handling:

After deduplication is confirmed, a child process handles embeddings and metadata generation.
This step allows further use of the file for applications like search or recommendation systems.
Frontend Handling:

The embedding process is asynchronous, with the frontend monitoring progress via a separate endpoint.


## Security for Hash Lookup
To prevent users from hashing arbitrary files and querying the database:

Authenticated Uploads: Only allow authenticated users to upload files.
Rate Limiting: Implement rate limits for hash lookups to avoid abuse.
Pre-Signed Uploads: Use pre-signed URLs for uploads, verifying user permissions before generating these URLs.
Hash Salt (Optional): Add a server-side salt to hashes before lookup to make direct hash generation harder for users.




i want to be able to use DNA to optimize storage, my first thought for this was for the cloud storage we will offer, as we won’t want to store a photo or some text that someone else has already stored, we just want to store a pointer to that text so that many people can use it, I think this will make the backend more complex, but could save on loads of storage, and I think the same thing could apply to local hosting as well, with some ORGS having docs that many people will want to use and it would be best not to burden the server with storaing the same doc 2 times

but I also don't want people to be able to post random request to try and just get to hashes they have not uploaded themself, is there anyway where when a file gets uploaded do you think this will work to solve the problem:

file upload

hash the file 
check hash on keydb server will be hash:json 

where the json is 

{
    "uploaded": datetime
    "server":ip
    "users": list of ids
}

keydb will return the json or none 
if json then we know we have the file alread and we just go to add the hash database under the book that the user uploade the file to
we then take that json and add the user id of the user who uploaded the file and make an update to the keydb server for the key ( sine this request is handeled on the server the catch server and user ids who have access to a file are hiden from enduser)
then we spin up a child prosses to handel the embeding and metadata for the file, we return sucess to the user as well an ID for the embeding and metadata request (the fruntend will use this id on a difrent endpoint to monader and see updates on the embeding)

sql database is layed out like: 
table user_info username, hashed_pw, salt, id, books [list of fgn keys]
table book_info id, ip (the is the ip of the vector db), name, discription, database_type, users[list of fgn keys so we books can check if a user should be able to access them], chapters[list of fgn keys]
table chapter_info id, name, discription, users[list of fgn keys so we books can check if a user should be able to access them], file[list of hashes]


text, slides, photos, pdf --> embeding 
video, audio gemini 1.5 flash --> text --> embeding 