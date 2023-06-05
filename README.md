# Deploy-ML-Application-using-OpenShift
ML Ops | Flask API | OpenShift | Model deployment 



## Step 1: Create a simple NLP model using  01-Create-Claims-Classification.ipynb

## Step 2: Exposing the model as an API

In the previous section, we learned how to create the code that classifies a repair based on the free text we enter. But we can't use a notebook directly like this in a production environment. So now we will learn how to package this code as an API that you can directly query from other applications.

Some explanations first:

* The code that we wrote in the notebook has been repackaged as a single Python file, prediction.py. Basically, the file combines the code in all the cells of the notebook.

* To use this code as a function you can call, we added a function called predict that takes a string as an input, classifies the repair, and sends back the resulting classification. Open the file directly in JupyterLab, and you should recognize our previous code along with this new additional function.

*There are other files in the folder that provide functions to launch a web server, and that we will use to serve our API.

## Step 3: Test the Flask application

Launch the Flask API server by running 03_MBR_run_application.ipynb file.  

Test the Flask API by running 04_MBR_test_application.ipynb.

Our API will be served directly from our container using Flask, a popular Python web server.  The Flask application, which will call our prediction function, is defined in the wsgi.py file.

## Step 4: Building the application inside OpenShift

By now the application code is working, We'are ready to package it as a container image and run it directly in OpenShift as a service that we will be able to call from any other application. Follow the steps to setup in OpenShift. The OpenShift Dedicated dashboard can be accessed from the application switcher in the top bar of the RHODS dashboard. 

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.1.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.2.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.3.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.4.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.5.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.6.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.7.1.jpg)





## Step 5: Testing the application

Copying and pasting the route's link into your browser.


