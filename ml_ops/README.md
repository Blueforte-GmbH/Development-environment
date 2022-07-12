# Ml Ops architecture

Architectures are fairly complex. MLOps is simply machine learning and operations mixed together and running on top of cloud based or on premise infrastructure and resources.


## Dynamic vs Static training architecture
1. Orchestrated training architecture. 
Training architecture for scenarios where you have to retrain your model but the data ingession changes from time to time. A workflow orchestration tool is used to schedule the extraction and processing

Training the model here can be either manually triggered or scheduled using a scheduler. 

This architecture is particularly useful for problems where users don’t need real-time inference.

[Orchestrated training](https://miro.com/app/board/uXjVO31Hw0Q=/?moveToWidget=3458764529209335628&cot=14)


2. Real time messages based training architecture. 
This sort of training architecture is useful when you need continuous model training. For example:

- New data arrives from different sources (eg mobile app, web interaction, and/or other data stores).
- We subscribe to the message broker so that when data comes in from the streaming service for eg Kafka, it pushes a message to the message broker, the message broker sends a message to the data pipeline to extract data from the warehouse. 
- Once the transformation is over and data is loaded to storage, and then fed into the training system 


It joins the data service (data pipeline) and the training service (training pipeline) into a single system, so that training is continuous across each job. You may need this training architecture, for example, when you need to refresh your model on real-time transactions (fraud detection applications).

[Real Time architecture](https://miro.com/app/board/uXjVO31Hw0Q=/?moveToWidget=3458764529210704819&cot=14)



# Dev Ops Best practices
1. Code Quality check
For a Python based code it is best to stick with the conventions. For example, Python’s recommendations for naming conventions are included in [PEP 8: Style Guide for Python](https://peps.python.org/pep-0008/#naming-conventions). 


2. Testing

![Image](/ml_ops/img/testing.jpeg)

- Unit Testing: 
Every function in the code base needs to be tested. This is very well known as Unit Testing. 
- Component testing
Given a system has many microservices, every service would be tested
- End to End test
We basically want to test inputs from one system and fed correctly into another system. 


3. CI / CD
Tests make no sense if there are not continuously. 

A general practice is to test the above mentioned code continuously using a CI CD framework like Github actions or Circle CI. 

