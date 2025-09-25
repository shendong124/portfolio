1. Data information:
   * Final dataframe shape: 172299 rows x1235 features
   * Columns dropped from recipe original dataframe: RecipeId, Name, AuthorId, AuthorName,   CookTime, PrepTime, TotalTime, DatePublished, Description, Images, RecipeCategory, Keywords,  RecipeIngredientQuantities, RecipeIngredientParts,  AggregatedRating, ReviewCount
   * Engineered numerical features:  average_rating, rating_count, TotalTimeMinutes, DescriptionLength, Instruction_length, ingredient_count.
   * One-Hot encoded features: Seasons, Recipe categories, keywords
   * Count vectorized feature: Ingredient list 
 
2. Model Parameters:
   * KNeighborsRegressor for average rating prediction: default parameters except for n_neighbors=5
   * KNeighborsClassifier for average rating prediction: default parameters except for 'metric' =  'euclidean' and  'n_neighbors' = 15
   * RandomForestClassifier for average rating prediction: default parameters except for n_estimators=100 and random_state=44
   * K-Means: default parameters except for n_clusters = 4, init='k-means++', random_state=42
   * RandomForestClassifier for cluster prediction: default parameters except for random_state=0


3. Performance Metrics
   * KNeighborsRegressor for average rating prediction: MSE= 1.12 | RMSE = 1.06 | MAE = 0.72 | R2 = -0.16
   * KNeighborsClassifier for average rating prediction: best accuracy score from CV = 0.41618 | best metric = euclidean | best n_neighbors = 15
   * RandomForestClassifier for average rating prediction: default parameters except for n_estimators=100 and random_state=44
precision    recall  f1-score   support


           1       0.00      0.00      0.00       757
           2       0.00      0.00      0.00       235
           3       0.00      0.00      0.00       560
           4       0.00      0.00      0.00      2425
           5       0.36      0.16      0.22      9022
           6       0.51      0.09      0.15      6566
           7       0.47      0.92      0.62     14895


   * K-Means: Silhouette Score: 0.0885
   * RandomForestClassifier for cluster prediction: default parameters except for random_state=0
Classification Report:
               precision    recall  f1-score   support


           0       0.93      0.90      0.92      7820
           1       1.00      0.06      0.11        34
           2       0.92      0.89      0.90     18086
           3       0.92      0.96      0.94     25750


   accuracy                                 0.92     51690
              macro avg       0.94      0.70      0.72     51690
          weighted avg       0.92      0.92      0.92     51690


4. Summary and improvement 
   * RandomForestClassifier gave a good performance score to predict all clusters except cluster 1. Low overall performance for cluster 1 could be improved by diverse techniques to over sample the minority class, assign higher weights to the minority class during model training or modify the loss function to penalize misclassifications of the minority class more heavily.
   * The silhouette score of k-means is very low. There are improvement that can be done for the clustering such as:
      * DBSCAN or Gaussian Mixture Models (GMM) for better clustering.
      * Try cosine similarity or Manhattan distance for K-means.