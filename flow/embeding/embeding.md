Proposed Workflow Overview:

File Ingestion:
Accept input in various formats (photo, text, video, audio).
Determine file type and route to the appropriate processing pipeline.
Processing Steps:

For Photos:

Use an image captioning model (BLIP, CLIP) to generate a summary and tags.
Store metadata (generated captions, tags).
Embed the image using an image-text embedding model (CLIP).
For Text:

Directly process text content for summary and tags using NLP models
Generate embeddings for storage.

For Video and Audio:

Step 1: Generate transcript (using models like Whisper or AWS Transcribe).
Step 2: Store the transcript as metadata.
Step 3: Pass the media and transcript to an AI model for: 
A summary of the entire content.
Generating tags based on content.
Step 4: Segment the file based on timestamp or predefined intervals.
Step 5: For each segment:
Use AI to analyze the segment within the context of the entire clip.
Generate embeddings for the segment.
Step 6: Store the processed data (transcript, summary, tags, segment embeddings).

different embedding models operate in different vector spaces, meaning the same concept ("queen") may be positioned differently across models. This happens because each model is trained with unique architectures, objectives, and datasets, leading to variations in embedding space geometry.

To ensure embeddings from different models are "aligned" or comparable across modalities (text, image, video)

- Universal Embedding Models
ALIGN 
FLAVA
BLIP-2

Gemini 1.5 pro (best this would require the least bit of messing around to work well but it will be very expensive unless we can find a 
true multimodal model like this we can host localy)

- Embedding Space Projection
Linear Projections: Training a simple transformation matrix to map embeddings across spaces.
Procrustes Alignment: Rotates one embedding space to match another while preserving distances.
Canonical Correlation Analysis (CCA): Aligns the spaces by maximizing correlation between embeddings of the same content across modalities.