# Solar Power Prediction Model
## Data Science Project
- For code go to Notebooks: [Notebooks](/sppm.ipynb)
- For raw data go to Data: [Data](/Data)
- Full Report Coming Soon
- Presentation Slides Coming Soon

**Problem Statement**   

Solar plants are a great, clean way to generate energy, however they can be unreliable. It’s impossible to know exactly how much power an individual panel or an entire plant will produce in a day, this can make running a solar power plant an incredibly difficult and unpredictable task. How can we use data to better predict the output of a solar power plant on a given day? 

**Context**     

We've gathered data from two separate power plants in India, including data about each plant’s power generation and relative weather. This data was taken over a 34 day period and takes outputs every 15 minutes. Using this we can get a good idea of how each subset of solar arrays and the plants as a whole performed on a given day

**Goal**

After analyzing this data we should be able to: 
- Predict how much power the plant should generate throughout one day given known weather data
- Determine whether or not a certain array of panels is properly functioning and be able to identify poorly performing panels
- Test our prediction against the real data to determine its accuracy


**Method**

Analyze the individual performance of each array to determine if any arrays are outliers or underperforming

![Arrays](/images/arrays.ind.png)

According to this heatmap, the features that have the highest positive correlation with price are:
- Fast Quads
- Area of Snow Makers
- Runs
- Night skiing ratio

After testing each feature individually against price (using one to one scatterplots), the other important features that stood out were: 

- Vertical Drop
- Total Number of Chairs
- Longest Run
- Skiable Area

**Modeling**

I decided to try two different types of models, a linear regression imputed with the median and mean values, and a random forest model by adding additional classifications. 

- **Linear Regression:** As stated above, this model worked by imputing missing values with median and mean values based on the data we had. With the four features from the heatmap used, this model had a Mean Absolute Error of $9 which was much too high for this scale. 

- **Random Forest Model:** Adding all eight features gave us a model that was much more accurate, with a Mean Absolute Error around $1. This was the model that was used to determine the final ticket price for the resort. After cross validating the two models, this one produced more consistent results and a lower MAE. 

While creating this price model, I also discovered that Big Mountain Resort could save more on operations costs by closing a certain number of runs each day. As seen by this chart: 

![closedRuns](/Images/BMR_closedRuns.png)

The resort could close up to six runs per day without seeing a significant drop in revenue! 

**Conclusion**

The Random Forest Model placed Big Mountain Resorts ideal ticket price at $94.22, much higher than their current price of $81. Therefore in order to increase revenue and lower operation costs, Big Mountain Resort should: 

- Raise ticket price to $89.99 
- Have 4-6 Runs closed each day to save on operations cost


To improve their facilities, encourage higher ticket prices, and improve their resort’s overall appeal: 

- Increase vertical drop (a highly price correlated feature) by 150 ft
- Add one chair lift
- Add an additional run
- Add 2 acres of snow cover

The model suggests that adding this would justify a $2 increase in ticket price, which given Big Mountain’s 350,000 annual visitors would result in approximately $700,000 in additional revenue. 

With these new changes, Big Mountain resort should expect to see a significant increase in their revenue, as seen below: 

![Revenue](/Images/BMR_revenue.png)
