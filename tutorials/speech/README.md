# **Translate speech in real time with Azure Cognitive Services**

Learn how to translate speech and convert it to text through real-time transcription with the Speech Translation API in Azure Cognitive Services.

In this tutorial you will:
* Learn what speech translation is all about
* Explore the Speech Translation API

## Create a subscription to the Speech Translation API

Let's create a speech-translation subscription by using the Azure portal.

1. Sign in to the Azure portal .

2. Select + Create a resource. In the Search the Marketplace box, type speech and press Enter.

3. In the Results list, select Speech. In the Speech pane, select Create.

![Selecting the Speech API](/images/00.png)

4. Enter a name for your Speech API subscription, such as SpeechTranslator.

5. For Pricing tier, select a tier.

6. Create a new resource group to hold your resources.

7. Select Create to create a subscription to the Speech API.

![Create Speech API](/images/03.png)

After a short delay, your new Speech API subscription will be available, and new API keys will be generated for programmatic use.

With a Speech API subscription created, you're now able to access your API endpoint and subscription keys.

## View subscription keys

To access your Speech Translation API subscription, you'll need to a subscription key that's passed with every request to authenticate the call.

1. In the left menu of the portal, select either Keys or Quick start.

2. You can see the key for the service.

3. Copy the value of KEY 1 or KEY 2 to the clipboard for use in an application.

![Copying the Speech API key to the clipboard](/images/02.png)

## Creating a Console app that performs Speech to text

1. Open Visual Studio 2019

2. Create a Console app with the name SpeechDemo

![Console app](/images/03.png)

3. Add the Microsoft.CognitiveServices.Speech Nuget package to your project

![Speech SDK](/images/04.png)

4. Use the code from [Program.cs](/resources/Program.cs)

5. Replace key and region values in line 12 with the ones from your Azure account.

6. Compile and Test the app.

![Speech Project](/images/05.png)

