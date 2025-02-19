https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/document_search.ipynb
https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/clustering_with_embeddings.ipynb
https://cloud.google.com/alloydb/docs/ai/work-with-embeddings
https://github.com/google/generative-ai-docs/blob/main/site/en/gemini-api/tutorials/text_classifier_embeddings.ipynb

https://cloud.google.com/vertex-ai/generative-ai/docs/embeddings/get-multimodal-embeddings#aiplatform_sdk_text_image_embedding-python_vertex_ai_sdk
https://github.com/facebookresearch/ImageBind
https://blog.voyageai.com/2024/11/12/voyage-multimodal-3/

user can set the embeding size of a chapter, 128 tokens or 512 mapped to - X embeding size, we can also give them the option to change this embeding dim if they want 
(this would require us to rebuild the dataset, but users could find that there are not happy with X size embeding and want to chage to accomadate X style doc better.)

Titan Text Embeddings V1 takes as input a non-empty string with up to 8,192 tokens and returns a 1,024 dimensional embedding. The characters to token ratio in English is 4.7 char/token, on average. Note on RAG uses cases: While Titan Text Embeddings V2 is able to accommodate up to 8,192 tokens, we recommend to segment documents into logical segments (such as paragraphs or sections).

https://www.youtube.com/watch?v=qCAvqsBbN2Y&t=1100s
we could use many collections, but i dont like this, i think using a unified vectorspace will be much bettre for us



https://blog.voyageai.com/2024/11/12/voyage-multimodal-3/


text, slides, photos, pdf --> embeding 
video, audio gemini 1.5 flash --> text --> embeding 


https://github.com/minio/minio/tree/master/docs/orchestration/docker-compose
https://min.io/docs/minio/linux/operations/monitoring/collect-minio-metrics-using-prometheus.html