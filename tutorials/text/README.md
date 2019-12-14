# Evaluate text with Azure Cognitive Language Services

Learn how to use Cognitive Language Services to analyze text and determine intent.

In this tutorial you will:
* Learn about Text Analytics API
* Sign up for a Text Analytics API key
* Design and build a service with Azure Functions that uses the Text Analytics API to sort text feedback
* Read and write Azure Queue storage messages in a function app with the help of bindings

## Text Analytics API

If you see a text ALL IN CAPITAL LETTERS, what emotions would it convey? If a book review claims that "the ending was unpredictable," is that statement a good or bad thing? How can you find out programmatically what language an email was written in? Text Analytics is about understanding and analyzing unstructured text to answer these kinds of questions. It covers sentiment analysis, key phrase extraction, language detection, and more.

In this module, we're going to focus our attention on sentiment analysis. We'll learn about the Text Analytics API. This cloud-based service from Microsoft provides advanced natural language processing (NLP) over raw text. When you've completed the module, you'll have built a solution with Azure Functions that sorts text feedback based on sentiment.

## Create an access key

Every call to Text Analytics API requires a subscription key. Often called an access key, it is used to validate that you have access to make the call. We'll use the Azure portal to grab a key.

1. Sign into the Azure portal.

2. Click Create a resource.

3. In the Search the Marketplace search box, type in text analytics and hit the Enter or Return key.

4. Select Text Analytics in the search results and then select the Create button in the bottom right of the screen.

5. In the Create page that opens, enter the required values into each field.

6. Select Create at the bottom of the page to start the account creation process. Watch for a notification that the deployment is in progress. You'll then get a notification that the account has been deployed successfully to your resource group.

![Resource created](/images/00.png)

### Get the access key

Now that we have our Cognitive Services account, let's find the access key so we can start calling the API.

7. Click on the Go to resource button on the Deployment succeeded notification. This action opens the account Quickstart.

8. Select the Keys menu item from the menu on the left, or in the Grab your keys section of the quickstart. This action opens the Manage keys page.

9. Copy one of the keys using the copy button.

![Keys](/images/01.png)

### Call the API from the testing console
Now that we have our key, we can head over to the testing console and take the API for a spin.

10. Navigate to the following URL in your favorite browser. Replace location with the one you selected when creating the Text Analytics cognitive services account earlier in this unit. For example, if you created the account in eastus, you'd replace location with eastus in the URL: https://location.dev.cognitive.microsoft.com/docs/services/TextAnalytics.V2.0

The landing page displays a menu on the left and content to the right. The menu lists the POST methods you can call on the Text Analytics API. These endpoints are Detect Language, Entities, Key Phrases, and Sentiment. To call one of these operations, we need to do a few things.

* Select the method we want to call.
* Add the access key that we saved earlier in the lesson to each call.

11. From the left menu, select Sentiment. This selection opens the Sentiment documentation to the right. As the documentation shows, we'll be making a REST call in the following format.

https://location.api.cognitive.microsoft.com/text/analytics/v2.0/sentiment

location is replaced with the location that you selected when you created the Text Analytics account.
We'll pass in our subscription key, or access key, in the ocp-Apim-Subscription-Key header.

### Make some API calls
12. In the Open API testing console section of this page, select the button corresponding to the location or region in which you created the Cognitive Services account. Selecting this button opens the live, interactive, API console.

13. Paste the access key you saved earlier into the field labeled Ocp-Apim-Subscription-Key. Notice that the key is written automatically into the HTTP request window as a header value.

14. Scroll to the bottom of the page and click Send.

15. Let's examine the sections of this screen in more detail.

In the Headers section of the user interface, we set the access, or subscription, key in the header of our request.

![Headers](/images/02.png)

Next, we have the request body section, which holds a documents array. Each document in the array has three properties. The properties are "language", "id", and "text". The "id" is a number in this example, but it can be anything you want as long as it's unique in the documents array. In this example, we're also passing in documents written in three different languages. Over 15 languages are supported in the Sentiment feature of the Text Analytics API. For more information, check out Supported languages in the Text Analytics API. The maximum size of a single document is 5,000 characters, and one request can have up to 1,000 documents.

![Body](/images/03.png)

The complete request, including the headers and the request URL are displayed in the next section. In this example, you can see that the requests are routed to a URL that begins with westus. The URL differs depending on the location you selected when you created your Text Analytics account.

![URLrequest ](/images/04.png)

![HTTP Request](/images/05.png)

Then we have information about the response. In the example, we see that the request was a success and code 200 was returned.

![Response](/images/06.png)

Finally, we see the response to our request. The response holds the insight the Text Analytics API had about our documents. An array of documents is returned to us, without the original text. We get back an "id" and "score" for each document. The API returns a numeric score between 0 and 1. Scores close to 1 indicate positive sentiment, while scores close to 0 indicate negative sentiment. A score of 0.5 indicates the lack of sentiment, a neutral statement. In this example, we have two pretty positive documents and one negative document.

![Content Response](/images/07.png)

Congratulations! You've made your first call to the Text Analytics API without writing a line of code. Feel free to stay in the console and try out more calls. Here are some suggestions:

* Change the documents in section number 2 and see what the API returns.
* Try the other methods, Detect Language, Entities, and Key Phrases, using the same subscription key.
* Try to make a call from a different region with your subscription and observe what happens.

The API testing console is a great way to explore the capabilities of this API.