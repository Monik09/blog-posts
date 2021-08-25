## Push Notification using Amazon Pinpoint in Flutter

Amazon Web Services, in early 2021, extended its support for Flutter, which is quite amazing and many new startups have started to use AWS in their flutter applications due to its ease of scalability and support. Amazon Web Service offers a wide variety of options for Flutter, but we're going to focus on Amazon Pinpoint Service today.

Amazon Pinpoint allow users to send push notifications to multiple recipients. To increase sales, companies and organizations can use marketing campaigns to contact their clients. 

Let's figure out how to integrate this into your Flutter application.


### What we are going to use💻?
To start, we need to install the following packages:
<ul>
<li>  [firebase_messaging 10.0.5](https://pub.dev/packages/firebase_messaging)</li>
<li>  [flutter_local_notifications 8.1.1+1](https://pub.dev/packages/flutter_local_notifications)</li>
<li>  [firebase_core](https://pub.dev/packages/firebase_core) </li>
<li>  [amplify_core 0.2.2](https://pub.dev/packages/amplify_core)</li>
<li>  [amplify_analytics_pinpoint 0.2.2](https://pub.dev/packages/amplify_analytics_pinpoint)</li>
<li>  [amplify_flutter 0.2.2](https://pub.dev/packages/amplify_flutter)</li>
</ul>

## Setup Amplify Pinpoint 

1. To install pinpoint in your amplify project, you will need to add amplify analytics service to your flutter project.
2. Run  `amplify add analytics` in your terminal (Make sure you are at root of the project)
![Screenshot_20210824_173824.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629807379751/wJNdQMbnq.png)

3. Select `Amazon Pinpoint service` and then give a name to your pinpoint service resource.
![Screenshot_20210824_173855.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629807291727/YMrFis-GT.png)

4. Press `Y` and then click enter. Your amazon pinpoint service will be added locally.
![Screenshot_20210824_175120.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629807691746/DynhJlPWC.png)
5. Now, to publish it in the cloud, run `amplify push`. 


> Point to be noted: It takes time for amazon analytics to start recording the events. For me, I was able to record events the next morning.

To send notifications from pinpoint, we will need to set up a module that will interact with the app to show the notification. To fulfil this, we have to use **Firebase Cloud Messaging Service** which will send our notification triggered from Amazon Pinpoint to the user.  

## Set up Firebase Cloud Messaging 

#### Firebase Console Setup:
1. Open  [Firebase Console](https://console.firebase.google.com/u/0/?pli=1)
2. Click on `Create Project`
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629808329862/Hzxw8iel6.png)
3. Give a name to your project and press continue.
4. Make sure analytics is enabled and then press continue.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629808476598/ifckB8Yq-.png)
5. Select your country and then create your project.
6. Register your app and follow the steps described there to successfully register the app. 
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629808805019/46ZalyEgH.png)
> Extra focus on initializing firebase SDK and google-services.json file
7. After your app has been registered, go to Engage->Cloud Messaging.
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1629809036364/MohwP3J4-.png)


## Let's write some code

<iframe src="https://giphy.com/embed/iFU36VwXUd2O43gdcr" width="480" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/drunkhistory-comedy-central-drunk-history-iFU36VwXUd2O43gdcr">via GIPHY</a></p>

Make a file named `notifications. dart` and add the following file. In this file, we are handling our notifications from the amazon pinpoint service. 

%[https://gist.github.com/Monik09/2bead3b8a5ba9ec5d440bd65bd837ae9]

In main.dart file, call this function `_configureAmplify()` inside init state

%[https://gist.github.com/Monik09/2b20d1816d436d3d06bd2054faa03a9e]

and add these lines in `main()` function.

%[https://gist.github.com/Monik09/b57104c243bd4b6f89138461bb62b2f0]


It's all. Ohh, wait. Let's check how to trigger our notification from Amazon Pinpoint Service.

## Make a notification from Pinpoint Service Webpage

1. Go to your pinpoint service page from your amplify admins page and then click on the pinpoint service you created. Click on Settings->Push Notifications and enable Firebase Cloud Messaging (FCM). After enabling, there will be a green tick as shown below.
![Screenshot_20210824_171228.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1629811928815/WFMPWdNML.jpeg)

2. Go to Test Messaging and click on `Push Notifications`. To send a message we will be requiring a google device token which we are getting using the `getToken()` function in the `requirements.dart` file. Without this token, we will not be able to send our message. 
Write this token inside the `Device tokens field`. 
![Screenshot_20210824_171101.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1629812128290/QTa0BNAY2.jpeg)
3. Write a message, add a picture URL and send this to the user.
![Screenshot_20210824_171142.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1629812122860/R9KgH6tII.jpeg)
<iframe src="https://giphy.com/embed/l0DAGxZyaWXJncHtu" width="480" height="180" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/demilovato-demi-lovato-made-in-the-usa-l0DAGxZyaWXJncHtu">via GIPHY</a></p>

## Kudos 🎉🎉
Congratulations to everyone who was able to send their first pinpoint service to trigger the notification. Despite it being a long tutorial, you all made it to the end. 

<iframe src="https://giphy.com/embed/ILV8xetoPJO92" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/thread-discussion-august-ILV8xetoPJO92">via GIPHY</a></p>

## Little Bit About Me🧑‍💻🧑‍💻🧑‍💻
Hey developers, I'm Monikinderjit Singh, working on Flutter for more than a year now. My interest in cloud technology is fueled by my need to learn more about it.  I am currently new to hashnode (this is my second blog post). I would appreciate you giving it a like if you find it interesting and leaving a comment if you have a better solution for this topic. It would be awesome if you could give me some feedback on improving my content.
You can connect with me on my [Twitter](https://twitter.com/monikIJS), [Github](https://github.com/Monik09) and  [LinkedIn](https://www.linkedin.com/in/monikinderjit-singh/) .  
