# MLP for bio sequence allignment
In bioinformatics, a sequence alignment is a way of arranging the sequences of DNA, RNA, or protein to identify regions of similarity that may be a consequence of functional, structural, or evolutionary relationships between the sequences. The objective of this project was to perform local sequence allignment on 40 mers of MERS and SARS. The approach is explained in the following steps:

1. Reading the data
2. Creating 40-mers of the data for both MERS and SARS
3. Retrieving the top 100 40-mers for both the sequences
4. Using FastText for embedding
5. t-sne for dimensionality reduction of the embedded 40-mers
6. Training the MLP model with various metrics as labels:
   
   1. Hamming distance of both the sequences
   2. Cosine similarity of the embedded 40-mers
   3. Euclidean distance of the embedded 40-mers
   4. Embedded longest common substring 
 
Cosine similary of the embedded 40-mers turns out to be the best metric for class label with the least loss. However the disadvantage being, no string reconstruction is possible with a scalar as output. This is the disadvantage of using FastText as an embedding technique. A better approach is to encode the words to their corresponding numbers. 
For e.g.: 
#### "A" -> 1
#### "C" -> 2
#### "G" -> 3
#### "T" -> 4

The input for the model will be sequence of two strings made up of "1" ,"2", "3", "4" . The class label is the encoded logest common substring. An approximate reconstuction has been done using the above mentioned encoding.
