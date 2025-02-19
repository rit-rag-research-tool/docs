Backend in Python 
- UV for project dependencies and environments
- ruff for linter and formatter
- (I can make C python modules for speed ups in the backend, but we could also use GO and github.com/go-python/gopy@latest to build like "gopy build -output=./mypackage ./mypackage"  
Since i think using Go is better here as we can use it other places in the backend, but its not going to be as clean as C bcouse of the GC overhead )

fruntend in JS with React
- electron for desktop 
(we should be able to just layer the web code right onto electron becouse the app should not have to deal with the OS very much and 
whatever needs to be done with the os can be abstracted away by electron, for example we dont need to have a db, down the line it 
could be good to have a local cach db, but the app should work with no os hooks and just lest electron handel the OS)
- electron-builder for Mac, win, deb, rpm, AppImage

Integrations
- this is specifically for retrieving documents, for example, you could have an integration with Google Drive and you could define what folder inside your Google Drive or what documents you want us to pull 
- Zotero (HIGH)
- Google (MID)
- Obsidian (LOW)
- Notion (LOW)
- atlassian (LOW)
- Onedrive (LOW)
- Dropbox (LOW)

-- NAMES ARE SUBJECT TO CHANGE --

- users can create Books when they create a book they can ether join a book ( this is for ORGS who want to enable sharing / managment of the database / LLM ) they can connect there own database and LLM or if they 
are a paying custmer they can slect cloud and the Book will be auto created with our info so we can host for them.

all books are created as an ORG, when a user creates a book they will be auto set as the owner with sharing turned on by default, so it will feel very natrial for a solo user, then chapters
under a book are assigned to a user in the org, so if you are a solo user and yo create a chapter in a book it will feel very clean and easy, but say you have a kid and you want to invite them to your book
becouse you dont want to set them up there own serevrs, they wont be able to see your chapters and you cant see there chapters bhecouse they are asigned to difrent pople in the org 
( you as the own can go into admin view to see all chapters in a book)


- as long as the app (running localy can see the endpoint for your DB its fair game, this will enable people to host apps on there LAN or localhost, it should be noted that without a tunel (this is somthing we could add later)
users who host there db and llm localy will be able to see there books but will not be able to connect to there books)

- books can have chapters, chapters are the equilavent to "notebooks" for notebooklm each notebook is a collection of files that you will be able to inetract with. 

- chapters can be shared with other people, they can ether be shared as a copy, mening that the user will get a snapshot of the shared chapter at the time of sharing pulled into there book - 
(if a book is set up as an org then admins can disable sharing chapters outside of the book)
chapters can also be live shared where we can offer proxying updates to the file through our backend to pretect the server hosting the db but will have a 10min update intervinetvul or 1m intervul for paying custmers 
or users can share a direct connection to a chapter, this will be a direct connection to the server hosting the db, we will make this as scure as posable but this should still be for trusted pople, 
the benifit is instant updates becouse we dont need to proxy the connection

- live sharing has a few permitions add, remove, edit, prompt passthrough (this is to expose the llm connected to the book if set to true the owner of the file will have there llm handle interactionjs from pople they have shared with 
if set to false the user who is being shared with will have the llm auto configured to the book they add the chapter too, even if set to true the user who is being shared with can use there own llm if they want more safety)


- could have somthing where users can make books or chapters public so pople can serhc for topics that have some other usre precompiled the data, say at read.ragstack.com 
(users who did this would have to proxy there connections through us and can not enable prompt passthrough)

file formats 
- .doc, .docx, .rtf, .pdf, .wpd, .txt, .md, .rtf, csv, (HIGH)

- .JPEG, .PNG, .GIF, .HEIF, .bmp, .tif, .webp, .eps (MID)

- .mp3, wav, .wma, .aac, (MID)

- .3gp, .mp4, .avi, .mpg, .mov, .wmv (LOW)

- .bat, .sh, .html, .css, .htm, .xhtml, all other programing lang files will be prossessed as txt files (HIGH)

Cloud vector DB 
- CromaDb ( we can use the metdata to filter but i was told by the croma team that the cloud server that we are runing has some restrictioons on len of Metadata, they did not tell me the len though. depening on if this gives up problmes we may move the metadata to a sql db)

Cloud object DB 
- S3 or R2

Cloud sql DB for account managment
- PostgreSQL

Cloud sql db for chat history 
- MySQL

Cloud cashing server
- keydb

User vector DBs 
- CromaDb (HIGH)
- Milvus (MID)
- Pinecone (MID)
- Weaviate (LOW)
- Qdrant (LOW)
- pgvector (LOW)

User SQL DBs 
- PostgreSQL
- MySQL
- Microsoft SQL Server
- Firestore 
- Aurora 

User Object DBs 
- anything that uses the S3 standard should be fine 

LLM Suport
- OpenAI (HIGH)
- Google (HIGH)
- Ollama (HIGH)
- Anthropic (MID)
- Meta (MID)
- HuggingFace (MID)
- Cohere (LOW)
- NVIDIA (LOW)


KEY THOUGHTS 

- Podcast is not important if needed this can be done much later.
- the build in webscraper will need to save website urls and images 
- use meta data in the vector db for tags 

IDEAS
- i am thinking throught how the sharing will work, and users will need to run there own MySQL for chat history,  vector db and object store. 
- we could have a few scrips set up for users to help automate setting up this like terraform for cloud deployments and auro pervision of resorses or a docker image for cloud and local  
