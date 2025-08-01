# DSA-Capestone-Project-2
Analysis of sales and order data for Kultra Mega Store (KMS),

# Case Scenerio I
1. Which product category had the highest sales?
- **SQL Query**
  
       SELECT
       product_category,
       SUM(sales) AS total_sales
       FROM
       public.orders
       GROUP BY
       product_category
       ORDER BY
       total_sales DESC
       LIMIT 1;
  Result:
<img width="289" height="88" alt="image" src="https://github.com/user-attachments/assets/8680c307-e140-4e83-9dcb-ec40cc42ccb1" />


2. What are the Top 3 and Bottom 3 regions in terms of sales?
- **SQL Query Top 3**
  
       SELECT
       region,
       SUM(sale) AS total_sales
       FROM
       public.orders
       GROUP BY
       region
       ORDER BY
       total_sales DESC
       LIMIT 3;
  - Result/:
<img width="193" height="117" alt="image" src="https://github.com/user-attachments/assets/a500bac9-ba9d-424b-b7c0-5d0656f12891" />

  
- **Bottom 3**

        SELECT
       region,
       SUM(sale) AS total_sales
       FROM
       public.orders
       GROUP BY
       region
       ORDER BY
       total_sales DESC
       LIMIT 3;
- Result: 
<img width="193" height="117" alt="image" src="https://github.com/user-attachments/assets/3321fb2c-4385-4f08-a37e-27984f0a835b" />

   
3. What were the total sales of appliances in Ontario?
- **SQL Query**
  
       SELECT
       SUM(sales) AS total_sales_appliances_ontario
       FROM
       public.orders
       WHERE
       product_category = 'Appliances'--
       AND province = 'Ontario'
- Result:
<img width="289" height="59" alt="image" src="https://github.com/user-attachments/assets/b91d88c7-42ef-4e41-8f43-66534865a72b" />


4. Advise the management of KMS on what to do to increase the revenue from the bottom
10 customers
- **SQL Query**
  
       SELECT
       customer_name,
       SUM(sale) AS total_customer_sales
       FROM
       public.orders
       GROUP BY
       customer_name
       ORDER BY
       total_customer_sales ASC
       LIMIT 10;
-Result: 
<img width="289" height="320" alt="image" src="https://github.com/user-attachments/assets/2824adcf-cd89-43a2-a880-0228afdba057" />


5. KMS incurred the most shipping cost using which shipping method
- **SQL Query**
  
          SELECT
          ship_mode,
          SUM(shipping_cost) AS total_shipping_cost_incurred
          FROM
          public.orders
          GROUP BY
          ship_mode
          ORDER BY
          total_shipping_cost_incurred DESC
          LIMIT 1;
- Result:
<img width="385" height="59" alt="image" src="https://github.com/user-attachments/assets/03d01a36-a431-41c8-811b-34c3c3477fb4" />


# Case Scenario II
6. Who are the most valuable customers, and what products or services do they typically
purchase?
- **SQL Query Most Valuable Customer**
  
       SELECT
       customer_name,
       SUM(sale) AS total_customer_sales
       FROM
       public.orders
       GROUP BY
       customer_name
       ORDER BY
       total_customer_sales ASC
       LIMIT 5;
