# GCP-Mini-Cloud-Function
Cloud functions are serverless function as a service (FaaS) that are executed in response to an event. An event could be something like an HTTP request, adding data to Cloud Storage etc.

### Deploying Cloud Functions
Either create the cloud function in the console or command line:
```
gcloud functions deploy hello_get --runtime python39 --trigger-http --allow-unauthenticated
```
where the hello_get command is in a Python file named main,py:
```
 26 def hello_get(request):
 27     """HTTP Cloud Function.
 28     Args:
 29         request (flask.Request): The request object.
 30         <https://flask.palletsprojects.com/en/1.1.x/api/#incoming-request-data>
 31     Returns:
 32         The response text, or any set of values that can be turned into a
 33         Response object using `make_response`
 34         <https://flask.palletsprojects.com/en/1.1.x/api/#flask.make_response>.
 35     Note:
 36         For more information on how Flask integrates with Cloud
 37         Functions, see the `Writing HTTP functions` page.
 38         <https://cloud.google.com/functions/docs/writing/http#http_frameworks>
 39     """
 40     return 'Hello World!'
```
The above command assumes that there is a function `hello_get` in some file in your working directory and that your function is written in Python. It uses HTTP requests as triggers and allows you to customize your authentication.

When you make a request to the functions url (something like https://us-central1-[PROJECT_ID].cloudfunctions.net/[FUNCTION_NAME]), the cloud function will execute. You can see the statistics about memory, compute, invocations / sec, and execution time in the dashboard (when you click on your function name in the console).

### Cloud Function Triggers
There are 8 different possible Cloud Function triggers:
1. HTTP
2. Cloud Storage
3. Cloud pub/sub
4. Firestore
5. Firebase (3 possible options)
