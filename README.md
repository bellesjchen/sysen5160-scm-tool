# sysen5160-scm-tool
The all in one tool for supply chain mangers
### Donghao Huang(dh734)
### Sijie Chen(sc2944)
### Keshan Chen(kc766)
### Fernando Celaya(fjc49)
#### For detailed documentation (including screenshots), please refer to (https://docs.google.com/document/d/1x1Y2nP7ZF6BjZqnmfv3iMOEAJCe7g9O-JJlvDwo7cjk/edit#)
# Abstract - Fernando
Supply chain management is a key activity of any product-driven company, and its correct or incorrect implementation can have great effects on the bottom line, customer satisfaction and general resilience of the company. As supply chains grow in complexity, more tools have appeared to help guide any supply chain related decision. However, these tools often rely on huge upfront implementation costs and deep integration with other business processes and decision support systems. This creates a significant divide in supply chain management quality between big and small companies, with the latter resorting to heuristics and general rules that tend to be a lot less efficient. In this paper we outline the creation of a modular open source supply chain management tool suited for small businesses, which can be indications to even the least technologically advanced companies. With this tool we hope small businesses can optimize their operations and reduce the advantage of big businesses with the capital needed to perform in-depth inventory analyses. 


# Problem Statement - Donghao
A supply chain is a complex process of transforming items from raw materials into finished products. Conventional supply chains often rely on humans to make many complex decisions, such as the purchase of raw materials for commodities, the configuration of production lines, inventory management, the setting of prices, and the route of transportation to distribution centers. Because of the complexity of decisions and the multitude of variables, most companies' supply chains are often riddled with inefficiencies.

Although many manufacturing companies have been trying to optimize supply chains for many years, the supply chain involves so many variables, such as raw material price fluctuations, unexpected events such as weather disasters in transit, and the well-known bullwhip effect ( a demand distortion that travels upstream in the supply chain from the retailer through to the wholesaler and manufacturer due to the variance of orders which may be larger than that of sales), that the problem has been difficult to properly address.

# Current Solutions - Donghao
Currently, there is already some similar product on the market, like the Saas of the SAP company. However, these products have two common problems. 
## Hard to Implement
Most of the SAP products are not directly specified for the supply chain system. Most of the products are so raw that the company is hard to implement without any help. Therefore, many giant companies need to form a specific department to implement, operate, and upgrade. The middle size companies have to seek the help of some consulting companies, like Accenture and IBM. Many small companies do not have enough resources to implement these products into their supply chain system.

## High Implementation Cost
The high difficult implementation also brings a high implementation cost. The cost is major comes from the license fee, the implementation fee, and the maintenance fee. The company needs to buy a license from the  SAP to get access to the software. The price of the license depends on the size of the company and the function of the software. Normally, companies need to spend thousands of dollars on purchasing or maintaining the license. After the company gets the license, they still need a specific technician to implement, maintain, and upgrade the system. Some companies do not have enough resources to hire a group of technicians, they will have to seek help from a consulting firm to help them launch some period project. Therefore, many small companies can only afford the very low integration. They can only buy some separate models from the SAP and periodically seek help from the consulting firm. 

# Value Proposition - Sijie
### Purchasing & Production & Distribution & Sales Process
Starting from the needs of consumers, the product scheme runs through the whole process of the industry, and provides building block product capability output for each link of the supply chain
### Rich technical reserves
The accumulation of AI capabilities and the improvement of technical reserves help provide a better product and service experience
### Horizontal service delivery capability
Resource integration covering procurement, warehousing, and transportation horizontally, and output of a complete set of services for information flow, logistics, and capital flow
### Product building block platform empowerment
Product modular deployment, platform-based output empowerment, to ensure the flexibility and versatility of product output

# Technical Description

## Demand data input - Fernando
Since the beginning, one of the main objectives of the application has been flexibility. To make a tool that can be useful to a large number of people, that tool must be able to adapt to the business processes of as many potential users as possible. A key part of this flexibility is the data exchange between the user’s IT systems and the app. We decided to resolve this by taking in the historical demand the user already has logged as a .csv file. This is probably the most versatile file we could think of, as it suits businesses of all sizes and can be easily obtained from all types of order databases, from SQL to Excel to Google Sheets. 

We assumed that businesses usually record their order data on a per order basis, with each row being a different order with all information about that order (Customer information, Product information, Sale information, etc.) stored in the different columns. 

The user can upload its .csv by dragging and dropping it, and a preview of all the columns appears below. Then the user must input the column headers as written in the .csv for 4 key general order information points: Product identifier, DC Location identifier, Amount purchased column, Date column. The user then checks the provided information and the app checks whether the given column names correspond to real columns in the file. If they are, the information from the file and the 4 column names are saved. 

