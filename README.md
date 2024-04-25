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

Initially, the project embarked on a broad research question aimed at exploring the feasibility of using machine learning on the edge to monitor indoor environments and predict the causes of air quality deviations. However, recognising the need for specificity and time and resources cnstraints, the focus shifted to a more targeted approach. The second iteration narrowed down the scope to examine the relationship between a *single pollutant* dust levels and a *single acitvity* cooking, employing sensors such as the dust sensor, temperature, and humidity sensors. The expected results would be to see 4 distinct clusters as per the following graph:

![4 states](https://github.com/StrikeEB/IAQ_ClassificationML/blob/main/4%20states%20for%20dust%20and%20cooking%20test.png)

To facilitate experimentation, the project also delved into enclosure design, aiming to simulate different environmental conditions for testing. 

However, technical challenges emerged during the wiring phase, leading to the inability to incorporate external sensors, such as the dust sensor. 

Despite efforts to troubleshoot and resolve the issues, including conducting blink tests, verifying wiring connections with both 3.3v and 5v power sources, and checking cables for any faults, the desired functionality could not be achieved. Additionally, attempts to incorporate different types of screens, namely LED and OLED, were met with limited success; while the LED screen emitted light but failed to display text, the OLED screen did not illuminate at all. Despite downloading necessary libraries and experimenting with various code snippets from previous projects, including seeking guidance from ChatGPT, the challenges persisted. 

![wiring](https://github.com/StrikeEB/IAQ_ClassificationML/blob/main/wiring.png)

Consequently, a decision was made to shift focus towards learning machine learning techniques, prompting a revision of the research question to leverage the capabilities of the Arduino Nano BLE 33's built-in sensors.

The research question therefore went through a third revision and decision was made to focus on the prediction of indoor air quality based on temperature and humidity fluctuations attributed to cooking activities. With a revised focus on leveraging the inbuilt sensors of the Arduino Nano BLE 33, the project aims to develop a model capable of classifying indoor environments into distinct states of "Not cooking", "Cooking, fan on" and "Cooking, fan off" as a small of the overall solution for an all rounded and effective air quality monitoring and management tool on the edge.

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

![Enclosure](https://github.com/StrikeEB/IAQ_ClassificationML/blob/main/enclosure.png)

## Model Development Plan

A comprehensive model development plan was formulated drawing inspiration from EdgeImpulse Academy's introductory course on YouTube (EdgeImpulse, n.d.). The plan entails six sequential steps to ensure a systematic approach to model development. Initially, the focus was on dataset collection, followed by the random division of the dataset into training, testing and validation subsets. Subsequently, the model was trained, and parameters were selected, leveraging the insights gained from the training process. Validation procedures were then conducted to assess the model's performance and fine-tune hyperparameters as necessary. Finally, the model's efficacy was evaluated through testing on unseen data, facilitating live classification of indoor air quality states. This structured approach provided a framework for methodical model development and refinement, aligning with best practices in machine learning implementation.

![Model Development Plan](https://github.com/StrikeEB/IAQ_ClassificationML/blob/main/model%20development%20plan.png)

## Reflections on model development steps, results and observations

*Step 1 - collecting data*

Step 1 involved collecting a dataset comprising 15 data points, each spanning 10 seconds, for three distinct states: "Not Cooking," "Cooking with Fan On," and "Cooking Fan Off." However, this process was accompanied by several challenges. Primarily, the sensors failed to detect significant changes in humidity or temperature when positioned more than 30cm away from the cooking pot, particularly within a cardboard enclosure. Wen placed outside the enclosure and closer to the cooking pot, moisture appeared on the sensors within 10 minutes and sensors showed flat readings. 
Additionally, various factors such as building characteristics, seasonal variations, and daily fluctuations in temperature can influence indoor air quality and blur the boundaries between different states. For instance, heating systems may alter temperature levels drastically, affecting the interpretation of sensor data. Or in winter mornings there may be natural moisture increase. To mitigate this challenge, a larger and more diverse dataset encompassing samples from different seasons, times of day, and heating conditions may be necessary. Furthermore, the intensity and duration of cooking activities can vary, resulting in fluctuations within the thresholds for "Cooking" states. Different cooking methods, such as frying versus simmering, may produce varying levels of airborne pollutants, further complicating the classification process. Moreover, transitional periods between states add another layer of complexity. For example, the shift from "Cooking with Fan Off" to "Cooking with Fan On" involves a gradual change in indoor air quality, necessitating a nuanced approach to classification. In such scenarios, regression methods offer advantages over classification, as they can predict time-series values and capture transitional trends more accurately.

*Step 2 - Randomly divide dataset*


Step 2 involved the random division of the dataset into training and testing subsets. This was accomplished by employing the "Perform train/test split within danger zone" function within Edge Impulse. The dataset was partitioned, allocating 83% for training purposes and reserving the remaining 17% for testing.
However, this process was not without its challenges. The primary obstacle encountered was the small sample size of the dataset. With only 15 data points per state, the dataset's limited size may not adequately represent the full spectrum of indoor air quality conditions. Consequently, there is a risk of overfitting, wherein the model becomes overly attuned to the nuances of the training data but struggles to generalize its predictions to unseen data. Addressing this challenge may require augmenting the dataset with additional samples to enhance its representativeness and improve the model's performance on unseen data.

![overfitting](https://github.com/StrikeEB/IAQ_ClassificationML/blob/main/overfitting.png)

*Step 3: train the model / choose the parameters*

Flatten processing block and a Classification learning block were chosen to optimise model's performance given the input data collected. The Flatten processing block transforms the input data into a one-dimensional array and the classification block tags output: "Cooking fan on", "Cooking fan off", and "Not cooking". 
Several challenges were encountered during this stage. The Flatten processing block converts the input data into a 1-dimensional array, which may not capture the spatial or temporal relationships present in the raw sensor data. This impacted the model's ability to learn complex patterns and distinguish between different states effectively.
Furthermore, classification is limited to three states, which would lead the model to not recognise any other activity affecting the states or transitioning of states. 
Additionally, with a small dataset, there was a heightened risk of overfitting, wherein the model may become too finely tuned to the training data, compromising its ability to generalise.
Moreover, the model's lacks interpretability which means it is difficult to discern the underlying rationale behind its classifications ie thresholds used. This lack of transparency makes it difficult to understand its decision-making process effectively. 



## Bibliography

* EdgeImpulse. (n.d.). Machine Learning for Sensor Networks [YouTube Playlist]. Retrieved from https://www.youtube.com/watch?v=TgekTwrftcg&list=PL7VEa1KauMQqZFj_nWRfsCZNXaBbkuurG&ab_channel=EdgeImpulse
* Essamlali, I., Nhaila, H., & El Khaili, M. (2024). Supervised Machine Learning Approaches for Predicting Key Pollutants and for the Sustainable Enhancement of Urban Air Quality: A Systematic Review. Sustainability, 16(3), 976.
* Newbiely. (n.d.). Arduino Nano OLED Tutorial. Retrieved from https://newbiely.com/tutorials/arduino-nano/arduino-nano-oled
* UK Parliament. (n.d.). Indoor Air Quality (POST-PB-0054) [PDF]. Retrieved from https://researchbriefings.files.parliament.uk/documents/POST-PB-0054/POST-PB-0054.pdf
* UK Parliament. (n.d.). Written evidence submitted by the Royal College of Physicians (RCP): Environment audit committee | Inquiry into outdoor and indoor air quality targets [PDF]. Retrieved from https://committees.parliament.uk/writtenevidence/121503/pdf/



## Declaration of Authorship

I, AUTHORS NAME HERE, confirm that the work presented in this assessment is my own. Where information has been derived from other sources, I confirm that this has been indicated in the work.


*Digitally Sign by typing your name here*

ASSESSMENT DATE

Word count: 
