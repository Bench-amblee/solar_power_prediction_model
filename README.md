# Solar Power Prediction Model
## Data Science Project
- For code go to Notebooks: [Notebook 1](/BMR_data_wrangling.ipynb), [Notebook 2](/BMR_exploratory_analysis.ipynb), [Notebook3](/BMR_data_processing.ipynb), [Notebook 4](/BMR_modeling.ipynb)
- For raw data go to Data: [Data](/Data)
- Read the full report here: [Report](/Big_Mountain_Report.pdf)
- View presentations slides here: [Presentation](/BMR_Presentation.pdf)

**Problem Statement**

Big Mountain Resort, a popular resort located in Whitefish, Montana, is rethinking their pricing strategy. With the addition of a new lift chair, the resort’s operating cost has gone up by $1,540,000. How can Big Mountain Resort use data to create a new, competitive price that will offset this and all other operating expenses.

**Goal**

Create a new data-based pricing strategy for Big Mountain Resort to increase revenue and cover their operating expenses. The resort can set whatever price they want but they need to stay competitive and not lose customers. Setting a price too low is just as bad as setting a price that’s too high, a model must be created in order to set a fair price for the facilities that the resort has to offer.

**Method**

Use data from resorts around the country to determine which features correlate most with ticket price. 

![Heatmap](/Images/BMR_heatmap.png)

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

