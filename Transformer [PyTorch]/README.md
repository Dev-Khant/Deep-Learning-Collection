# Transformer Implementation in PyTorch

In NLP sentences go through pre-processing stage where words are lowered, punctuation marks and digits are removed etc.<br>
Then words are passed through Stemming or Lemmatization process.<br>
The words are converted into tokens by the above processes.<br>
Vocabulary is created using libraries like **NLTK** or **spaCy**.<br>
Then tokens are mapped with the corresponding index in vocabulary.<br>
                                                                      
                                                                      
## Passing Sentence In Transformer Encoder
<br>![Positional Embedding](https://user-images.githubusercontent.com/57898986/147196000-b82e72b6-23c5-4bdb-b77b-303da93410fe.jpg)
<br><br>
- Input sentence is converted to Tensor with a specific length and if sentence is shorter than specified length then the input Tensor is padded with **[pad]** value from vocabulary.<br> 
- Tensor is passed through an Embedding layer where each word gets it embedding of specific dimension.<br>
- For the Positional Embedding I have simply used no. from 0 to sentence length. But in the original paper researchers have used **sin** function is used for Even positions and **cosin** function for Odd positions.<br>

## Encoder Block
<br>![Transformer block](https://user-images.githubusercontent.com/57898986/147198483-db679d55-dfec-417e-b4d3-018dd95f8c72.jpg)
<br><br>
- Encoder consists of **Multi-Head Attention, Feed Forward Network and Normalization Layer**.<br>
- Let's go through each one of them.<br>

### Multi-Head Attention












<!-- - While in output sentence **[start]** is prepended and **[end]** is appended and then converted to Tensor with a specific length, if sentence is shorter **[pad]** values are appended in Tensor.<br>   -->





