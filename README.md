# Project Overview


## Backend

### Technologies
- **Python**
  - `uv` for project dependencies and environment management
  - `ruff` for linting and formatting
  - Performance optimization via:
    - **C Python modules** for speed-ups
    - **Go** (via `github.com/go-python/gopy@latest`) for additional flexibility
      ```bash
      gopy build -output=./mypackage ./mypackage
      ```
      - Pros: Usable across backend services
      - Cons: Go's garbage collection overhead

## Frontend

### Technologies
- **JavaScript with React**
- **Electron** for desktop applications
  - Web code layers directly onto Electron, minimal OS interaction
  - Future considerations for local cache database
- **Electron-builder** for packaging:
  - macOS, Windows, Debian, RPM, AppImage

## Integrations

Priority levels: ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic) ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic) ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)

| Integration   | Priority |
|---------------|----------|
| Zotero        | ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic)     |
| Google Drive  | ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic)    |
| Obsidian      | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |
| Notion        | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |
| Atlassian     | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |
| OneDrive      | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |
| Dropbox       | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |

## Features

### Book & Chapter Management
- Users can create **Books**, either:
  - Joining an **Org** (for sharing and database/LLM management)
  - Using cloud hosting (paid customers)
- Each book is an org, with the creator as the default owner
- Chapters assigned to individual users within the org
- Sharing Options:
  - **Snapshot**: One-time copy
  - **Live Share** (Proxy updates via backend)
  - **Direct Connection** (Instant updates, more secure)
  - Public books at `read.ragstack.com`

### Database Support

**Cloud Services:**
- Vector DB: CromaDb
- Object DB: S3 / R2
- SQL DBs:
  - PostgreSQL (account management)
  - MySQL (chat history)
- Caching: KeyDB

**User-hosted Databases:**

| Type      | Supported Options                                   |
|-----------|----------------------------------------------------|
| Vector    | ChromaDB, Milvus, Pinecone, Weaviate, Qdrant |
| SQL       | PostgreSQL, MySQL, MSSQL, Firestore, Aurora        |
| Object    | Any S3-compatible store                            |

### File Format Support

#### High Priority ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic)  
- **Documents:** `.doc, .docx, .rtf, .pdf, .wpd, .txt, .md, .csv` 
- **Programming Files:** `.bat, .sh, .html, .css, .htm, .xhtml, all code files processed as .txt`

#### Medium Priority ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic)
- **Images:** `.jpeg, .png, .gif, .heif, .bmp, .tif, .webp, .eps`
- **Audio:** `.mp3, .wav, .wma, .aac`

#### Low Priority ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic) 
- **Video:** `.3gp, .mp4, .avi, .mpg, .mov, .wmv`

## LLM Support

| Provider      | Priority |
|---------------|----------|
| OpenAI        | ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic)     |
| Google        | ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic)     |
| Ollama        | ![HIGH](https://img.shields.io/badge/PRIORITY-HIGH-red?style=plastic)     |
| Anthropic     | ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic)    |
| Meta          | ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic)    |
| HuggingFace   | ![MID](https://img.shields.io/badge/PRIORITY-MID-orange?style=plastic)    |
| Cohere        | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |
| NVIDIA        | ![LOW](https://img.shields.io/badge/PRIORITY-LOW-green?style=plastic)     |

## Key Considerations

- **Web Scraping:** Needs to store website URLs and images
- **Metadata:** Utilize vector DB for tagging
- **Automation Scripts:**
  - Terraform for cloud deployments
  - Docker images for cloud/local use
- **Tunnels:** Future implementation for LAN-hosted DBs

## Future Ideas

- Introduce public book sharing with proxy services
- Cloud deployment automation with Terraform
- Local and cloud support via Docker


