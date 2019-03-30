# A Tableau Story of Mobike Data

The initial version:https://public.tableau.com/shared/HHCZWWJ39?:display_count=yes

The final version:https://public.tableau.com/shared/ZH56KMRBY?:display_count=yes

### Summary
The data set provides a random sample of millions of user usage data for Mobai's urban area in Shanghai, including starting point, destination, lease time, return time, user ID, vehicle ID, transaction number.
+ orderid: Order number
+ bikeid: Bicycle number
+ userid: User number
+ start_time: Order start time
+ start_location_x: longitude of start location
+ start_location_y: latitude of start location
+ end_time:Order closure time
+ end_location_x:longitude of end location
+ end_location_y:latitude of end location
+ track:Riding path
+ start_location:Starting point coordinates
+ end_location:ending point coordinates
+ utility_time:Riding time
+ new_start_location:new coordinates of start location
+ new_end_location:new coordinates of end location
+ distance_ride:trip dist
+ label_start_location:label of start location
+ district:Area to which the order belongs

Since its landing in Shanghai in 2016, Mobi has steadily increased the number of users, the number of orders and the length of riding time.

The number of orders on weekdays is more concentrated and abundant than that on weekends.

42.5% of users use Mobai for short-distance cycling (less than 1 km). The number of users in different areas presents a gradient performance.

Mobay's parking policy for vehicles seems reasonable and orderly, basically meeting the needs of users in different regions to use bicycles.

### Design
1. In order to reflect the trend of the three data, I used a linear graph to express the trend of the data, in order to show the overall operation status of Mobi in August and one month since it landed in Shanghai in 2016. Each point in the graph contains the start_time, the number of users, the order number and the average utility_time.
2. I studied the time points of using cars on one day a week in August and the difference between using cars on weekdays and weekends. On the daily car time point chart, I use the square chart and use the color depth to show the different magnitude of the single day car. Each square contains the starting time of the order, the week of the day and the order number, which can find the peak commuting time of the working day (i.e. 7-8 a.m. and 17-19 p.m.). The color is darker than others, which indicates that the order volume of users has increased sharply in these two stages, while the color change on weekends is not obvious, indicating that the weekend use of cars is relatively average.

The right workday and weekend car usage distribution chart uses the bar chart method, each bar chart contains the starting time of riding, weekdays & weekends of the same kind of order and order id, quantifying the difference between the order; thus more intuitive performance of the use of weekdays and weekends between the two; The difference in the number of cars further supports the conclusion of the left-hand graph.

In addition, using the chart on the left as a filter, adding operations, using the selection mode and clicking on any box, you can display the corresponding order volume and the corresponding workday or weekend on the right chart.
3. I used bar charts to draw the ride time of each user. Each bar chart contains the order quantity information. It was found that 90% of users ride for less than 33 minutes. It can be asserted that most of the users of Mobai use bicycles for short rides.

At the same time, I use the scatter plot method to draw the trend chart of August order quantity, each point contains the date (start_time), week (week) and order number (orderid), adding a filter, which echoes the above figure, more specifically showing the situation of each user riding.
4. After studying the user's riding distance, I then studied the user's riding distance. Firstly, I drew a pie chart by using the sum of the riding distance. At the same time, I created a pie chart for the total distance group, which was within 1 km, 1-6 km, 6-10 km and 10 km away, and marked each group with color, updated the user's order quantity information to the pie chart, and displayed the group's. Percentage, found that 98% of users use bicycles not more than 10 kilometers, and 55.5% of users in 1 to 6 kilometers mostly;

Based on the information of different regions in Shanghai, I used bar chart to draw the distribution map of bicycle usage in different regions. At the same time, I increased the usage of each bicycle. Two groups of data were separated by color, which formed a contrast and enriched the content. It can be found that users in different regions have different vehicle usage habits. The users in Yangpu District use bicycles the most, while Fengxian District use bicycles the most. The use of bicycles in the district and Qingpu district is very bad.

Finally, I use scatter plot method, using the latitude and longitude information of the starting point of the order, to describe the distribution of all orders on the map, which contains regional information, separates them by color, and adds a distance grouping filter to allow the reader to view the distribution of the corresponding areas. The density distribution of the points in the graph proves the arguments of the above two graphs.
5. I use the longitude and dimension of the starting and ending points of orders to draw scatter points on the map, divide the area information by color, each point contains bike information (bikeid). Studying the bike point and user parking point of Mobay Bicycle Company can be used to judge the rationality of the company's policy and the good habits of users. From the background map which contains street information, it can be seen that the bicycle drop points chosen by Mobay Company are generally set on both sides of some important streets and also in some alleys. At the same time, from the distribution map of bicycle parking points, it is also on both sides of the road in general, indicating that the user's parking habits are generally good.
6. In this project, the most time-consuming is through KMeans clustering algorithm, grouping large data and defining the number of clusters, so that the longitude and latitude of the data set can be reversed into address information through Baidu Map API.
7. In the process of data cleaning, we also need to extract a certain number of latitude and longitude coordinates, one by one to form a data object, and then form a path map through Tableau.

### Feedback
1. In the story, your text narrative part is more, and the text box content is smaller, which affects the visual effect. Drag and resize the border of the text box to make the visualization better.
2. There is a problem with the chart "Bus usage on weekdays and weekends". It has no clear meaning and no interactive function.
3. Story point 3, the above chart is not good at using scatter points, which can not reflect the number of specific points and the corresponding order number. Points themselves may overlap (in fact, there is a lot of overlap), and can not draw conclusions from the chart intuitively. If you want to study the user's riding time, use group bar chart or histogram to divide the group distance and display frequency, so as to improve the visualization effect.
4. The chart above uses too many dividers, which affects the visualization effect.
5. There is no sense. It is impossible to see from the map whether parking is reasonable. The map does not show detailed information of streets, subway stations or other prominent geographical indications, nor does it show which areas are suitable for bicycle parking and which are not. It is impossible to judge whether parking is reasonable only according to a longitude and latitude coordinate point. Please reorganize the visualization logic and explain the results correctly.
6. Story 2 is not interactive. Modify as follows, adding a filter
7. The title is too big, which affects the perception.
8. Lack of interaction in bicycle ride duration maps and legend away from target data
9. Story point 6, the whole is meaningless, the audience can not be interested in a single order route, and the order is only a number, for the audience has little meaning. For stories, please start from the theme and draw exploratory conclusions about the overall situation of the data. There is no need to create interactive dashboards and other content. Please reproduce the relevant visualization and explain the results correctly. Modification: Delete the last image.

### Resources
forum:<http://discussions.youdaxue.com/t/tableau/65358>
books:<利用Python进行数据分析>，<统计学>;
