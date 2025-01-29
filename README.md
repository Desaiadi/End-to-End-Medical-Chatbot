## **End-to-End Medical Chatbot**

**Overview**

The End-to-End Medical Chatbot is a conversational AI application designed to provide information and answer questions related to medical topics. It leverages a large language model (LLM) and a vector database to process and respond to user queries.

**Key Features**

- **Natural Language Understanding:** The chatbot can understand and respond to user queries in a natural language format.
- **Custom Medical Knowledge Base:** It is equipped with a comprehensive knowledge base of medical information derived from a The Gale Encyclopedia of Medicine book.
- **Contextual Understanding:** The chatbot can maintain context during conversations, allowing for more relevant and informative responses.
- **User-Friendly Interface:** The chatbot provides a user-friendly interface for easy interaction.

**Technologies Used**


 - It uses the _Llama-2-7B-Chat-GGML_ model, which is a **large language model (LLM)** that has been fine-tuned.
   * Name - **llama-2-7b-chat.ggmlv3.q2_K.bin**
   * Quant method - q2_K
   * Bits - 2
   * Size - **2.87 GB**
   * Max RAM required - 5.37 GB
   * Use case - New k-quant method. Uses GGML_TYPE_Q4_K for the attention.vw and feed_forward.w2 tensors, GGML_TYPE_Q2_K for the other tensors.
   * **Model:** Know more about model **[Llama-2-7B-Chat-GGML](https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML)**
 - It is trained on the pdf **[The Gale Encyclopedia of Medicine, Volume 1, 2nd Edition, 637-page PDF]

## Understanding the Chatbot's Workflow

![Architecture_Medical_Chatbot](https://github.com/user-attachments/assets/ed79ddc4-009e-49ad-aa71-234d8bc23a9a)

### Data Integration and Extraction
1. **Data Source:** The chatbot utilizes a The "Gale Enclopedia of Medicine book" as its primary source of medical information. This book contains details about various diseases, their symptoms, treatments, and other relevant medical data.
2. **Extraction:** The content from the PDF book is extracted and converted into a textual format that the chatbot can process. This involves extracting text from the PDF, handling formatting, and ensuring the extracted data is in a suitable format for subsequent steps.

### Text Chunking
- **Reasoning:** The language model used in the chatbot has limitations on the input size it can process at once. To address this, the extracted text is divided into smaller, manageable chunks.
- **Process:** The text is broken down into segments of a predetermined size. This ensures that the model can process each chunk efficiently and avoid overwhelming it with excessive information.

### Embedding Generation
- **Purpose:** Embeddings are numerical representations of text that capture the semantic meaning of the words and phrases. They are essential for the chatbot to understand and process the information effectively.
- **Process:** Each chunk of text is converted into an embedding using a suitable embedding technique. This involves transforming the text into a numerical vector that represents its semantic meaning.

### Semantic Index Creation
- **Purpose:** The semantic index is a database that organizes the embeddings in a structured manner. It helps the chatbot quickly find relevant information based on user queries.
- **Process:** The embeddings generated from the text chunks are stored in the semantic index. The index uses algorithms to calculate the similarity between different embeddings, allowing the chatbot to efficiently retrieve related information.

### Knowledge Base
- **Purpose:** The knowledge base is essentially the repository of medical knowledge that the chatbot can access. It is built using the semantic index.
- **Structure:** The semantic index organizes the embeddings in a way that allows the chatbot to easily search for and retrieve information based on specific queries.

### User Interaction and Response Generation
1. **User Query:** A user asks a question related to medical topics.
2. **Query Processing:** The chatbot processes the user's query and converts it into an embedding. This embedding represents the semantic meaning of the query.
3. **Information Retrieval:** The chatbot searches the semantic index for embeddings that are similar to the query embedding. This helps identify the most relevant information from the knowledge base.
4. **Response Generation:** Based on the retrieved information, the chatbot generates a response using the language model. The model processes the information and formulates a coherent and informative answer to the user's query.

### Technologies
- **Python:** A popular programming language used for building the chatbot's logic and functionality.
- **Langchain:** A framework that simplifies the process of building and deploying language models.
- **Flask:** A web framework used to create the chatbot's user interface.
- **Meta Llama 2:** A powerful language model capable of understanding and generating human-like text.
- **PineCone:** A vector database that efficiently stores and retrieves embeddings.


**Installation Quickstart** 
1. Open Git Bash.
2. Change the current working directory to the location where you want the cloned directory.
3. Type `git clone`, and then paste the URL you copied earlier.
```bash
   git clone https://github.com/Desaiadi/End-to-End-Medical-Chatbot.git
```
Press Enter to create your local clone.
4. Create a conda environment after opening the repository
```
  conda create -n mchatbot python=3.8 -y
```
```
  conda activate mchatbot
```

5. Install the pip packages in requirements.txt
 ```bash
   pip install -r requirements.txt
 ```
5. Create a .env file in the root directory and add your Pinecone credentials as follows:

```
  PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
  PINECONE_API_ENV = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```
Download the quantize model from the link provided in model folder & keep the model in the model directory:
```
## Download the Llama 2 Model:

llama-2-7b-chat.ggmlv3.q4_0.bin


## From the following link:
https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML/tree/main

# run the following command
python store_index.py

# Finally run the following command
python app.py

```

Now,
```
open up localhost:
```
**Data Preparation**

- Replace the `data/medical_book.pdf` file with your own medical PDF book.
- Ensure the book contains relevant medical information and is formatted in a way that can be easily extracted.

**Customization**

- You can customize the chatbot's behavior by modifying the LLM model, knowledge base, and other components.
- Consider adding more features or improving the chatbot's responses based on user feedback.

**Contributing**

Contributions to this project are welcome! Please feel free to submit pull requests or issues.

**License**

This project is licensed under the MIT License.

**Additional Notes**

- For more details on the project's architecture and implementation, refer to the video transcript.
- This README file provides a basic overview of the project. You may want to add more specific information or sections as needed.


