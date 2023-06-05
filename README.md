## Deploy-ML-Application-using-OpenShift


### Step 1: Create a simple NLP model using  01-Create-Claims-Classification.ipynb

### Step 2: Exposing the model as an API

In the previous section, we learned how to create the code that classifies a repair based on the free text we enter. But we can't use a notebook directly like this in a production environment. So now we will learn how to package this code as an API that you can directly query from other applications.

Some explanations first:

* The code that we wrote in the notebook has been repackaged as a single Python file, prediction.py. Basically, the file combines the code in all the cells of the notebook.

* To use this code as a function you can call, we added a function called predict that takes a string as an input, classifies the repair, and sends back the resulting classification. Open the file directly in JupyterLab, and you should recognize our previous code along with this new additional function.

*There are other files in the folder that provide functions to launch a web server, and that we will use to serve our API.

### Step 3: Test the Flask application

Launch the Flask API server by running 03_MBR_run_application.ipynb file.  

Test the Flask API by running 04_MBR_test_application.ipynb.

Our API will be served directly from our container using Flask, a popular Python web server.  The Flask application, which will call our prediction function, is defined in the wsgi.py file.

### Step 4: Building the application inside OpenShift

By now the application code is working, We'are ready to package it as a container image and run it directly in OpenShift as a service that we will be able to call from any other application. Follow the steps to setup in OpenShift. The OpenShift Dedicated dashboard can be accessed from the application switcher in the top bar of the RHODS dashboard. 

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.1.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.2.jpg)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.3.png)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.4.png)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.5.png)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.6.png)

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_9.7.1.png)





### Step 5: Testing the application

Copying and pasting the route's link into your browser.

#### cURL from a terminal session:

We can use the OpenShift Web Terminal to access service from a command line.
In the terminal shell, enter a cURL command with sample text like, I turn the key and nothing happens. Replace the localhost in the command with the right hostname for the route, and make sure to include /prediction:

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_10.2.png)
![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_10.2.1.png)

#### From Python code:

Send a RESTful post request with sample text like, I turn the key and nothing happens. Replace the localhost in the command with the right hostname for the route, and make sure to include /prediction:

![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_10.3.png)


#### From a notebook:

We can also test the REST API endpoint from a Jupyter Notebook. Open the notebook named 05_MBR_enter_repair.ipynb. In the first cell, replace the placeholders with the text.
The repair text goes in the my_text field in the file, and the route in the my_route field, as follows:
![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_10.4.png)


Run both cells and see the result.
![test](https://github.com/JasonSCFu/Deploy-ML-Application-using-OpenShift/blob/main/Images/nlp_sandbox_figure_10.4.1.png)