**SQL Query Typical Purchase**
   
     SELECT
     product_category,
     SUM(sales) AS total_category_sales_for_customer,
     COUNT(*) AS nimber_of_orders_in_category
     FROM
     public.orders
     WHERE
     customer_name IN ('Emily Phan', 'Deborah Brumfield', 'Roy Skaria', Sylvia Foulston', 'Grant Carroll')
     GROUP BY
     customer_name,
     product_category
     ORDER BY
     customer_name,
     total_category_sales_for_customer DESC;  
- Result: 
<img width="453" height="204" alt="image" src="https://github.com/user-attachments/assets/cf199885-c1e5-4231-b1a4-52cca57b00ab" />


7. Which small business customer had the highest sales?
- **SQL Query**
  
       SELECT
       customer_name,
       SUM(sale) AS total_customer_sales
       FROM
       public.orders
       WHERE
       customer_segment = 'Small Business'
       GROUP BY
       customer_name
       ORDER BY
       total_customer_sales ASC
       LIMIT 1;
- Result:
<img width="445" height="59" alt="image" src="https://github.com/user-attachments/assets/ee9a7006-2c54-4311-a790-bbd439f5032d" />


8. Which Corporate Customer placed the most number of orders in 2009 – 2012?
- **SQL Query**
  
       SELECT
       customer_name,
       COUNT(order-id) AS total_ordes-placed
       FROM
       public.orders
       WHERE
       customer_segment = 'Corporate'
       AND order_date BETWEEN '2009-01-01' AND '2012-12-31'
       GROUP BY
       customer_name
       ORDER BY
       total_orders-placed DESC
       LIMIT 1;
- Result:
<img width="346" height="59" alt="image" src="https://github.com/user-attachments/assets/6e254482-7ad3-4b02-9097-2ad257204517" />


9. Which consumer customer was the most profitable one?
- **SQL Query**
  
       SELECT
       customer_name,
       SUM(profit) AS total_customer_profit
       FROM
       public.orders
       WHERE
       customer_segment = 'Consumer'
       GROUP BY
       customer_name
       ORDER BY
       total_customer_profit DESC
       LIMIT 1;
- Result:
<img width="449" height="59" alt="image" src="https://github.com/user-attachments/assets/5c43e84e-4540-43fe-a68e-77457d89760b" />


10. Which customer returned items, and what segment do they belong to?
- **SQL Query**
  
       SELECT DISTINCT
       o.customer_name,
       o.customer_segment
       FROM
       public.orders AS o
       JOIN
       public.order-status AS os ON o.order-id = os.order-id
       WHERE
       os.status = 'Returned';
- Result:
- 
11. If the delivery truck is the most economical but the slowest shipping method and
Express Air is the fastest but the most expensive one, do you think the company
appropriately spent shipping costs based on the Order Priority
- **SQL Query**
  
          SELECT
          order-priority,
          ship_mode,
          SUM(shipping_cost) AS total_shipping_cost_for_priority,
          COUNT(order-id) AS number_of_orders_for_prority_ship_mode
          FROM
          public.orders
          GROUP BY
          order-priority,
          ship_mode
          ORDER BY
          order-priority ASC
          total_shipping_cost_for_priority DESC;
- Result:
<img width="887" height="465" alt="image" src="https://github.com/user-attachments/assets/2167353d-3d43-42ac-a1d0-2a1621e02cf6" />


# Question 4: What should KMS do to increase revenue from the bottom 10 customers?
From the analysis, the bottom 10 customers contributed very little to overall revenue. To address this, KMS should focus on personalized engagement. First, they need to look at each customer’s buying pattern—what products they bought, how often, and their segment (e.g., consumer, small business). With this knowledge, they can offer targeted promotions, discounts, or bundles tailored to those preferences.
For customers who ordered just once or very rarely, KMS can send follow-up emails or calls to re-engage them. For example, offering a discount code on their next purchase could prompt a repeat order. Another tactic is to introduce a referral bonus where these customers get rewarded for inviting others.
Sometimes, low-spending customers just aren’t aware of the full product range. KMS could send curated product recommendations based on their past order. In essence, small nudges, personalized offers, and a bit more attention can turn these low-value customers into active buyers over time.

# Question 5: Which shipping method incurred the most cost for KMS?
According to the data, the Delivery Truck shipping method incurred the highest overall shipping cost. At first, this might seem strange because Delivery Truck is considered the cheapest per unit. But the reason it became the most expensive overall is likely because it was used for a large volume of orders—including orders where it may not have been the best fit.
What this tells us is that the frequency of usage matters. Even a low-cost method becomes costly if used repeatedly without strategic planning. If KMS wants to control logistics costs, they need to assess not just cost-per-delivery, but whether the delivery method truly matches the order size, urgency, and customer need. This insight shows the importance of smarter logistics planning not just picking the cheapest method, but the right one.

# Question 11: Did the company appropriately spend shipping costs based on Order Priority?
Based on the analysis of Kultra Mega Stores’ shipping methods and order priorities, it’s clear that there was a mismatch between how orders were prioritized and how they were shipped. Specifically, Express Air, which is the fastest and most expensive shipping method, was often used for orders marked with Low or Medium priority. This is concerning because those orders did not demand urgent delivery, yet they attracted significantly higher shipping costs.
A specific example of this can be seen in Order_ID 19583, placed by a consumer customer named Michael Johnson. The order was marked with Low Priority but was shipped via Express Air, incurring a high shipping cost of ₦89,980. There was no urgent need based on the priority tag, making this an inefficient logistics decision.
On the other hand, Delivery Truck, considered the most economical but slowest shipping method, turned out to have the highest overall cost. This may be due to volume, but it also points to a possible overuse or poor alignment with actual order needs. If the goal was to save cost on non-urgent deliveries, the execution didn’t fully align with that strategy.
The data showed that shipping choices were not consistently aligned with the stated order priorities. Express Air should have been reserved for critical or high-priority orders only, but in practice, it was used more broadly. If KMS wants to manage costs better, especially in a competitive retail space, it should review its shipping policies and ensure logistics decisions reflect the actual urgency of each order.

# Conclusion
By implementing the recommendations and aligning shipping strategies with actual order priorities, Kultra Mega Stores can reduce unnecessary logistics expenses, improve customer satisfaction, and make more informed operational decisions.
