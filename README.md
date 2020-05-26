
# Generating News Headlines Using Natural Language Processing
This project focuses on the application of deep learning to natural language processing. I worked with a subset of Reuters news headlines that are collected over 15 months, covering all of 2019, plus a few months in 2018 and in a few months of this year.

In particular, I built an autoencoder of news headlines. I have an encoder that maps a news headline to a vector embedding, and then a decoder that reconstructs the news headline. Both my encoder and decoder networks are Recurrent Neural Networks. I built:

- a neural network that takes a sequence as an input
- a neural network that generates a sequence as an output

This project is organized as follows:
- Exploring the data
- Building the autoencoder
- Training the autoencoder using data augmentation
- Analyzing the embeddings (interpolating between headlines)

Furthermore, I use data augmentation for improving of the robustness of the autoencoder, as proposed by Shen et al [1].

[1] Shen et al (2019) "Educating Text Autoencoders: Latent Representation Guidance via Denoising" https://arxiv.org/pdf/1905.12777.pdf


## Motivation and Comments
I always found news headlines to be particularly interesting because of the way they grab the readers attention in just a single sentence. This inspired me to try and create a neural network that is able to do the same. Thus, by training the network using these gripping headlines, I created a model that generates its own news headlines drawing from the themes of the original inputted headline. A few examples of the models success is shown below.
Additionally, this project contains detailed reasonings and justifications of why I am doing what I am doing at each step to make it easy for the reader to follow along with the notebook. This also helped me map out my thoughts and have a clear direction while working through the project.

## Visualization of Data Distribution
![](https://github.com/saihiel/news_headlines/blob/master/images/distribution_of_headline_lengths.png)

I found this histogram useful to see the distribution of headline lengths. This allowed me to make decisions about the kind of model I should use. For instance, the size of the hidden layer or the embedding size depends on the length of the sequences. Since, if a single headline can be 200 words long, then the size of the embedding needs to be large enough to be able to represent this headline.

## Results
Since the project contains various components, I have provided the results for the significant ones. Further details can be found in the notebook.  
**1. Generating a new headline using an original headline.**  
  &nbsp;&nbsp;&nbsp;*Original Headline:* Wall street rises, limps across the finish line of a turbulent year.  
  &nbsp;&nbsp;&nbsp;*Generated Headline:* Wall street rises after the losses from the markets poor performing year.

**2. Demonstrating the correctness of the embedding space created for each of the headlines by finding the closest 5 headlines  to a given headline that are contained in the dataset.**  
  &nbsp;&nbsp;&nbsp;*Original Headline:* Asia takes heart from new year gains in u.s. stock futures  
  &nbsp;&nbsp;&nbsp;*5 Closest Headlines:*  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-- italy 's salvini loses aura of invincibility in emilia setback  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-- saudi , russia look to seal deeper output cuts with oil producers  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-- eu orders quarantine for staff who traveled to northern italy  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-- update _num_-italy 's prime minister says new government will bicker less  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-- portugal 's moura pays tribute to cod fishermen at milan fashion close  

**3. Interpolating between two given headlines. The percentage is used to simplify the representation of the distance within the embedding space from the first headline to the second headline.**  
   &nbsp;&nbsp;&nbsp;*First Original Headline:* n.korea's kim says new path inevitable if u.s. demands unilateral action  
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Generated Headline:* (25% from 1 to 2) n.korea situation says states new soft leave will force the warned dollars  
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Generated Headline:* (50% from 1 to 2) experts pressing bolsonaro to defend compensation not tensions  
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Generated Headline:* (75% from 1 to 2) kurdish syrian seal to rocky development of the airliner: korean extremism  
   &nbsp;&nbsp;&nbsp;*Second Original Headline:* kurdish fighters pull out of flashpoint town: syria's defense ministry  
