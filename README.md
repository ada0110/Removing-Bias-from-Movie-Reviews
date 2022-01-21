# Removing Bias from Movie Review Rating Prediction
I used [domain adaptation](https://arxiv.org/pdf/1409.7495.pdf) method to train LSTM model for predicting movie review rating without being biased towards the genre of the movie using. This method seemed to have worked well on removing gender/racial biases in various NLP tasks discussed above. So, the idea is to train a model in such a manner that it is able to learn the overall category/rating of review while not focusing on the protected information (genre, celebrity etc.). 

Also, since there was no dataset having `(movie, genre, review, rating)` tuple, I build the dataset from IMDB by scraping (using requests, BeautifulSoup) and IMDbPY library.

Model was trained on two objectives but we only want to it to learn one of them (review class) and not learn the other (genre). Both `L1` and `L2` are cross-entropy losses (sparse). 
> L1 = review rating loss  
> L2 = genre loss  
> alpha = hyperaparmeter to control trade-off between L1 and L2  

I implemented the following architecture to train the bias free model:

![image](https://user-images.githubusercontent.com/64487038/150490057-19ad894d-06a5-4dfc-b0c3-79fd5934bc52.png)

Please check the attached report for more details.
