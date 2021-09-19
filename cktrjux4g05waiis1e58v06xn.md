## Why you shouldn't use Flutter Web for your websites right now?

Flutter is an amazing framework developed by Google for mobile development in May 2017. You can create Android and Ios mobile applications with a single codebase. But in early 2021, Flutter web stable was released. But the question is, is it worth using Flutter for your websites?

So today I will be discussing what are the reasons you should think before using Flutter for your websites.

### Table of Contents

- [How Flutter Web works](#how-flutter-web-works)
- [Performance](#performance)
- [SEO](#seo)
- [When you can use Flutter Web?](#when-you-can-use-flutter-web)


### How Flutter Web works

Flutter web is built over the concept of converting dart to js and using it to render the page. With the combination of DOM, Canvas and WebAssembly, the Flutter team has tried to run Flutter web over modern browsers. 
In deep down, Flutter uses a canvas tag. The Canvas tag is an amazing and powerful tag in HTML which is used to draw graphics on the web page. This tag is the reason Search engines don't have any way to understand the content made.

![Ready gif](https://media.giphy.com/media/lrhmB3wPtgckHC7Wl2/giphy.gif?cid=ecf05e4717q9fq55g4pwrmykmuom2appm0mgkn587uws5p29&rid=giphy.gif&ct=g)

### Performance
In terms of talking about performance, I am not really impressed by it. If you have some animations on your website, there's no doubt that performance is going to suffer. I deployed one or two websites on Flutter web and ran the Lighthouse tool to check the quality of web pages. Those of you who work as web developers are aware of just how critical it is for your pages to be of high quality. I have attached the picture of the result(for reference,  [here](https://monikinderjit.web.app)  and let's analyze some important points in it.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632073193480/Glk17JqxU.png)


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632073373021/uWjMGx2XP.png)

If you observe the blocking time it is quite higher than the required(should be around 300ms) and time to first byte(TTFB) is a disaster(it should be between 200-500ms). My website uses some animations and a backend database which are obviously making performance go down.

### SEO
As I stated above Flutter uses canvas to render over HTML, most of the web crawlers are unable to crawl that content. Another thing that makes crawlers difficult is the navigation used in Flutter. It uses hashes for navigation which makes indexing terrible for crawlers.
But you can try to improve SEO for Single Page websites by using semantic labels correctly in your code. But most people out there don't suggest Flutter Web create websites that require SEO for its content posting on Google. 


### When you can use Flutter Web?

1. You can use Flutter web if you are focussing on the 1-page website and have not much competition for SEO(having a unique name ;) ).
2. If you have a mobile application developed on Flutter and Seo and performance don't much matter or the website have only a small feature.
3. You don't like HTML based frameworks. 


### Know More About Me

![know me](https://media.giphy.com/media/3otPoJREeBJxZRxdyE/giphy.gif?cid=ecf05e475sef22waehp89t6kmoi2e6ep01f0r4w0oay4it5d&rid=giphy.gif&ct=g)

Hey developers, I'm Monikinderjit Singh, working on Flutter for more than a year now.
I would appreciate you giving it a like if you find it interesting and leaving a comment if you have a better solution for this topic. It would be awesome if you could give me some feedback on improving my content.
You can connect with me on my [Twitter](https://twitter.com/intent/follow?screen_name=monikIJS), [Github](https://github.com/Monik09) and  [LinkedIn](https://www.linkedin.com/in/monikinderjit-singh/) .