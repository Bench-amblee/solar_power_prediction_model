# ☀️ Solar Power Prediction Model ⚡️
## Data Science Project
- For code go to Notebooks: [Notebooks](/sppm.ipynb)
- For raw data go to Data: [Data](/Data)
- Full Report Coming Soon
- Presentation Slides Coming Soon

**Problem Statement**   

Solar plants are a great, clean way to generate energy, however they can be unreliable. It’s impossible to know exactly how much power an individual panel or an entire plant will produce in a day, this can make running a solar power plant an incredibly difficult and unpredictable task. How can we use data to better predict the output of a solar power plant on a given day? 

**Context**     

We've gathered data from two separate power plants in India, including both power generation and meteorological data. This data was gathered over a 34 day period and takes outputs every 15 minutes. Using this we can get a good idea of how each subset of solar arrays and the plants as a whole performed on a given day

**Goal**

After analyzing this data we should be able to: 
- Predict how much power the plant should generate throughout one day, one month, or one year given previous weather data
- Determine whether or not a certain array of panels is properly functioning and be able to identify poorly performing panels
- Test our prediction against the real data to determine its accuracy


**Method**

Analyze the individual performance of each array to determine if any arrays are outliers or underperforming

![Arrays](/images/arrays_ind.JPG)    

No one array was dragging the pwoer plant down, but too double check we compared the each array to the average for each day and found, once again, that no one array was under or overperforming.   

![Array 1 Compared to Average](images/array_v_average.JPG)    

**Nominal Operating Cell Temperature**    

Halfway through the exploratory data analysis, we learned about the equation for Nominal Operatig Cell Temperature, which is not only a way to predict the temperature of the solar cells but also analyze it's overall efficiency.

![NOCT Calculation](images/NOCT_calculation.JPG)

Using this, in addition to finding out which variables were most important through a correlation heatmap, we were able to determine that the most important features for creating our model were:

- DC Power (kW)
- Ambient Temperature (C°)
- Module Temperature (C°)
- Solar Irradiation (W/m²)

**Modeling**

This time around we tried three different models, and because we already had the equation to tell us exactly what our power output values should be, we had very good testing/train splits. The three models we tested were as follows:

- **Linear Regression:** A simple, normalized linear regression witha test size of 0.25. This worked really well because our many of the relationships between variables were already linear. With high model score and a low Mean Absolute Error this looked like a great pick at first.

- **Random Forest Model:** This model was imputed with the mean and with 12 estimators for our data pipeline. The results were underwhelming, with a much lower score than the linear regression and higher MAE.

- ** Gradient Boosting:** Initiall this model yielding a MAE of around -10 but with some improvements to the hyperparameters, notably increases the number of trees to 70, we eventually got a great model score and an even lower MAE.

To properly determine which model would most accurately predict the daily power output, we decided to make two random sets of data and each model against a control using the same random data. On the far right you'll see the "real" data, meaning what the power output should look like and to the left you'll see how each model performed.

![Model Performances](images/model_test.JPG)

As you can see, the Gradient Boosting model was closest. To further verify this we made a new, much larger set of random data and compared the two again:

![Model Larger Performances](images/model_large.JPG)

The Gradient Boosting Model was the most accurate for predicting power output!

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
