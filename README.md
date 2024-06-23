# 23M0323_LLM
Season of Code 2024

*Large Language Models*

LLM stands for Large Language Model, a type of artificial intelligence model designed to understand and generate human language. These models are characterized by their vast number of parameters, typically ranging from 10 to 100 billion. Beyond their sheer size, LLMs exhibit remarkable qualitative properties, such as emergent behaviors. One notable example is zero-shot learning, where the model can perform tasks it wasn't explicitly trained to do, demonstrating a sophisticated level of language understanding and generation

In the old way of supervised learning, models were trained on large labeled datasets; for instance, to translate "Hello" to "Hola," the model needed numerous labeled examples in different languages. In contrast, zero-shot learning leverages the new way of self-supervised learning, where models are trained on large corpora of text without explicit labels. These models learn to perform tasks such as translation by predicting the next word in a sequence, utilizing vast amounts of text data. This allows them to handle tasks they haven't been explicitly trained on, demonstrating a more advanced and flexible understanding.
LLMs operate on the next-word prediction paradigm, where they predict the next word in a sequence based on the previous words, a method known as autoregression. During the training process, they are exposed to diverse and extensive text datasets, which enhances their language understanding and generation capabilities. This extensive training allows them to perform a wide range of language tasks with high accuracy and flexibility.
There are 3 levels of using LLMs:
Level 1: Prompt Engineering
Level 2: Model Fine-tuning
Level 3: Build Your Own LLM

Level 1: Prompt Engineering
Prompt engineering involves using an LLM out-of-the-box without altering any model parameters. For straightforward applications, this can be easily achieved by utilizing tools like ChatGPT. For more customized use cases, it may involve using APIs from providers such as OpenAI or Hugging Face, which offer greater flexibility and control over the model's behavior and outputs.

Level 2: Model Fine-tuning
Model fine-tuning involves adjusting at least one internal parameter of a pre-trained LLM to tailor it for specific tasks. The process includes three main steps: First, obtain a pre-trained LLM. Second, update the model's parameters using task-specific examples. Finally, utilize the fine-tuned LLM to achieve improved performance on specific tasks. This customization enhances the model's accuracy and effectiveness for the intended applications.

Level 3: Build Your Own LLM
Building your own LLM involves creating an LLM from scratch by defining all model parameters. The process includes three main steps: First, collect extensive datasets, such as Python code, Wikipedia articles, and books. Second, train the model on these datasets to develop a pre-trained LLM. Finally, the outcome is a custom LLM tailored to specific requirements or applications, offering precise control over its capabilities and performance.

*Prompt Engineering*

Prompt engineering refers to any use of an LLM out-of-the-box, involving the art of programming LLMs with prompts to achieve desired tasks. It is described as "the means by which LLMs are programmed with prompts" , and "an empirical art of composing and formatting the prompt to maximize a model’s performance on a desired task" . Essentially, prompt engineering leverages the nature of language models to complete documents, enabling the performance of various tasks by creatively arranging prompts as if they were parts of a document . This technique can be easily applied through tools like ChatGPT or more complex APIs from providers such as OpenAI or Hugging Face.

Six Strategies for Getting Better Results with Prompt Engineering:

1. Refining Prompts:
   - Crafting clear and specific prompts to guide the language model effectively.
   - Ensuring that prompts are well-defined to minimize ambiguity and enhance the quality of responses.
2. Using Context Effectively:
   - Providing relevant context within the prompts to help the model understand the background and deliver more accurate responses.
   - Including necessary details that can influence the model’s understanding and output.
3. Leveraging Examples:
   - Using examples within the prompts to illustrate the desired format or content of the responses.
   - Examples help the model grasp the expected outcome more clearly.
4. Experimenting with Different Approaches:
   - Trying various prompt formulations and approaches to find the most effective ones.
   - Being open to adjusting and experimenting to identify the best strategies for different scenarios.
5. Validating Model Outputs:
   - Regularly checking and validating the responses generated by the model to ensure they meet the required standards.
   - Implementing feedback loops to correct and improve the model’s performance over time.
6. Iterating Based on Feedback:
   - Continuously iterating on the prompts and strategies based on feedback and performance metrics.
   - Making incremental improvements to refine the model’s capabilities and outputs.

By following these strategies, developers can significantly enhance the performance and reliability of their language models, ensuring they deliver more accurate, relevant, and high-quality responses.



*Fine-Tuning*
 
Fine-tuning refers to the process of taking a pre-trained machine learning model and further training it on a new task or dataset. This typically involves adjusting the model's parameters so that it can better perform the specific task it's being fine-tuned for. Fine-tuning leverages the knowledge and representations learned by the model during its initial training (often on a large general dataset) and adapts these to a more specialized task or domain. The goal is to improve the model's performance on the new task without requiring extensive training from scratch.

