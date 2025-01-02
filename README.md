This repository contains code for a content-based song recommendation system that suggests new songs to add to a playlist based on its existing content. 

 #Data Collection
A “song database” was created by querying the top 10 songs of the top 2500 most-listened-to artists on Spotify using the Spotify Web API. The API extracted general information about each track including track name, artist name(s), release date etc. as well as audial metrics such as danceability, valence, acoustic-ness etc. Additionally, playlists were also queried, extracting general information and audial metrics for each song. 


The song recommendation system consists of a two-part machine learning model. 
The first part involved training a denoising autoencoder to generate song embeddings of each track in the song database. 
Then, the ‘target’ playlist (which we want to create recommendations for) was aggregated into one “mean” song, and encoded to generate a playlist embedding.  
Finally, using cosine similarity, the top 20 songs most similar to the playlist embedding were identified as song recommendations.
The second part of the team's model assessed the quality of the top 20 songs recommended by the first part of the model. 
For this part, a dataset was created with every song from the ‘target’ playlist and an equal number of random songs not in it. 
An XGBoost classifier was trained on this dataset to predict if a song should be in the ‘target’ playlist. 
The top 20 recommendations were evaluated using this model to determine if any of the 20 recommendations belong to the playlist/ are good quality recommendations for the playlist. 
The team's two-part machine learning model was tested on a variety of playlists, including genre-based and utility-focused playlists (e.g., workout, study). 
The XGboost model was fit to each of these playlists resulting in an average test accuracy of 0.84 and average precision of 0.86 across the playlists tested. 
The model performed best on genre-specific playlists like pop and old-school rap, which had test precisions of 0.93 and 0.94 respectively. 
From these results, it was concluded that playlists that shared a specific genre or music type will typically result in a more accurate classification model, and thus better quality recommendations. 
