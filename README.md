# Spam-Detection
This project is aimed at detecting spam messages using machine learning algorithms. The project uses a dataset of messages that have been previously labeled as either spam or not spam (ham), and uses this data to train various machine learning models to predict whether new, unseen messages are spam or not.        

# Prerequisites                
To run this project, you will need the following:              
Python 3.x       
Jupyter Notebook        
scikit-learn library         
pandas library          
numpy library             

# let's check for the size of the dataset
data.shape      
(150, 5)     
From this dataset, class and message are the only features we need to train a machine learning model for spam detection, so let’s select these two columns as the new dataset: 

data = data[["v1", "v2"]]               
Now let’s split this dataset into training and test sets and train the model to detect spam messages:             
x = np.array(data["message"])        
y = np.array(data["class"]),br> cv = CountVectorizer()        
X = cv.fit_transform(x) # Fit the Data            
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)           
clf = MultinomialNB()             
clf.fit(X_train,y_train)                
                               
# Now let’s test this model by taking a user input as a message to detect whether it is spam or not:             
sample = input('Enter a message:')              
data = cv.transform([sample]).toarray()           
print(clf.predict(data))               
Enter a message:You won $40 cash price ['spam']
