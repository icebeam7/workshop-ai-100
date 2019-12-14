# **Create Intelligent Bots with the Azure Bot Service**

Learn about QnA Maker and how to integrate it with a bot

In this module, you will:
* Create and Publish a QnA Maker knowledge base.
* Integrate a knowledge base with a bot.

## Create a QnA knowledge base

Let's create a QnA Maker knowledge base (KB).

1. Go to the [QnA Maker portal](https://www.qnamaker.ai/).

2. Select Sign in in the upper-right corner and sign in with your Azure credentials.

3. Unless you already have a knowledge base (KB), the portal will point out that you don't have any.

### Creating a knowledge base and QnA Service

4. In the menu at the top of the portal, select Create a knowledge base.

5. Select Create a QnA service. Selecting this button takes you to the Azure portal and signs you in with the credentials you used earlier. You create the QnA Maker service and the associated Azure app service that will host it in this portal. You can also create a QnA Maker service in the Azure portal before you create a knowledge base.

### Provide the QnA Maker service details

6. Provide these details to create the QnA Maker service:

* Enter a globally unique name for your QnA Maker service, such as yourname-qna. Make a note of this name as you'll be using it later.
* Select your Azure subscription.
* Select the F0 pricing tier for the service, which is the free tier.
* Select a location for the service, which should be the same region as the bot service, and near your physical location.
* Create a resource group called LearnRG.
* Select F (three Indexes), the free tier, for the search pricing tier.
* For the search location, select the location you used earlier.
* Verify that the app name is unique. (If it is, it will be marked with a green check mark.)
* Select the location for the website, which should match the location you used earlier.
* You won't be using Application Insights for this test, so disable App insights.
* Select Create.

After a brief deployment process, your resource will be created for the service.

### Connect the QnA Maker service to the knowledge base

7. Return to the QnA Maker web portal tab and refresh the page.

8. The page will refresh. Scroll down to Step 2.

9. The entries under Step 2 won't be filled in, but a link to the account information will be populated.

10. Select your Azure Directory ID, subscription name, and the name of the new QnA service you created earlier.

11. In Step 3, give your knowledge base a name. We'll use the Microsoft Bot FAQ, so you can name it BotFAQ.

### Populate the knowledge base
12. We need some data for our KB. We'll use an existing FAQ as a sample.

13. Download the [Microsoft Bot FAQ zip file](/resources/Microsoft Bot FAQ.zip) and extract it to your local computer.

14. In Step 4 of the QnA web portal process, select Add file, locate the Word document that you extracted in the previous step, and add the document as a source to populate your KB.

15. Under Chit-chat, select The Professional to add a predefined personality to your KB. Chit-chat adds responses for messages like hello and goodbye.

16. Select Create your KB.

After a short time, your KB will be created and the Edit page will load.

### Test your knowledge base

17. To get an idea of how a bot might respond to questions, select Test in the upper-right corner.

18. A test panel opens, ready for a question.

19. Enter Hello and select the Enter key. QnA will respond with "Hello."

20. Enter when will v3 retire? and select Enter. QnA will respond with a message about v3 updates and release information.

21. Enter what is included in v4? and press Enter. Read the response.

You can continue to test the interaction by asking questions and evaluating the responses to get an idea of how the QnA KB is polled for answers.

## Publish a knowledge base

Now that you've created a QnA knowledge base, it's time to publish it so you can access it from a client application.

1. On the QnA Maker Knowledge base page, where you were testing in the previous exercise, select PUBLISH in the menu at the top of the page.

2. Read the message on the next page. It indicates that your KB will move from test to production. It also points out that your KB will be available as an endpoint that you can use in apps and bots.

3. Select Publish.

4. After a short time, a success message will appear (if no errors occur).

5. Note the URL information that appears. You can use the information provided to test the KB with Postman or curl.

If you need to, you can select Edit Service to go back to the KB and make edits.

## Integrate QnA with a bot

Now that you've created and published your QnA knowledge base, it's time to learn how to integrate it with a bot. In this exercise, you'll create a chatbot on the Azure to integrate with the QnA Maker knowledge base you created earlier.

1. In the QnA Maker portal, go to the Publish page, and publish your knowledge base, if it is not already published.

2. Select Create Bot. The Azure portal opens with the bot creation configuration.

3. Enter the settings to create the bot:
* Give your bot an appropriate name
* Choose the Subscription service you have been using for this course
* Select the proper Resource Group
* Choose the location for the bot. Remember that it's best to use the same location as your other services
* Select F0 pricing tier
* The app name should auto-populate
* Choose C# as the SDK language
* Leave the remaining fields at their default.

4. Click Create. In a few minutes, your bot should be created.

### Chat with the Bot

5. In the Azure portal, open the new bot resource from the notification.

6. From Bot management, select Test in Web Chat and test the QnA by asking the bot questions