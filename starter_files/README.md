# Your Project Title Here
Throughout this project, the goal was to deploy using Azure ML a model ready to be consumed, as well as a pipeline. 

In order to achieve this, the following key steps have been performed:
1. Train a model using AutoML
2. Deploy the model, providing and endpoint, with its corresponding documentation and logs
3. Consume endpoint to obtain the predicted result from the model
4. Integrate the same process of the previous steps within a pipeline

## Architectural Diagram
![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/Architectural_diagram.png?raw=true) 

## Key Steps
#### 1. Train a model using AutoML: ####
First, dataset was registered for the training:

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/registered_dataset.png?raw=true)

Once registered, and the training is finished, the best model obtained is:

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/best_model.png?raw=true)

#### 2. Deploy the model, generate endpoint, logs, and documentation ####
First, the model was deployed, generating the http endpoint, and Application Insights was enabled to 
register the logs running the python script logs.py (modifying it accordingly beforehand):

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/deployment_with_application_insights.png?raw=true)

Once deployed, I proceeded with the documentation of the endpoint using Swagger. 
In order to achieve this, an http server has to be running to enable the swagger-ui to pull the proper 
swagger.json file (our documentation file, previously downloaded from Azure).

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/swagger_http_request.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/swagger_http_methods.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/swagger_http_methods_2.png?raw=true)

#### 3. Consume the model through the endpoint and benchmark the endpoint ####
Once the endpoint of the model was up and running with the documentation required to call it, I used the endpoint.py script
to obtain the predicted values of the classes of two new rows.

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/consumed_endpoint_model.png?raw=true)

Benchmarking the endpoint:
![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/benchmark_endpoint.png?raw=true)
 

#### 4. Create and publish a pipeline ####
In this step, the same process of training the model and exposing and endpoint for it was done using a pipeline.

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/pipeline_created.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/pipeline_endpoint.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/published_pipeline_overview.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/rundetails.png?raw=true)

![alt text](https://github.com/ignacio-ibanez/Ml_azure_project2/blob/master/starter_files/screenshots/scheduled_run.png?raw=true)

## Screen Recording
https://www.youtube.com/watch?v=wwQre35lPW0

## Future improvements
A possible improvement for the project could be to set a longer timeout value for the step of training
the model with AutoML. This would give AutoML more time to find a better model, and achieve higher accuracy.
Another improvement could be to add some feature to detect when new data has been added to the dataset, and rerun 
automatically the pipeline so that the model uses as well the new data.
