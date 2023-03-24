# Pattern-Recognition-with-Adaptive-Resonance-Theory
This project presents a pattern recognition task, based on multiple patterns i.e., alphabets A-T. The proposed solution employs an Adaptive Resonance Theory (ART) network to recognize patterns, given certain initial conditions and is then evaluated for a number of vigilance levels.

## Adaptive Resonance Theory
Adaptive resonance theory (ART) is a type of neural network that employs unsupervised learning. They are open to new learning i.e., adaptive without discarding previous information i.e., resonance. This is phenomena is also referred to as stability-plasticity dilemma. In other words, they can learn new patterns without forgetting old ones. It is generally employed for pattern recognition and clustering applications. For this project, I have used ART 1, which is designed for sequences of binary input patterns.

## Data Generation

There are 20 clean patterns as represented in the problem statement, with each having dimensions of 8x8. The patterns are of grey-scale representation, and have been populated using binary values i.e., 1 & 0.

![clean patterns](https://user-images.githubusercontent.com/97694796/227644564-763c204a-7d2b-4f4a-9733-a8d18fe23184.png)

In addition, I have generated two sets of noisy patterns associated with each clean pattern by introducing random noise. This is achieved by reversing values of 12.5% & 25% of pixels per pattern. The obtained patterns for each scenario are as follows:

![12.5% noise](https://user-images.githubusercontent.com/97694796/227645105-593b3753-dae4-4827-9c15-9b23a67eb795.png)
                                     
![25% noise](https://user-images.githubusercontent.com/97694796/227645287-f9d1c551-82de-4363-b059-6db4f752c843.png)

## Model Buiilding 

Under this section, the network is built and evaluated for several scenarios. The learning process is unsupervised and based on the principles of clustering algorithm. In summary, input is presented to the network and the algorithm checks whether it fits into one of the already stored clusters. If it fits, then the input is added to the cluster that matches the most else a new cluster is formed.

We evaluate the performance based on correct recognition/association of the input pattern with the stored patterns, otherwise, the creation of new category/cluster. An important parameter is the ‘Vigilance’ parameter, defined as the similarity between the top-down template and the input vector.

There are two scenarios for the vigilance test:

a. Vigilance test is passed. Update T-D and B-U weights for both layers, for the associated cluster.
b. Vigilance test is failed. Repeat the earlier steps and compare the input with remaining clusters to choose one. If none passes the test, create a new category, and do not disrupt weights for the other stored clusters.

## Model Evaluation

For higher values of vigilance, the network can distinctly categorize input patterns into new categories. This is a desired attribute but leads to overfitting. On the other hand, a smaller value means patterns can be incorrectly associated with similar but different patterns. Thus, it is imperative to choose the value of the vigilance parameter according to the problem specifications. Fuethermore, the network was able to successfully learn all patterns for high vigilance values whilst ensuring previous clusters were not impacted. This reaffirms our initial hypothesis about the ability of ART network in resolving the stability-plasticity dilemma.

