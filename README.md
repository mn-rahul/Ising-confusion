# Ising-confusion
## Classifying the phases in an Ising Model using confusion scheme.

Classifying phases in Ising model using ANN and implementing the confusion scheme by deliberately mislabelling the data around the critical temperature. 
The data was sampled using metropolis algorithm. A simple neural network was trained on the sampled to data to identify the phases. 

Confusion can be considered as a combination of supervised and unsupervised learning. It acts an unsupervised learning model when the data is mislabelled.
Confusion can be understood in the following way. <br>
1. Consider the range (a,b) within which the $T_c$ lies. Let  c lie between a and b such that the data can be classified into two classes or phases (c may or may not be the actual critical point).\\ \\
2. Propose  c’ to be the critical point. Everything below c’ will be labelled 0 and the ones above c’ as 1 and the network is trained.\\ \\
3. Data is assumed to have two different structures(features) above and below c.\\\\Now let us consider the following cases:\\1. c' = a, In this case both the features are labelled as 1( higher temperature phase) hence the NN predicts with maximum accuracy. \\2. When c=c’ , data on either sides of c is labelled correctly and hence NN predicts accordingly without any confusion. \\
3. Consider $a<c’<c$., NN sees the same data between (a,c’) and (c’,c) but labels them differently (hence the Confusion).\\
4. Similarly when $c<c'<b$ same data has different label between (c,c') and (c',b). In both 3 and 4 it will choose to learn the majority label. 
the model performance $P(c')$ is
\begin{equation}
    P(c') = 1-\frac{min(c-c',c'-a)}{b-a}
\end{equation}
    
The reason why this scheme was used in the first place was to increase the model performance at the crossover or $T_c$. Classifying phases at either extreme of the temperature scale is an easy task, however at the crossover model performance maybe low beacuse the data on either side of the $t_c$ is similar. 
https://doi.org/10.1038/nphys4037 