The only problem we haven’t been able to solve right now is that sometimes after checking and attempting to save the data the column names are erased, however we haven’t been able to identify when this happens. 

There is also sample data included for people that just want to explore the app. 

##  Visualization - Keshan
To provide the users with an overall and straightforward picture of the statistical information of supply chain, we added the visualization analysis part by linking Plotly with Streamlit. In this part, we used historical supplychain data downloaded from Internet and divided the statistical information into three parts. In the future, after the users implementing their own dataset, this part would provide them with a comprehensive visualization analysis that related to their dataset. 

The first part focuses on the customer segments, markets proportion and order item quantity with number of orders. Users who are browsing this page would comprehend the basic information about the current market and customers. Also, based on the histogram chart on the right, users would be able to learn the relationship between order item quantity and number of orders within that specific quantity, and find out the most frequent order item quantity from this chart. 

The second part is about the order sales within areas, and it is divided into two subparts which presents the numbers, sales and profit of orders distributed in different regions and countries. Users could be able to comprehend the sales information of their products in different areas. For example,in the first four charts, users could find the area with the largest amount of orders as well as area with the highest sales revenue. To make the distribution of profit more clear and add more interaction ways to our app, we also implemented a heat map in which the user could click and see the details in specific area. This heat map could also be reduced or magnified in size when user scrolls the map using mouse, allowing the user to explore the distribution in a more flexible way. 



The third part concentrates on the order shipping. In this part, the user could gain the information about delivery status and shipping mode. We have two pie charts to present the proportion of delivery status and shipping mode calculated by the number of orders. Also, the histogram chart in the middle shows the delivery status in different regions. Based on this part, the user could adjust the delivery mode and storage capacity in different regions to make the delivery process more efficient, which is what they may concern besides the sales of orders. 



## Per product or location analysis - Fernando

A classical demand analysis tool in any supply chain manager’s belt is the Pareto analysis. The Pareto rule roughly states that 20% of products will account for 80% of demand and vice versa. Although these numbers are not set in stone we do see this general behavior emerging very often. Identifying these products can be very useful for the development of several supply chain strategies. In a hybrid made to stock - made to order strategy for example we only carry stock for those items with the highest demand, while capacity is directed to fulfill orders of the lower demand items with a higher priority. 

This analysis could also be useful not on a per product basis, but also on a per location basis where we see where most of the demand for a given product is coming from. 



As we can see we can choose a per product or per location analysis, we choose the desired product or location and we can see the sales data for the different locations - or products if we chose a per location analysis - and that demand is graphed both individually and cumulatively. 
Per product and location pair analysis - Fernando
Even though the previous analysis is useful, usually managers need to analyze the data for a given product in a given location to decide the specific inventory of that product to hold in that location. That is what this analysis allows us to do. It takes a product, a location and a time window as the input and it shows the demand for that pair in that time window. This visual analysis can many times lead to interesting insight, like seeing seasonality in the demand or periods of higher and lower activity. However, many times this human visual examination is not enough. That is where the demand analyzer comes in. 

This analyzer uses the Kolmogorov-Smirnov test to find which distribution best fits the data out of a pre-selected list of continuous distributions: ["chi", "expon", "f", "cauchy", "norm", "t"]
For the pre-selected list of discrete distributions: ["poisson", "binom"] the fitting needs a previous step as the parameters cannot be readily fitted to the data. This fitting to obtain the distribution parameters is done by constructing a histogram with the demand data and fitting the distribution curve to that histogram. 

We then choose the best fitting distribution through the p-value given by the Kolmogorov-Smirnov test, which gives the probability of the null hypothesis being true, with the null hypothesis being that the observed demand follows the given distribution. 

Although many times managers just assume a normal distribution as a proxy for their demand, by examining a larger list of distributions we can decide on a better fitting one. 



Many times however the given demand data is way different from any of the given distributions and none of them have a reasonable p-value. In these scenarios, the tool just assumes a normal distribution and calculates the demand average and variance as the parameters. 

Once the manager is satisfied a save button can be pressed and the product, location, distribution, and distribution parameters are saved for the next analysis. 

In this analysis, we also find a similar problem we haven’t been able to solve similar to the one outlined in the data input part, with the application sometimes refreshing when some of the input parameters are changed. 

## Cost prediction - Sijie
This part is mainly to make some predictions about the price changes of raw materials to help our supply chain system make later inventory decisions. It can forecast unit cost and FCL cost for manually picked dates.

