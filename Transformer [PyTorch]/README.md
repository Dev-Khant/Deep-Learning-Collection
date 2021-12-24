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
<br>![self attention](https://user-images.githubusercontent.com/57898986/147345666-5a46903a-7795-43d5-b95f-f517ee5fbf40.png)
<br><br>
In self-attention each word embedding is multiplied with all other word embeddings present in a sentence. Self-attention allows word to look at other positions in the input sentence for clues that can help lead to a better encoding for this word.<br>
- First step is three vectors are created **Query**, **Key**, **Value** by multipying the word embedding with three matrics(query, key and value) that are trained during the training process.<br>
- Second step is in self-attention is to calculate a score. Let's say we are calculating for first word in sentence then we need to score each word of the input sentence against this word. The score determines how much focus to place on other parts of the input sentence as we encode a word at a certain position.<br>
- The score is calculated by taking the **dot product** of the query vector with the key vector of the respective word we are scoring. So if we are processing the self-attention for the word in position **#1**, the first score would be the dot product of **q1** and **k1**. The second score would be the dot product of **q1** and **k2**.
- The third and fourth step is to divide the scores by 8. This leads to having more stable gradients. Then softmax is applied so that the scores are normalized and all add up to 1.<br>
- The fifth step is to multiply each value vector by the softmax score. Because we want to focus on words with higher score and drown-down irrelevant words(whose softmax score is less).<br>
- Sixth step is to sum the weighted value vectors. This produces the output of self-attention layer at this position(first word).<br>
- In actual implementation, this calculation is done in matrix form for faster processing.<br><br>

In Transformer there are multiple **self-attention heads** each with their own **Query, Key and Value weights matrix**. In original paper, they have used 8 heads means there are 8 query, key and value matrices(Q1 K1 V1, Q2 K2 V2 etc).<br>
Now the same process mentioned above happens with all heads and the final outputs from all heads concatenated and is multiplied with a **weight matrix** which is jointly trained with model.<br>
### Feed Forward Network and Normalization Layer

For **first norm layer** there are two inputs - output of self-attention and original embeddings(because of skip connections).<br>
Then the **output** of norm layer is passed through a FFN and again with another norm layer with inputs consisting of output of FFN and output of 1st norm layer.<br>
The final output is of second norm layer.<br>

The original paper uses **8 encoder blocks**.

## Decoder Block
<br>![Decoder](https://user-images.githubusercontent.com/57898986/147348752-48b6a166-c47e-481e-bfcf-610f250ed9ad.png)
<br>









<!-- - While in output sentence **[start]** is prepended and **[end]** is appended and then converted to Tensor with a specific length, if sentence is shorter **[pad]** values are appended in Tensor.<br>   -->





