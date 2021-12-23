# Transformer Implementation in PyTorch

In NLP sentences go through pre-processing stage where words are lowered, punctuation marks and digits are removed etc.<br>
Then words are passed through Stemming or Lemmatization process.<br>
The words are converted into tokens by the above processes.<br>
Vocabulary is created using libraries like **NLTK** or **spaCy**.<br>
Then tokens are mapped with the corresponding index in vocabulary.<br>
                                                                      
                                                                      
## Passing Sentence In Transformer Encoder
<br>![positional embedding](https://user-images.githubusercontent.com/57898986/147200024-c3d3d7fb-c61f-4207-bcc6-3c303b1dfd86.jpg)
<br>
- Input sentence is converted to Tensor with a specific length and if sentence is shorter than specified length then the input Tensor is padded with **[pad]** value from vocabulary.<br> 
- Tensor is passed through an Embedding layer where each word gets it embedding of specific dimension.<br>
- For the Positional Embedding I have simply used no. from 0 to sentence length. But in the original paper researchers have used **sin** function is used for Even positions and **cosin** function for Odd positions.<br>

## Encoder Block
<br>![Transformer block](https://user-images.githubusercontent.com/57898986/147200206-11bf4cea-a911-4b8e-88b9-bb2ef91b1bad.jpg)
<br>
- Encoder consists of **Multi-Head Attention, Feed Forward Network and Normalization Layer**.<br>
- Let's go through each one of them.<br>

### Multi-Head Attention












<!-- - While in output sentence **[start]** is prepended and **[end]** is appended and then converted to Tensor with a specific length, if sentence is shorter **[pad]** values are appended in Tensor.<br>   -->





