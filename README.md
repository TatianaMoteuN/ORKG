# ncg_challenge : Build a research problem extraction system
The NLPContributionGraph (NCG) challenge was organized in SemEval 2021 . The general task information is available here https://ncg-task.github.io/


<<<<<<< HEAD

### Appraoch : the task is organized into two parts:

    • Build a based graph model that will help model relationships between entities in order to visualize research problems solved by researchers in a kind of space
    • build a topic modeling (LDA) that will helps us extract abstract "topics" that appear in a collection of documents.



    1) Based graph model

In this part, we build a knowledge graph embeddings using AmpliGraph library. We trained the the datasets on four different models and the scoring results will be reported below.

Prerequisites:
    • Python ≥ 3.6
    • Linux Box
    • Install Tensorflow 1.x version
    • Install AmpliGraph using: pip install ampligraph
      

    • Knowledge graph creation: the knowledge graph creation required a dataset into the form a a triple of < source, target, edge>. Using our dataset, we obtained a graph as showed in the image below
      
    • Models: models used in our experiments are: 
        ◦ ComplEx
        ◦ TransE
        ◦ DistMult
        ◦ HolE
	The hyper-parameters are the same for each model and the average Loss is reported in the following table
    
        | Model   |Avg Loss|
| :----------:|:----:| 
| ComplEx     | 0.006 | 
| TransE      | 0.029 | 
| DistMult    | 0.010 |
| HolE        | 0.923 |



    • Performance evaluation: The evaluation for neural embeddings models involved model selection routine, negatives generation and learning-to-rank-based implementation. The negatives generation is done simply by concatenating the train and test sets. We report the filtered MR(Mean Rank), MRR(Mean Reciprocal Rank), Hits@ for each model
    
    | Model   | MR   |MRR   |Hits@10|Hits@3| Hits@1|
| :----------:|:----:| :---:| :---: | :---:| :----:|
| ComplEx     | 3.00 | 0.33 |  1.00 | 1.00 | 0.00  |
| TransE      | 1.00 | 1.00 |  1.00 | 1.00 | 1.00  | 
| DistMult    | 1.00 | 1.00 | 1.00  | 1.00 | 1.00  |
| HolE        | 1.00 | 1.00 | 1.00  | 1.00 | 1.00  |


      
    • Prediction: the code provides a possible method to restore the model for making prediction on test set. We can then see the scored values and transform them into probabilities (bound between 0 and 1).



    2) Topic modeling

Topic modeling is an unsupervised technique to identify natural topics in the text and, is used there o extract research in text document. It does not required model training and a labeled training dataset. There a few algorithms for topic modeling but here we only experiment LDA (Latent Dirichlet Allocation). In this tutoriel, we will perform the following tasks:
    • Loading data
    • Data preprocessing
    • Data exploration
    • Data preparation
    • LDA model training
    • Analyzing the LDA model
      

       LDA model training
       Here we import our model from gensim library and we keep parameters as default except the number of topics set as 10

	Analyzing the LDA modeling
	Here we visualize the topics from the trained model. To do so, we used pyLDAvis, a python library for interactive topic model visualization that will help us understand and interprete individual topics and relationships between them. The output is showed in the image below

https://github.com/TatianaMoteuN/ncg_challenge/blob/main/image.png
       
=======
The NLPContributionGraph (NCG) challenge was organized in SemEval 2021 . The general task information is available here https://ncg-task.github.io/


>>>>>>> 136ecb4078fcb7c7168911d621e38da38a3f52ce