I tried moving average, linear regression, nearest neighbor, AutoARIMA and LSTM, and finally lstm works best. The main reason is because the advantage of LSTM lies mainly in its groundbreaking structure of long and short-term memory. Then the vanishing and exploding gradient problem of RNN is also solved. However, its disadvantage is that it is too complicated and the training time is too long. But fortunately this time we don't have much data, so the results come out relatively fast.

When writing the code, I first normalized the dataset and then built the LSTM network. Sequential represents a sequential model, and the core operation is to add layers to it. In addition to LSTM, you can also add Conv2D, MaxPooling, or Flatten layer,etc. The method of training the model is to use the 60 values in front of each number for training, to predict a total of 248 numbers, and to use the model to predict and convert the standardized data into the original data again. After selecting a suitable dataset, the RMSE value remains below 10, which can prove that our prediction model is still relatively successful.

The final rendering is as follows.

First of all, you can choose the time length of the training data. The reason why you can choose manually here is that there may be some short-term unexpected situations that may cause price fluctuations, such as sudden wars, Black Friday, etc. At this time, you can narrow the time length of the training data set to get a more accurate forecast in the near term. If there are no external factors causing price fluctuations for a period of time, you can make the training data set as large as possible to make predictions more accurate.

Then you can choose to predict unit cost or carrier cost. Unit cost is helpful for future calculation and carrier cost can make the cost more intuitively.

After that, you can choose the date you want to source the raw material.

The system will give you a prediction value.

There are still some shortcomings in this algorithm, for we do not take many variables into consideration. In next step I want to further adjust the prediction model by modifying various parameters, such as changing the number of LSTM layers, increasing the training algebra, etc.
Inventory management - Donghao
 This part mainly helps the logistic engineer set up the proper order size, fill rate, and safety stock level, and picks the proper shipping method. This part will integrate with the most common strategy, the order-up-to policy, in the supply chain industry. The order-up-to policy is to set up the protection safety stock level in the inventory house to guarantee the fill rate, and the logistic engineer will make the order depend on the shipping lead time. This part will also demonstrate the operation cost lively to help the logistic engineer find out the optimal inventory management parameter.

According to the information input by the stakeholders(the holding cost, backorder cost, and the shipping method), we will calculate the most economical order size. This amount is calculated following the equation of the economic order quantity model and the following formula. (D: demand rate, S: order cost, H: holding cost). We will also suggest customer service levels based on the economic aspect follow the critical ratio. The equation is following: (h: holding cost, b: backorder cost). 
We also let the supply chain manager decide what is the final customer service level they want to achieve.
 The application will also calculate the target inventory the system need to maintain based on the fill rate set up by
 the stakeholder.  Following the equation  
The final inventory cost calculation is based on the equation that: Inventory cost = average inv*holding cost*order-times*shipping-time. And the operation cost is the following equation: Operation cost = Inventory cost + shipping cost*order times.

All the calculation above is based on the assumption that the customer demand and order demand are normally distributed. And all the demands we collected are identical independent across the location and time. In the future, to make the SCW close the reality and more functional, the inventory demand should deeper corporate the actual demand distribution model. Another assumption made in the inventory model is the shipping time is fixed. However, in the reality, the shipping time also fluctuates. In the further development, we also need to build up the model of the shipping time simulation to better build up more accurate shipping time estimations and get more precise inventory cost models.

## Streamlit - Fernando
In order to build the whole application Streamlit was used, as it is very easily integrated with the python code and can create very visually appealing and responsive web applications. Furthermore, Streamlit provides hosting capabilities for free tied to GitHub repositories, so anyone can access our tool at any time. 

In order to create the desired multi page structure, we decided to use a library called streamlit-multipage. This library allows to create different pages which can be better organized in different files, it provides the navigation to interface between the pages and allows the application to be state-persistent. This was a key requirement for our tool, as we wanted to organize the different functionalities in different pages and allow the user to travel between them with the tool storing the choices and data input provided in other pages. Here we see for example the welcome page with the interface for page changing. 



# Use case - Sijie

1.Choose the delivery mothod
1.1Data Collection
1.2Find the order cost
1.2.1Material Cost Prediction
1.2.1.1Unit Cost
1.2.1.2Carrier Cost
1.2.2Shipping Cost Estimation 
1.2.3Exchange Rate Changes Estimation
2.Find the recommended customer service level
3.Find the most economical order size
3.1Find the customer demands
4.Find the target inventory
# Stakeholders - Donghao
The Supply Chain Wizard(SCW) is a powerful tool that can help the supply chain department improve working efficiency and working performance. The financial department can be also benefited from the tool by its strong flexibility and data visualization part. The following is the major stakeholder of the app system. 
 
