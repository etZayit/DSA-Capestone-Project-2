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
  Result: [Uploading 1. Pr"product_category","total_sales"
"Technology","5984248.1820"
oduct category with highest sales.csv…]()

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
- Result: [Uploadi"region","total_sales"
"West","3597549.2755"
"Ontario","3063212.4795"
"Prarie","2837304.6015"
ng 2. Top 3 Regions (Highest Sales).csv…]()

   
3. What were the total sales of appliances in Ontario?
- **SQL Query**
  
       SELECT
       SUM(sales) AS total_sales_appliances_ontario
       FROM
       public.orders
       WHERE
       product_category = 'Appliances'--
       AND province = 'Ontario'
- Result: [Uploading 3. Tot"total_sales_appliances_ontario"
"202346.84"
al sales of appliances in Ontario.csv…]()

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
-Result:[Uploadin"customer_name","total_customer_sales"
"Jeremy Farry","85.72"
"Natalie DeCherney","125.9"
"Nicole Fjeld","153.03"
"Katrina Edelman","180.76"
"Dorothy Dickinson","198.08"
"Christine Kargatis","293.22"
"Eric Murdock","343.328"
"Chris McAfee","350.18"
"Rick Huthwaite","415.82"
"Mark Hamilton","450.99"
g 4. Identify the Bottom 10 Customers by Sales.csv…]()

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
- Result: [Uploading 5. Mo"ship_mode","total_shipping_cost_incurred"
"Delivery Truck","51971.94"
st expensive shipping cost method.csv…]()

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
- Result: [Uploading "customer_name","total_customer_sales"
"Emily Phan","117124.438"
"Deborah Brumfield","97433.1355"
"Roy Skaria","92542.1530"
"Sylvia Foulston","88875.7575"
"Grant Carroll","88417.0025"
6. Most valuable cutomers.csv…]()

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
- Result:  [Uploading 7. Small business "customer_name","total_customer_sales"
"Dennis Kane","75967.5905"
owners with highest sales.csv…]()

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
- Result:[Uploading 8. Co"customer_name","total_orders_placed"
"Adam Hart","27"
rporate customer with the most orders.csv…]()

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
- Result: [Uploading"customer_name","total_customer_profit"
"Emily Phan","34005.44"
 9. Most profitable consumer customer.csv…]()

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
- Result: [Uploading 10. Custome"customer_name","customer_segment"
"Edward Nazzal","Home Office"
"Cindy Chapman","Corporate"
"Henry Goldwyn","Small Business"
"Julie Prescott","Home Office"
"Liz Willingham","Home Office"
"Ionia McGrath","Small Business"
"Eugene Moren","Home Office"
"Laurel Elliston","Home Office"
"Bobby Odegard","Corporate"
"Charlotte Melton","Home Office"
"Ashley Jarboe","Small Business"
"Dennis Bolton","Small Business"
"Susan Vittorini","Home Office"
"Roy Skaria","Corporate"
"Vivek Grady","Corporate"
"Anne Pryor","Consumer"
"Rob Williams","Home Office"
"Mary Zewe","Corporate"
"Jim Epp","Small Business"
"Noel Staavos","Home Office"
"Cynthia Arntzen","Home Office"
"Brad Eason","Small Business"
"Lisa DeCherney","Consumer"
"Helen Wasserman","Home Office"
"Laurel Beltran","Consumer"
"Kalyca Meade","Corporate"
"Duane Huffman","Small Business"
"Ben Ferrer","Corporate"
"Bill Donatelli","Small Business"
"Brian Stugart","Consumer"
"Kristina Nunn","Consumer"
"Christina DeMoss","Home Office"
"Julia West","Home Office"
"Roy Phan","Corporate"
"Carlos Daly","Home Office"
"Alyssa Tate","Small Business"
"Craig Yedwab","Consumer"
"Jim Kriz","Consumer"
"Shirley Daniels","Corporate"
"Patrick Jones","Home Office"
"Bobby Elias","Small Business"
"Trudy Bell","Consumer"
"Tom Prescott","Small Business"
"Helen Andreada","Corporate"
"Frank Gastineau","Small Business"
"Matt Connell","Corporate"
"Nathan Mautz","Home Office"
"Trudy Brown","Small Business"
"Berenike Kampe","Corporate"
"Harold Dahlen","Corporate"
"Amy Hunt","Home Office"
"Alejandro Grove","Consumer"
"Raymond Book","Consumer"
"Nathan Gelder","Home Office"
"Sarah Brown","Consumer"
"Pauline Chand","Corporate"
"Joel Eaton","Home Office"
"Karl Brown","Corporate"
"Sonia Cooley","Corporate"
"Darrin Sayre","Consumer"
"Benjamin Patterson","Corporate"
"Aaron Bergman","Corporate"
"Nora Paige","Small Business"
"Fred Hopkins","Home Office"
"Saphhira Shifley","Corporate"
"Erin Mull","Corporate"
"Anna Gayman","Corporate"
"Maria Zettner","Corporate"
"Resi Polking","Small Business"
"John Grady","Corporate"
"Neil Knudson","Corporate"
"Mitch Gastineau","Corporate"
"Cari MacIntyre","Corporate"
"Stephanie Ulpright","Consumer"
"Denise Monton","Home Office"
"Monica Federle","Corporate"
"Grant Carroll","Corporate"
"Becky Pak","Corporate"
"Grant Thornton","Corporate"
"John Lee","Corporate"
"Tamara Dahlen","Corporate"
"Ben Wallace","Home Office"
"Cindy Stewart","Consumer"
"Harold Pawlan","Small Business"
"Steve Chapman","Corporate"
"Tom Stivers","Small Business"
"Hallie Redmond","Small Business"
"Kean Takahito","Home Office"
"Damala Kotsonis","Corporate"
"Tracy Collins","Consumer"
"Arthur Prichep","Home Office"
"Christine Abelman","Corporate"
"Matt Collister","Home Office"
"Lycoris Saunders","Corporate"
"Julia West","Consumer"
"Tonja Turnell","Consumer"
"Adam Bellavance","Small Business"
"Denise Leinenbach","Home Office"
"Anthony Garverick","Small Business"
"Michelle Ellison","Small Business"
"Tony Sayre","Small Business"
"Sanjit Jacobs","Consumer"
"Mike Caudle","Corporate"
"Jane Waco","Corporate"
"Aleksandra Gannaway","Corporate"
"Roland Fjeld","Corporate"
"Peter McVee","Small Business"
"Amy Hunt","Small Business"
"Sally Hughsby","Consumer"
"Michael Oakman","Small Business"
"Meg O'Connel","Corporate"
"Doug Bickford","Corporate"
"Becky Castell","Consumer"
"Gary Hwang","Home Office"
"Kelly Williams","Corporate"
"Dorothy Badders","Home Office"
"Stephanie Phelps","Consumer"
"Jeremy Pistek","Corporate"
"Janet Lee","Consumer"
"Katherine Nockton","Home Office"
"Randy Ferguson","Corporate"
"Dave Hallsten","Home Office"
"Michael Dominguez","Home Office"
"Muhammed Yedwab","Consumer"
"Bill Eplett","Corporate"
"Benjamin Venier","Small Business"
"Barry Gonzalez","Small Business"
"Peter Fuller","Corporate"
"Luke Schmidt","Home Office"
"Hunter Glantz","Corporate"
"Nick Crebassa","Corporate"
"Rick Bensley","Consumer"
"Victor Price","Consumer"
"Astrea Jones","Corporate"
"Liz Pelletier","Home Office"
"Toby Knight","Corporate"
"John Dryer","Corporate"
"Sean Braxton","Small Business"
"Guy Thornton","Corporate"
"Khloe Miller","Home Office"
"Sonia Sunley","Small Business"
"Joy Smith","Corporate"
"Magdelene Morse","Home Office"
"Muhammed Lee","Consumer"
"Anna Haberlin","Corporate"
"Ricardo Block","Corporate"
"Nancy Lomonaco","Home Office"
"Art Miller","Corporate"
"Jim Sink","Corporate"
"Parhena Norris","Home Office"
"Katherine Nockton","Corporate"
"Joseph Airdo","Consumer"
"Steve Nguyen","Consumer"
"Scott Cohen","Consumer"
"John Castell","Small Business"
"Shahid Hopkins","Small Business"
"Maya Herman","Corporate"
"Marc Harrigan","Home Office"
"Lena Radford","Small Business"
"Brendan Sweed","Consumer"
"Carl Weiss","Consumer"
"Rick Reed","Consumer"
"Darren Budd","Home Office"
"Mark Cousins","Corporate"
"Brooke Gillingham","Small Business"
"Michelle Tran","Corporate"
"John Lucas","Corporate"
"Cyra Reiten","Consumer"
"Brian Moss","Corporate"
"Fred Harton","Home Office"
"Lela Donovan","Corporate"
"Chad Sievert","Corporate"
"Katherine Hughes","Consumer"
"Quincy Jones","Corporate"
"Alejandro Grove","Corporate"
"Speros Goranitis","Corporate"
"Ruben Dartt","Corporate"
"Bryan Mills","Small Business"
"Dianna Vittorini","Corporate"
"Roy Phan","Consumer"
"Brad Thomas","Home Office"
"Cari Sayre","Corporate"
"Carol Triggs","Home Office"
"Valerie Takahito","Consumer"
"Darren Budd","Consumer"
"Jack Garza","Corporate"
"Tamara Willingham","Corporate"
"Greg Tran","Home Office"
"Eva Jacobs","Home Office"
"Maureen Gastineau","Consumer"
"Pete Kriz","Corporate"
"Scot Wooten","Corporate"
"Dave Poirier","Small Business"
"Michael Granlund","Corporate"
"Frank Hawley","Home Office"
"Michelle Ellison","Consumer"
"Sue Ann Reed","Consumer"
"Sean O'Donnell","Corporate"
"Evan Minnotte","Corporate"
"Ritsa Hightower","Corporate"
"Thais Sissman","Small Business"
"Darren Powers","Corporate"
"Joni Wasserman","Consumer"
"John Lucas","Small Business"
"Bruce Stewart","Corporate"
"Christy Brittain","Consumer"
"Joel Jenkins","Corporate"
"Candace McMahon","Corporate"
"Stuart Calhoun","Consumer"
"Laurel Elliston","Corporate"
"Mike Gockenbach","Consumer"
"Victoria Pisteka","Corporate"
"Bill Overfelt","Corporate"
"Tony Chapman","Consumer"
"Ken Dana","Small Business"
"Guy Armstrong","Corporate"
"Barbara Fisher","Small Business"
"Art Foster","Home Office"
"Adrian Barton","Small Business"
"Katharine Harms","Consumer"
"Odella Nelson","Small Business"
"Alex Russell","Home Office"
"Liz Price","Corporate"
"Dave Kipp","Corporate"
"Arthur Wiediger","Corporate"
"Cindy Chapman","Consumer"
"Charles Crestani","Consumer"
"Richard Eichhorn","Consumer"
"Frank Atkinson","Corporate"
"Cari Sayre","Home Office"
"Jason Klamczynski","Small Business"
"Erica Hernandez","Small Business"
"Dionis Lloyd","Small Business"
"Liz Carlisle","Corporate"
"Justin Ellison","Home Office"
"Rick Wilson","Consumer"
"Peter Fuller","Consumer"
"Luke Weiss","Corporate"
"Erin Creighton","Corporate"
"Karen Seio","Consumer"
"Ken Black","Consumer"
"Anthony O'Donnell","Consumer"
"Alice McCarthy","Corporate"
"Michelle Lonsdale","Home Office"
"Rob Lucas","Small Business"
"Toby Swindell","Small Business"
"Tony Molinari","Corporate"
"Clytie Kelty","Small Business"
"Sibella Parks","Small Business"
"Randy Bradley","Small Business"
"Alan Hwang","Small Business"
"Liz Willingham","Corporate"
"Bill Donatelli","Corporate"
"Sarah Jordon","Consumer"
"Robert Waldorf","Home Office"
"Phillina Ober","Small Business"
"Jill Matthias","Consumer"
"Shaun Chance","Corporate"
"Eleni McCrary","Home Office"
"Sean Wendt","Corporate"
"Dorris Love","Home Office"
"Maria Bertelson","Corporate"
"Brian Stugart","Corporate"
"Tom Zandusky","Home Office"
"Larry Tron","Home Office"
"Emily Grady","Home Office"
"Philip Fox","Home Office"
"Charles Sheldon","Corporate"
"Duane Benoit","Home Office"
"Brendan Dodson","Corporate"
"Phillip Breyer","Corporate"
"Jas O'Carroll","Home Office"
"Jay Fine","Consumer"
"Beth Thompson","Corporate"
"Naresj Patel","Corporate"
"Sanjit Chand","Home Office"
"Deanra Eno","Corporate"
"Thomas Boland","Corporate"
"Barry Blumstein","Small Business"
"Mark Packer","Small Business"
"Roger Demir","Consumer"
"Sandra Glassco","Home Office"
"Max Jones","Home Office"
"Kimberly Carter","Small Business"
"Denny Ordway","Small Business"
"Xylona Price","Corporate"
"Brenda Bowman","Small Business"
"Sally Matthias","Corporate"
"Larry Tron","Corporate"
"Jas O'Carroll","Corporate"
"Bobby Trafton","Corporate"
"Duane Noonan","Corporate"
"James Galang","Consumer"
"Carlos Daly","Corporate"
"Olvera Toch","Home Office"
"Valerie Dominguez","Corporate"
"Natalie Webber","Corporate"
"Alan Hwang","Corporate"
"Grant Carroll","Small Business"
"Anna Chung","Home Office"
"Daniel Raglin","Corporate"
"James Lanier","Corporate"
"Craig Carroll","Corporate"
"Ryan Crowe","Small Business"
"Karl Brown","Home Office"
"Brad Thomas","Corporate"
"Roland Black","Small Business"
"Brian DeCherney","Corporate"
"Nora Pelletier","Corporate"
"Paul MacIntyre","Corporate"
"Herbert Flentye","Small Business"
"Bryan Spruell","Home Office"
"Carlos Soltero","Consumer"
"Jay Kimmel","Small Business"
"Michelle Ellison","Home Office"
"Dan Reichenbach","Corporate"
"Cathy Prescott","Corporate"
"Dean Braden","Corporate"
"Marc Crier","Consumer"
"Pete Armstrong","Consumer"
"Dean Percer","Home Office"
"Neil French","Corporate"
"Craig Leslie","Consumer"
"Amy Cox","Home Office"
"Linda Cazamias","Corporate"
"Maxwell Schwartz","Corporate"
"Charles McCrossin","Corporate"
"David Philippe","Consumer"
"Dave Hallsten","Corporate"
"Sean Miller","Small Business"
"Neoma Murray","Small Business"
"Steven Cartwright","Home Office"
"Edward Hooks","Consumer"
"John Murray","Small Business"
"Carol Darley","Home Office"
"Troy Blackwell","Home Office"
"Ellis Ballard","Corporate"
"Fred Chung","Corporate"
"Tamara Manning","Corporate"
"Patrick Ryan","Corporate"
"Mike Pelletier","Corporate"
"Giulietta Dortch","Corporate"
"Corinna Mitchell","Corporate"
"Eudokia Martin","Home Office"
"Annie Thurman","Consumer"
"Roy French","Consumer"
"Carol Darley","Small Business"
"Evan Henry","Corporate"
"Nathan Mautz","Corporate"
"Steven Roelle","Small Business"
"George Zrebassa","Small Business"
"Julia Dunbar","Consumer"
"Cassandra Brandow","Home Office"
"Thea Hudgings","Consumer"
"Ted Trevino","Corporate"
"Todd Boyes","Small Business"
"Patrick Bzostek","Consumer"
"Sung Pak","Small Business"
"Karen Bern","Corporate"
"Mick Crebagga","Corporate"
"Darren Budd","Corporate"
"Joe Elijah","Home Office"
"Becky Martin","Home Office"
"George Bell","Corporate"
"Dan Lawera","Corporate"
"Theresa Swint","Consumer"
"Ed Braxton","Home Office"
"Patrick O'Donnell","Home Office"
"Jesus Ocampo","Small Business"
"Brian Dahlen","Small Business"
"Dennis Pardue","Corporate"
"Corey Catlett","Home Office"
"Don Weiss","Corporate"
"Sam Zeldin","Small Business"
"Bill Shonely","Small Business"
"Alejandro Savely","Corporate"
"Mitch Willingham","Corporate"
"Carlos Meador","Corporate"
"Art Ferguson","Corporate"
"Cynthia Arntzen","Small Business"
"Tony Sayre","Home Office"
"Christine Kargatis","Small Business"
"Ken Lonsdale","Consumer"
"Jonathan Doherty","Corporate"
"Naresj Patel","Small Business"
"Jennifer Halladay","Home Office"
"John Stevenson","Small Business"
"Duane Huffman","Consumer"
"Sheri Gordon","Corporate"
"Carlos Soltero","Small Business"
"Kristen Hastings","Corporate"
"Rachel Payne","Consumer"
"Aaron Hawkins","Home Office"
"Julia Barnett","Home Office"
"David Kendrick","Home Office"
"Amy Cox","Small Business"
"Ralph Kennedy","Corporate"
"Jessica Myrick","Small Business"
"Greg Guthrie","Small Business"
"Larry Hughes","Home Office"
"Janet Martin","Corporate"
"Craig Molinari","Small Business"
"Kimberly Carter","Home Office"
"Susan MacKendrick","Corporate"
"Tim Brockman","Consumer"
"Keith Dawkins","Home Office"
"Erica Smith","Small Business"
"Michelle Huthwaite","Home Office"
"Kean Nguyen","Corporate"
"Giulietta Dortch","Consumer"
"Dianna Arnett","Home Office"
"Jack O'Briant","Small Business"
"Sarah Foster","Corporate"
"Delfina Latchford","Small Business"
"Gary McGarr","Home Office"
"Daniel Lacy","Small Business"
"Frank Merwin","Corporate"
"Liz MacKendrick","Corporate"
"Ivan Gibson","Corporate"
rs that returned items and segment they belong to.csv…]()

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
- Result: [Uploading 11. Ordering by cost DESC to see highest cost methods.csv"order_priority","ship_mode","total_shipping_cost_for_priority","number_of_orders_for_priority_ship_mode"
"Critical","Delivery Truck","10783.82","228"
"Critical","Regular Air","8586.76","1180"
"Critical","Express Air","1742.10","200"
"High","Delivery Truck","11206.88","248"
"High","Regular Air","10005.01","1308"
"High","Express Air","1453.53","212"
"Low","Delivery Truck","11131.61","250"
"Low","Regular Air","10263.62","1280"
"Low","Express Air","1551.63","190"
"Medium","Delivery Truck","9461.62","205"
"Medium","Regular Air","9418.72","1225"
"Medium","Express Air","1633.59","201"
"Not Specified","Regular Air","9734.08","1277"
"Not Specified","Delivery Truck","9388.01","215"
"Not Specified","Express Air","1470.06","180"
…]()
