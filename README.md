# StreamSync-Collaborative-AI-Video-Summarizer

StreamSync is a collaborative AI-driven video summarization tool. Upload or link lengthy videos—lectures, podcasts, or webinars—and receive chapter breakdowns, concise summaries, and a searchable transcript. Collaborate in real-time to refine chapters and annotate key moments.

## Tech Stack
- AI/ML: PyTorch
- API: FastAPI
- Back-End: ASP.NET Core

## Requirements
- Transcript generation from video/audio (e.g., using Whisper or an external transcription API)
- AI chapter and summary generation (using LLMs with prompt templates for structured output)
- Collaborative annotation system (store user contributions per timestamp)

## Installation

### Python & FastAPI (AI + API)
bash
# 1. Clone the repo
git clone https://github.com/your-org/StreamSync-Collaborative-AI-Video-Summarizer.git
cd StreamSync-Collaborative-AI-Video-Summarizer

# 2. Create a virtual environment
python3 -m venv venv
source venv/bin/activate

# 3. Install Python dependencies
pip install -r requirements.txt


Create a `.env` file in the project root with:
env
OPENAI_API_KEY=your_openai_api_key
TRANSCRIPTION_API_KEY=your_transcription_service_key
MODEL_NAME=your_preferred_llm_model


### ASP.NET Core (Back-End)
bash
# 4. Navigate to ASP.NET project folder
cd backend

# 5. Restore NuGet packages
dotnet restore

# 6. Build the project
dotnet build


Configure your database connection string in `appsettings.json` under the `ConnectionStrings` section.

## Usage

1. Start the FastAPI service (AI & transcription):
   bash
   uvicorn api.main:app --reload --host 0.0.0.0 --port 8000
   
2. Start the ASP.NET Core back-end:
   bash
   cd backend
   dotnet run
   
3. Open the front-end (if included) or use API endpoints to upload videos, fetch transcripts, chapters, and manage annotations.

## Implementation Steps

1. Set up the FastAPI project structure and virtual environment.
2. Integrate Whisper (or external API) for transcript generation.
3. Define prompt templates and integrate an LLM via PyTorch for chapter and summary generation.
4. Build ASP.NET Core services for user management and annotation storage.
5. Design the database schema to store videos, transcripts, chapters, summaries, and timestamped annotations.
6. Implement FastAPI endpoints for video upload/linking, transcription, and chapter generation.
7. Implement ASP.NET Core controllers for retrieving and updating collaborative annotations.
8. Add authentication and authorization to secure API endpoints.
9. Write unit and integration tests for both FastAPI and ASP.NET Core modules.
10. Deploy using Docker or your preferred cloud service.

## API Endpoints

### FastAPI (AI + Transcription)
- `POST /api/videos/upload` - Upload a video file.
- `POST /api/videos/link` - Provide a URL for transcription.
- `GET /api/videos/{id}/transcript` - Retrieve generated transcript.
- `GET /api/videos/{id}/chapters` - Retrieve AI-generated chapters and summaries.

### ASP.NET Core (Annotations)
- `POST /annotations` - Add or update an annotation at a timestamp.
- `GET /annotations/{videoId}` - Fetch all annotations for a video.
- `PUT /annotations/{id}` - Modify a specific annotation entry.
- `DELETE /annotations/{id}` - Remove an annotation.