## Production Planner
The SCW utilized the data analysis method to build up the model of the customer demand which can help the production planning engineer generate reliable demand predictions. The precise demand prediction can greatly contribute to a stable production plan. Currently, most of the production capacity is occupied by the expedited order, which is generated by the wrong demand prediction. The production department needs to cost a large amount of resource to revise the production plan. With the precise prediction of demand, the amount of expedited orders will largely decrease. The production capacity will be largely released. As a result, the ability of the risk resists and the average production amount will largely increase.  

## Logistic Engineer
The logistic engineer is mainly responsible for the management of the logistic system and the inventory management in the supply chain system. The SCW can help support the job of a logistic engineer in both systems. Normally, there are two delivery methods for international shipping, which are marine shipping and air cargo shipping. Marine shipping needs low cost but the lead time is very long. On the contrary, air cargo shipping requires high shipping costs but can largely shorten the shipping lead time.  The SCW can quickly simulate the operation cost of different shipping methods help them to make the decisions. At the same time, the SCW will also provide the most economical order size to help the engineer make the decision. For inventory management, the SCW can help logistic engineers determine the safety stock level. The safety stock level is closely related to the fill rate (the probability that the manufacturer is able to fulfill the demand), and the shipping leads time. The SCW can quickly help the logistic calculate the safety stock level under different scenarios. The higher fill rate requires a higher safety stock level. Therefore, the extremely high fill rate will boost the operation cost to very high. The SCW will provide the most economical fill-rate suggestion to the logistic engineer. 

## Procurement Engineer
Normally, the largest proportion of the operation cost is the production cost which is closely related to the raw material cost. The raw material price fluctuates fiercely cross time. The SCW uses time-series technology to predict the specific price of raw material price to help the procurement engineer make the budget model. The SCW will also provide a graph of the price trend to help the buyer find out the proper time to make the purchasing order. The demand prediction can also largely help the procurement department predict the total volume they need to purchase in the following year. The precise volume can help the buyer get the proper volume discount.

## Financial Department
The SCW has a clear data visualization and a clear operation cost summary. All this information can help the financial department quickly extract the information they need to build up the operation model and the budget model for the company.

# Further Development - Keshan
After implementing all the method and finalizing our app, we have several ideas of the further development of our app. Firstly, since the app is run by Streamlit, when we change the data input or import a different dataset, the whole page would be reloaded, which costs a very long time to wait for the whole page refreshing with new data input or dataset. Moreover, when the page is reloaded, the previous data and output would be lost and replaced with new data, which is inconvenient when the user wants to compare different output with different data input. For this problem, we would find an alternative way or platform to deal with this problem in the future. Secondly, our current data visualization is based on the historical data which has already imported to the py file when running the program. Users would prefer to see the visualization of their own dataset, so our further development for this demand is that we should make the data visualization module adaptable to the user’s dataset. Then it would be more clear, straightforward and comprehensive for them to be able to know their supply chain information as much as possible. For the inventory analysis, in the future, we want to relate the cost prediction to cost input to make it more reliable. Also, for the prediction module, our training and testing data are all historical data that downloaded from Internet. In the future, we should make the prediction module be able to use any cost file that the use uploaded and train the model using the uploaded dataset instead of the pre-imported one. 



I have written some ideas here related to some parts, there are very probably others
App is too slow due to Streamlit reloading the whole page every time a data input change is made
Sometimes when a data input change is made the page completely refreshes and the previously made changes are lost. 
Making the data visualization module adaptable to any .csv demand data input
Relating the cost prediction to cost inputs in the inventory analysis
Being able to upload any cost file for the prediction module

# Implementation Plan - Fernando

All the previous changes should be implemented by first talking with stakeholders to identify any other problems or additional features we have not thought about. After recording all necessary features and bug fixes needed to progress, the next step would be to rank urgence and work needed. Then these features and bug fixes must be progressively carried out. A key in this execution step relies on the application being open source, so any stakeholder or developer can carry out these fixes or implement any further features they see fit. 

The success of the implementation plan will be judged on the adequate implementation of the new features/ bug fixes. As a final Long term goal, The tool could be deemed as successful when someone decides to use it for a real world application in supply chain management or as an educational tool in a supply chain course. 


References
1. 	Cabrera D.; Cabrera L. Systems Thinking Made Simple: New Hope for Solving Wicked Problems. Ithaca, NY: Odyssean; 2015.
2. 	Cabrera D, Mandel JT, Andras JP, Nydam ML. What is the crisis? Defining and prioritizing the world’s most pressing problems. Front Ecol Environ. 2008;6: 469–475. doi:10.1890/070185