There are 3 ways to Fine-tune a LLM:
Supervised Fine-tuning
Self Supervised Fine Tuning
Reinforcement Learning

 Supervised Fine-tuning :

1. Choose fine-tuning task: Define the specific task or problem you want the pre-trained model to solve. This could be text classification, image recognition, language translation, etc.
   
2. Prepare training dataset: Gather and preprocess a dataset that is annotated or labeled for the fine-tuning task. The quality and size of this dataset significantly impact the fine-tuning process.

3. Choose a base model: Select a pre-trained model that best fits your task requirements and matches the domain of your fine-tuning dataset. Common choices include BERT, ResNet, GPT, etc., depending on whether your task involves natural language processing (NLP), computer vision, or other domains.

4. Fine-tune model via supervised learning: Adjust the parameters of the pre-trained model using the labeled dataset. This involves feeding the dataset into the model and updating its weights through backpropagation to minimize the prediction error on the task-specific labels.

5. Evaluate model performance: Assess how well the fine-tuned model performs on a separate validation or test set. Metrics like accuracy, precision, recall, or F1-score are commonly used depending on the nature of the task. This step helps determine if further adjustments or iterations are needed.

Followings are the options for Parameter Training while finetuning :

1. Retrain all parameters: Fine-tune the entire model from scratch on the new task, updating all parameters of the pre-trained model. This approach can be computationally intensive but allows the model to adapt fully to the new data and task requirements.

2. Transfer Learning: Freeze some or most of the pre-trained model's parameters and only update the final layers (often called the classifier or head) that are specific to the new task. This method leverages the general knowledge encoded in the pre-trained model while adapting it to the specifics of the new task.

3. Parameter Efficient Fine-tuning (PEFT): Fine-tune a smaller set of parameters than retraining all parameters but more than just updating the final layers. This approach seeks a balance between computational efficiency and adaptation to the new task, focusing updates on layers most relevant to the fine-tuning task.

Each of these approaches to parameter training offers different trade-offs in terms of computational resources, speed of adaptation, and the extent to which the model can leverage prior knowledge from the pre-training phase. The choice of method depends on factors such as the size of the fine-tuning dataset, computational constraints, and the desired level of adaptation to the new task.

QLoRA (Quantized Low-Rank Adapter) optimizes memory usage by representing parameters in a lower precision format (e.g., 16-bit floating-point, "16biff"). This allows for more efficient storage and computation, particularly beneficial when working with large models. Quantization is the process of splitting a range into buckets. In the context of machine learning, it involves reducing the precision of the model's parameters, allowing for more efficient computation and reduced memory usage. Followings are the 4 steps of implementing QLoRA to fine tune a LLM:

  Step 1: 4-bit NormalFloat

In the initial step of QLoRA, the model weights are quantized to a 4-bit floating-point representation using the NormalFloat technique. This method compresses the model's weights into a significantly smaller format, reducing both memory usage and computational requirements. The 4-bit representation is carefully designed to maintain precision for smaller numbers, which are more common in neural network weights, while still accommodating a range of values. This allows for a substantial decrease in the memory footprint of the model, enabling faster processing and less resource-intensive training.

 Step 2: Double Quantization

The second step in QLoRA involves a process known as double quantization. This technique further compresses the model weights in two stages. First, the weights are quantized to an intermediate bit-width, often 8-bit, which strikes a balance between size and precision. Then, these 8-bit weights undergo a second round of quantization to reach the final 4-bit representation. This two-step process helps manage the trade-off between maintaining the model's accuracy and achieving high levels of compression, ensuring that the model remains both efficient and effective.

 Step 3: Paged Optimizer

In the third step, QLoRA employs a paged optimizer to handle memory more efficiently during training. This optimizer functions similarly to virtual memory systems in operating systems, where only the necessary data is kept in active memory while the rest is stored on disk. During training, only the parts of the model currently being updated are loaded into memory, while the inactive parts are paged out. This approach allows for the training of large models on hardware with limited memory, as it optimizes the use of available resources and prevents memory overload.

 Step 4: LoRA (Low-Rank Adaptation)

The final step in QLoRA is Low-Rank Adaptation (LoRA), which focuses on fine-tuning the model with efficient low-rank updates. Instead of updating the entire weight matrix during fine-tuning, LoRA approximates these updates using two smaller matrices that represent low-rank components. This decomposition significantly reduces the number of parameters that need to be adjusted and stored, making the fine-tuning process less memory-intensive and faster. By targeting low-dimensional subspaces for updates, LoRA enables the model to adapt to new tasks effectively while maintaining a low computational cost.




