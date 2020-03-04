# Smartphone Recommender
The project developed to hit a partial note on the discipline of Artificial Intelligence.

### Project structure
The project is organized of the following form:

### API
An API responsible by returning a list of recommendations and a list of filters to be used on 
the client application.

The API contains the following routes:

##### /recommendations
This route returns a list of recommendations based on a list of informed filters on query string
params. Below, an example of a query string is informed.

Method: GET
Params:

* cpu=Snapdragon 855
* storage-capacity=128 GB
* removable-storage=No
* os=Android 8.1 "Oreo"
* display=6.41" 2340x1080 AMOLED
* camera=Dual 12 MP + 13 MP (rear camera) 24.8 MP (front camera)

##### /filters
This route returns the filters that the client application go show to allow that the user can select
yours preferences.

Method: GET
Params: No params is needed

### Recommender
The recommender was built based on the [KNN](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm) algorithm, and a dataset of smartphones characteristics downloaded from [Kaggle](https://www.kaggle.com/shivamsinghal1012/smart-phones-details). To build the project, the implementation of KNN existent on the [scikit-learn](https://scikit-learn.org/stable/modules/neighbors.html) library was used.

### Client Application
To represent the recommendations to a user, one web application was developed. Where, the user can select a lot of filters (based on the content of the dataset), and after a click on "Filter", the API returns a list of recommendations based on preferences of the user, or null (when nothing hit the user preferences). 

### The deploy
To deploy, the [Heroku](https://www.heroku.com/) platform was used. Bellow the urls of API and Client application are informed.

API:
* [https://radiant-bastion-89139.herokuapp.com/filters](https://radiant-bastion-89139.herokuapp.com/filters)
* [https://radiant-bastion-89139.herokuapp.com/recommendations](https://radiant-bastion-89139.herokuapp.com/recommendations)

CLIENT:
* https://protected-plains-78201.herokuapp.com/

### Credits
The article [https://medium.com/@sumanadhikari/building-a-movie-recommendation-engine-using-scikit-learn-8dbb11c5aa4b](https://medium.com/@sumanadhikari/building-a-movie-recommendation-engine-using-scikit-learn-8dbb11c5aa4b) was used like reference.
