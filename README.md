# Visual Question Answering (VQA)
This repository contains my end of studies' project about Visual Question Answering [(VQA)](https://visualqa.org/) 
as a student in the Information Technology and Cybersecurity Department at [INSA CVL](https://insa-centrevaldeloire.fr/). The project implements 
a novel co-attention model presented in "Hierarchical Question-Image Co-Attention for Visual Question Answering" [paper](https://arxiv.org/abs/1606.00061)
in [Keras/Tensorflow](https://www.tensorflow.org/).

## Overview
To correctly answer visual questions about an image, the machine needs to understand both the image and question. A model that can 
jointly reasons about image and question attention could improve the state-of-the-art on the VQA problem. So I decided to study the paper and experienced
this novel mechanism by myself. In this repository only parallel co-attention mechanism which generates
image and question attention simultaneously is implemented.

## Architecture
* STEP 1: Extract image features from a pre-trained CNN (VGG19 is used here).
![Alt text](/images/VGG.jpg?raw=true "VGG architecture")
* STEP 2: Compute word embedding, phrase embedding and question embedding
* STEP 3: Calculate co-attended image and question features from all three levels (word, phrase, question)
* STEP 4: Use a multi-layer perceptron (MLP) to recursively encode the attention features

## Dataset
I evaluate the proposed model on the [VQA 2 dataset](https://visualqa.org/download.html). 
The dataset contains 443 757 training questions, 214 354 validation questions, 447 793 testing questions, 
and a total of 6 581 110 question-answers pairs. There are three sub-categories according to answer-types including 
yes/no, number, and other. Each question has 10 free-response answers. The paper uses the top 1000 most frequent answers as the possible outputs. 
This set of answers covers 87.36% of the train+val answers. For testing, I train the model on VQA train+val and 
report the test-dev and test-standard results from the VQA evaluation server like in the paper. 

## Results:
<table>
  <tr>
    <th> Y/N </th>
    <th> Num </th>
	<th> Other  </th>
	<th> All </th>
  </tr>
  <tr>
    <td> 66.47 </td>
    <td> 31.8 </td>
	<td> 32.88 </td>
	<td> 46.69 </td>
  </tr>  
</table>

Some prediction answers on the test-standard:
![Alt text](/images/example1.png?raw=true "Example 1")
![Alt text](/images/example2.png?raw=true "Example 2")
![Alt text](/images/example3.png?raw=true "Example 3")

## Repository Files:
* EDA.ipynb : Exploratory data analysis on the data set
* DataProcess.ipynb : Feature engineering
* Model.ipynb : parallel co-attention model
* Evaluation.ipynb : test-standard results

## References
* Lu, J., Yang, J., Batra, D., & Parikh, D. (2016). Hierarchical question-image co-attention for visual question answering. Advances in neural information processing systems, 29, 289-297.
* https://github.com/arya46/ML-DL-Projects
* https://towardsdatascience.com/visual-question-answering-with-deep-learning-2e5e7cbfdcd4
































