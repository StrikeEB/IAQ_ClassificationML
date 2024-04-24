# ML on the edge for Indoor Air Quality Monitoring using Arduino Nano BLE 33 and Edge Impulse

Edge Impulse [link](https://studio.edgeimpulse.com/public/379255/live)

## Indoor Air Quality Challenge and Context

The UK Parliament's report on Indoor Air Quality highlights the critical link between poor indoor air and heightened health risks, including respiratory and cardiovascular illnesses, cognitive impairment, and certain cancers (UK Parliament, 2023). This underscores the significance of addressing indoor air quality concerns, especially considering that individuals spend a significant portion, ranging from 80% to 90%, of their time indoors, encompassing various settings such as homes, workplaces, schools, and transportation.

Poor indoor air quality stems from various sources, including building materials, cooking and heating appliances, consumer products, occupant activities, dampness, and mould, as well as the surrounding environment where buildings are situated. To combat indoor air pollution, multiple strategies can be employed, such as eliminating pollutant sources, enhancing ventilation systems, and employing air purification methods.

However, mitigating indoor air pollution presents challenges due to the trade-off between improving ventilation to enhance air quality and minimizing energy consumption in buildings. Striking a balance is crucial to ensure that indoor air remains at optimal levels without resorting to keeping windows open or operating heating, ventilation, and air conditioning (HVAC) systems excessively.


*Could ML Help Address This Challenge?*

Supervised machine learning (ML) has emerged as a promising approach in air quality analysis, offering potential solutions to mitigate indoor air quality issues (Essamlali et al., 2024). In particular, two main types of ML models have been instrumental in addressing indoor air quality concerns. Firstly, supervised ML classification models are employed to identify and classify different states of indoor air quality, providing insights into the current condition of the environment. Secondly, regression models play a crucial role in predicting continuous values, such as pollutant levels, by considering various factors such as time, location, and weather conditions. These ML techniques offer valuable tools for understanding and managing indoor air quality, paving the way for more effective strategies to ensure healthier indoor environments.


## Application overview and research question development

*Application Overview*

Given the aforementioned challenge, the primary goal off this project is to explore benefits and challenges of real-time classification of indoor air quality and determine if they are caused by activities that are taking place indoors. The project aims to discern various states of indoor air quality by leveraging sensor data collected from embedded devices and supervised machine learning. 

The expectation is that by employing machine learning algorithms directly on the edge, accurate insights into indoor air quality conditions could offer a practical and efficient solution for monitoring and managing indoor environments without having to trade off the energy efficiency. it's proposed to deploy this ML model on the edge in a form of a physical device that would blend in into our homes well.

*Research question iterations and development*

Initially, the project embarked on a broad research question aimed at exploring the feasibility of using machine learning on the edge to monitor indoor environments and predict the causes of air quality deviations. However, recognising the need for specificity and time and resources cnstraints, the focus shifted to a more targeted approach. The second iteration narrowed down the scope to examine the relationship between a *single pollutant* dust levels and a *single acitvity* cooking, employing sensors such as the dust sensor, temperature, and humidity sensors. To facilitate experimentation, the project also delved into enclosure design, aiming to simulate different environmental conditions for testing. However, technical challenges emerged during the wiring phase, leading to the inability to incorporate external sensors, such as the dust sensor. Consequently, the research question underwent further refinement in the third iteration, centring on the prediction of indoor air quality based on temperature and humidity fluctuations attributed to cooking activities. With a revised focus on leveraging the inbuilt sensors of the Arduino Nano BLE 33, the project aims to develop a model capable of classifying indoor environments into distinct states of "Not cooking", "Cooking, fan on" and "Cooking, fan off" as a small of the overall solution for an all rounded and effective air quality monitoring and management tool on the edge.

## Final Research Question investigated

How well can an ML model predict if temperature and humidity in the room increased due to cooking? What are key challenges in training such model?

Sensors required: temperature and humidity. 

The goal is to develop a model that accurately classifies whether the indoor environment is in one of the three states: 
1. Not Cooking
2. Cooking, fan on
3. Cooking fan off

## Enclosure prototyping and design process

The project underwent an enclosure design process encompassing three key stages. Initially, a detailed paper drawing was created, outlining the essential components and features required for the indoor air quality monitoring device. This included provisions for a screen, strategically positioned side holes for sensors, a designated back hole for cable management, and considerations for constructing a durable sauce/oils holder to enhance practicality. 
Subsequently, a cardboard mock-up was crafted to assess the device's size, visual aesthetics, and the functionality of embedded sensors within the enclosure. This phase aimed to validate the design concept and identify any potential shortcomings before proceeding to the final iteration. I used this carboard box to conduct some test using Edge Impusle and it provided useful insights discussed later in the report.
The culmination of this iterative design process would be expected to lead to the development of the final enclosure design, synthesising insights from previous stages to produce a functional and aesthetically pleasing solution ready to be released into market.

## Data
Describe what data sources you have used and any cleaning, wrangling or organising you have done. Including some examples of the data helps others understand what you have been working with.

*Tip: probably ~200 words and images of what the data 'looks like' are good!*

## Model
This is a Deep Learning project! What model architecture did you use? Did you try different ones? Why did you choose the ones you did?

*Tip: probably ~200 words and a diagram is usually good to describe your model!*

## Experiments
What experiments did you run to test your project? What parameters did you change? How did you measure performance? Did you write any scripts to evaluate performance? Did you use any tools to evaluate performance? Do you have graphs of results? 

*Tip: probably ~300 words and graphs and tables are usually good to convey your results!*

## Results and Observations
Synthesis the main results and observations you made from building the project. Did it work perfectly? Why not? What worked and what didn't? Why? What would you do next if you had more time?  

*Tip: probably ~300 words and remember images and diagrams bring results to life!*

## Bibliography
*If you added any references then add them in here using this format:*

1. Last name, First initial. (Year published). Title. Edition. (Only include the edition if it is not the first edition) City published: Publisher, Page(s). http://google.com

2. Last name, First initial. (Year published). Title. Edition. (Only include the edition if it is not the first edition) City published: Publisher, Page(s). http://google.com

*Tip: we use [https://www.citethisforme.com](https://www.citethisforme.com) to make this task even easier.* 

----

## Declaration of Authorship

I, AUTHORS NAME HERE, confirm that the work presented in this assessment is my own. Where information has been derived from other sources, I confirm that this has been indicated in the work.


*Digitally Sign by typing your name here*

ASSESSMENT DATE

Word count: 
