# :cupid: Speed Dating Investigation :cupid:
Project using ML Unsupervised methods to group customers in a speed dating event. By grouping customers at a speed dating event using these techniques, attempting to use data to derive meaningful insights on customer behaviour and preferences.

The first step was to reduce the dimensionality of the dataset (around 120 features). I had to create a custom function to pre-process the data. I also used PCA (Principal Component Analysis), t-SNE, and finally IsoMap to reduce over 50% of the features. 

Later I clustered using K-Means on hand-picked features under the category 'PREFERENCES', where I chose the ideal number of clusters using the Silhoutte method. Once that was achieved I analyzed the clusters by plotting scatter graphs. From these scatter graphs I generated a hypothesis and proved it using other features of the dataset. 

### NOTE: I highly recommend to follow the full notebook, but you can find a summary, key figures, images and the final conclusion below. 


## Results 

### Most relevant features after PCA Analysis


![image](https://user-images.githubusercontent.com/99181273/233694827-74048afc-5adb-4b33-a59e-dfe1594bfb3e.png)


### Calculation of retained data

![image](https://user-images.githubusercontent.com/99181273/233695098-674e2945-66cf-4d81-98bc-aec254318397.png)


### Plotting t-SNE for 'core' features and 'generated' features for dimensionality reduction

![image](https://user-images.githubusercontent.com/99181273/233695339-a3d55702-81da-41ea-9626-d44f5d0a4a6f.png)

We can see here that both shapes are very similar, a sort of diamond shape. We can also see that the 'core' Features t-SNE is more densely packed in the middle.. As the shapes are similar it indicates the generated features can be discarded as they don't display any 'new' data.


### Plotting Iso-Map for further dimensionality reduction 

![image](https://user-images.githubusercontent.com/99181273/233695701-3347673f-e4e5-4389-9539-97feb63f7ad0.png)

We can see here reducing the dimensions even further will lower the density and bring more variance to the data, which is ideal for clustering. 


### Features chosen to cluster on (PREFERENCES)

- 'shared_interests_partner',
- 'interests_correlate',
- 'funny_important',
- 'importance_same_religion',
- 'shared_interests_o',
- 'intelligence_important',
- 'ambtition_important',
- 'shared_interests_important',
- 'sincere_important'

### Silhoutte Score with Kmeans to choose optimal amount of clusters

![image](https://user-images.githubusercontent.com/99181273/233696353-c00e7540-a248-499c-b13c-9a6a49c133d8.png)

We can see that in this case 12 is the ideal number of clusters. 

### Visualizing clusters (Please open image in a new tab) 

![image](https://user-images.githubusercontent.com/99181273/233696669-b3992d39-1fd9-4556-97c3-f2b6a7b63dde.png)

I know this is a hard to graph to see, but we can see a bit of our data. If we consider our y axis variables, shared_interests_partner, and interests_correlate, we can see how some clusters are defined.

- We can see that dark blue clearly prefer funny people.
- That orange types are religous.
- Pinks want the polar opposite from who they are.
- In particular I want to focus on one group.

*Light blues* don't care at all about religion, if their partner is funny, if they their partners are ambitious, or intellligent, or sincere.

Seem they like they would go for anything. This could also mean their standards are lower due for them being in general seen as less attractive, or older.

**Hypothesis**: This cluster is formed by a population of people not considered 'conventionally attractive' and thus have lower standards. We can analyze the distributions of this cluster by sex, race, and especially match rate. To prove the hypothesis correct we would have to see that the majority of this cluster was unsuccessful in matching. 


###  Gender distribution of Light Blues 

![image](https://user-images.githubusercontent.com/99181273/233697464-35c453ec-3293-4dea-812c-05da95ae3ee7.png)

### Race and Gender distribution of Light Blues

![image](https://user-images.githubusercontent.com/99181273/233697618-369ef98f-aca9-4dd6-a2cb-b730db0f7374.png)

### Match Rate of Light Blues (0 - No Match, 1 - Match)

![image](https://user-images.githubusercontent.com/99181273/233697704-3c010543-cc97-407b-a63c-31de8c15b97d.png)

## Conclusion 

As seen our hypothesis was correct, unfortunately our light blues were not very successful in their romantic endeavours. The analysis could continue by sampling the light blues, and apply further analysis with other features. The same methodology could be used to analyze what composed the other clusters. If this was a customer behaviour dataset, we could follow these methodologies to discover customer preferences. 