*RAG (Retrieval-Augmented Generation)*

RAG (Retrieval-Augmented Generation) is a method that combines the strengths of large language models (LLMs) with the precision and relevance of a specialized and mutable knowledge base. The primary aim of RAG is to enhance the capabilities of LLMs by providing them with access to a dynamic repository of information that can be updated and customized as needed. This integration allows the model to generate more accurate and contextually appropriate responses by drawing on up-to-date and specialized knowledge that might not be present in the static pre-trained model.

RAG operates using two key elements: the retriever and the knowledge base.:

1. Retriever
The retriever is responsible for fetching relevant information from the knowledge base based on the input query. When a user inputs a query, the retriever searches through the knowledge base to identify and retrieve the most pertinent pieces of information. This step is crucial because it ensures that the generation process is informed by the latest and most relevant data available. The retriever can use various methods for information retrieval, including traditional search algorithms, semantic search, or more advanced techniques like dense vector representations and similarity search.
2. Knowledge Base
The knowledge base in RAG is a specialized and mutable repository of information. Unlike the static data encoded in the weights of a pre-trained language model, the knowledge base is designed to be easily updated and expanded. It can include a wide range of data types, such as documents, articles, databases, and other structured or unstructured information. The mutability of the knowledge base means that it can be continually refined and augmented to keep up with new developments, domain-specific knowledge, or any other evolving informational needs.

In practice, RAG works by first using the retriever to identify relevant documents or pieces of information from the knowledge base in response to a query. These retrieved pieces of information are then fed into the language model, which uses them to generate a response. This combined approach allows the language model to produce answers that are both coherent and highly relevant, leveraging the latest information available in the knowledge base. By augmenting LLMs with this dynamic retrieval mechanism, RAG enhances the model's ability to provide accurate and context-aware responses, making it especially valuable in applications where up-to-date and specialized information is crucial.



*Building a large language model (LLM)  from scratch*

Building a large language model (LLM) from scratch involves several key steps, from data curation to model architecture, training at scale, and evaluation. Here's a detailed explanation of each step:

 Step 1: Data Curation

The quality of an LLM heavily depends on the quality and diversity of the data it's trained on. Followings are the steps involved in data curation:

- Data Sources: Gather data from various public and private sources:
  - Public Datasets: Sources like Common Crawl (e.g., C4, Falcon RefinedWeb), The Pile, and datasets provided by Hugging Face. These datasets are often vast and cover a wide range of text sources from the internet.
  - The Internet: Web pages, Wikipedia, forums, books, scientific articles, code bases, etc., provide diverse textual data.
  - Private Data Sources: For instance, BloombergGPT's FinPile sourced from Bloomberg archives, which provides specialized financial data.

- Utilizing Pre-trained Models: Use existing large language models like Alpaca, which are trained on structured text generated by models like GPT-3. These pre-trained models provide a strong starting point for further customization or fine-tuning.

 Step 2: Model Architecture

Selecting the right model architecture is crucial for designing an effective LLM. Key considerations include:

- Transformers: Neural network architectures that use attention mechanisms for handling sequential data efficiently.
there are 3 types of Transformer architecture used as follows:
  - Encoder: Translates tokens into semantically meaningful representations, used in tasks like text classification.
  - Decoder: Similar to encoder but without allowing self-attention with future elements, suitable for text generation tasks.
  - Encoder-Decoder: Combines both encoder and decoder, enabling cross-attention, essential for tasks like translation.

 Step 3: Training at Scale

Training an LLM at scale involves using advanced techniques to handle large amounts of data and computational resources effectively:
- Training Techniques includes the following:
  - Pipeline Parallelism: Distributes transformer layers across multiple GPUs to speed up computation.
  - Model Parallelism: Decomposes parameter matrix operations into multiple matrix multiplies across GPUs.
  - Data Parallelism: Distributes training data across multiple GPUs to accelerate training.
- Zero Redundancy Optimizer (ZeRO): Optimizes training efficiency by reducing redundancy in the optimizer state, gradient, or parameter partitioning, which is crucial for managing large-scale models.

 Step 4: Evaluation

To ensure the model meets performance expectations and benchmarks, evaluation involves:

- Benchmark Dataset: Use standardized datasets to measure model performance consistently.
- Multiple-choice Tasks: Evaluate the model's ability to choose the correct answer among multiple options.
- Open-ended Tasks: Assess the model's performance in generating coherent and contextually appropriate responses.

By following these steps—from curating high-quality data to selecting an appropriate architecture, training efficiently at scale, and rigorously evaluating performance—an effective large language model can be developed from scratch, tailored to specific tasks and domains. These steps ensure that the model not only performs well but also adapts to diverse linguistic challenges and requirements.
