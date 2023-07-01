# SpaceShip

# Overview of the datasets
Given 2 datasets: train.csv and test.csv.
train dataset is used for training and validating during cross-validation of the model.
The training dataset consisted of 8693 rows/samples with 14 columns/features (including the target column). The test dataset consisted of 4277 rows with 13 features (the test set does not contain the target variable).

# Columns:
PassengerId - A unique Id for each passenger. Each Id takes the form gggg_pp
where gggg indicates a group the passenger is traveling with and pp is their
number within the group. People in a group are often family members, but not
always.
HomePlanet - The planet the passenger departed from, typically their planet of
permanent residence.
○ CryoSleep - Indicates whether the passenger elected to be put into suspended
animation for the duration of the voyage. Passengers in cryosleep are confined to
their cabins.
○ Cabin - The cabin number where the passenger is staying. Takes the form
deck/num/side, where the side can be either P for Port or S for Starboard.
○ Destination - The planet the passenger will be debarking to.
○ Age - The age of the passenger.
○ VIP - Whether the passenger has paid for special VIP service during the voyage.
○ RoomService, FoodCourt, ShoppingMall, Spa, VRDeck - Amount the passenger
has billed at each of the Spaceship Titanic's many luxury amenities.
○ Name - The first and last names of the passenger.
○ Transported - Whether the passenger was transported to another dimension.
This is the target, the column you are trying to predict

# Pre-processing of the data
○ 'HomePlanet' consisted of 3 different values: Earth, Europa, and Mars. Converting this column to integers as Earth: 0, Europa: 1, Mars: 2 for both train and test data.
○ 'Destination' column also consisted of 3 different values so these are converted to integer values: 'TRAPPIST-1e': 0, '55 Cancri e': 1, 'PSO J318.5-22': 2. This is done for both train and test datasets.
○ Columns like 'Age', and 'Cabin' are having a wide range of values and they are already in integer format so no change.
○ 'CryoSleep' column consisted of True or false values hence these are converted to 1's and 0's. 1 representing True and 0 representing False.
○ The above step is carried out for the columns VIP and Tranported for both train and test sets.

# Correlation Matrix
○ Now almost all the columns are converted to integer values except for the columns like name, PassengerId, etc. 
○ Correlation matrix is constructed in order to determine the relation and dependence of features on one another.
○ Taking only the Transported_numeric column into consideration, we can identify the columns:{Age, RoomService, Spa, VRDeck, HomePlanet, Destination, Cryosleep} are having correlation coefficient values greater than 0.05 and others are less than 0.05. The features whose correlation coefficient values are less than 0.05 will be of less importance so can be neglected. 
○ Therefore we drop all the unwanted columns from the train and test dataset for better accuracy.

# Building model
○ Split the train data into test and train and use it for cross-validation
○ reshaping and encoding of the X and Y values are performed
○ Then the model is trained for different methods such as LogisticRegression, SVM, etc, and measured the accuracies.
○ Found that the highest accuracy was achieved in the case of Logistic Regression-77.787%
○ Finally test set is passed to the model and the outputs are stored in the form of file.csv files with 2 columns: PassengerId and Transportation
