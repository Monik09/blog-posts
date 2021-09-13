## How to create a Hover Effect in Flutter in minutes?

Are you wondering how you can create a hovering effect in Flutter(Web) as Flutter does not provide a single widget to do that? 
The hovering effect is one of the most important features in all e-commerce websites/apps. It is generally used to ask for extra user attention and action. So it's important to know how we can do that in Flutter.

So buckle up your seat belts and let's dive into it.

%[https://media.giphy.com/media/Wp7qEwWS8sx7KR9Xql/giphy.gif?cid=ecf05e475d1jt5zex2rfy1gmfz1ms1z8da7pytosjvlxkhx8&rid=giphy.gif&ct=g]

## What's the content
We will be using Flutter's in-built features to implement a hovering effect. So no need to add expensively (cool down, I know they are free but I'm saying in context to efficiency and code) and non-efficient (most of the packages are badly written) to have this simple effect. We will be going through:
1. Setting up the Flutter project
2. Brief Intro to InkWell
3. Whats' this Animated Container?
4. Implement Hovering effect

### Setting Up Flutter Project
**Step 1**: Go to cmd/terminal and type `flutter create <project_name>`</br>
**Step 2**: Type `cd <project_name>` in terminal and run flutter pub get</br>
**Step 3**: Now lets remove this boiler plate code and start working.


> Tip: You can simply press `Ctrl+F` and enable regular expressions (`Alt+r`). Type `//.*` and all the commented lines will be selected. Now you can replace it with empty space and press Ctrl+F or any key binding you have set for formatting. 

Ok cool, we are now ready to understand our widgets to be used.

### Brief Intro to InkWell
InkWell is an amazing material widget in Flutter which comes with many in-built features such as splashColor, onLongPress and many more. Some of the important parameters for our purpose are listed in the table below:


%[https://gist.github.com/Monik09/3ab484e39c3181caec2759e1d0f07ac4]


Let's answer some of your questions:

> Ques1: So why are we using InkWell?</br>
The question lies in the above table. As we can see the InkWell has an onHover function which is called when the user brings in/out the mouse to the widget. </br>

> Ques2: So whats' our idea?</br>
We will be using this amazing feature by InkWell to change the boundaries of the container which will look like a hovering effect.

> Ques3: Hey but the container has fixed height and width and not a good animation too when increasing size. How we will cope up with this?</br>
So that's our next section, Animated Containers. Let's quickly go there.


### Whats' this AnimatedContainer?
AnimatedContainer is a special Container that helps us give more wizardly powers to a simple Container. As the name suggests, it is a container with the capabilities to add animations. 

> Animated version of Container that gradually changes its values over a period of time. &nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;  &nbsp;     ---From  [api.flutter.dev](https://api.flutter.dev/flutter/widgets/AnimatedContainer-class.html)

Let's look into its arguments:

%[https://gist.github.com/Monik09/201a4a54439c7780fb15635fe6aec2b5]

So we now are ready with our fundamentals strong. So lets' finally code.

### Let's code & implement the hovering effect
**Step 1:** Create a stateful class HoveringWidget. Why Stateful? Because we are going to use AnimatedContainer and it's always better to use Stateful class.
Create an InkWell widget as shown below.

```
class HoveringWidget extends StatefulWidget {
  _HoveringWidgetState createState() => _HoveringWidgetState();
}

class _HoveringWidgetState extends State<HoveringWidget> {
  @override
  Widget build(BuildContext context) {
    return InkWell(
        child:Text("Hover Button"),
        onTap:(){},
        onHover:(val){} 
         /*val--->true when user brings in mouse
         val---> false when brings out his mouse*/
    );
  }
}
``` 
onHover is this function that will be called when a user brings it to the mouse inside/outside. 
**Step 2:** Create a boolean variable isHover and set it to false.
```
bool isHover=false;
```
**Step 3:** Inside onHover function, use setState to change the value of isHover to val.
```
  setState((){
        isHover=val;
      });
```
**Step 4:** Now we are done with InkWell. So let's wrap this widget inside AnimatedContainer and add duration, padding to it. Carefully look at how I have given padding over here:

```
 Widget build(BuildContext context) {
    return AnimatedContainer(
      height:100,//there should be outline/dimensions for the box. 
      //Otherway, You can use positioned widget
      duration: Duration(milliseconds: 200),
      padding: EdgeInsets.only(top: (isHover) ? 25 : 30.0, bottom:!(isHover)? 25:30),
      child: InkWell( 
        onTap:(){},
        child: Text("Hover Button"),
        onHover: (val) {
          setState(() {
            isHover = val;
          });
        },
      ),
      /*val--->true when user brings in mouse
     val---> false when brings out his mouse*/
    );
  }
``` 
When the isHover will be true, it will decrease top padding and element will move upwards. With animations, it will look like hovering and will hence create our hovering effect.

It should be working now!
Now let's do some decoration over InkWell to look better.


```
Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: AnimatedContainer(
          height: 70,
          duration: Duration(milliseconds: 200),
          padding: EdgeInsets.only(
              top: (isHover) ? 25 : 30.0, bottom: !(isHover) ? 25 : 30),
          child: Container(
            height: 30,
            color: Colors.blue,
            child: InkWell(
              onTap: () {},
              child: Text("Hover Button"),
              onHover: (val) {
                print("Val--->{}$val");
                setState(() {
                  isHover = val;
                });
              },
            ),
            /*val--->true when user brings in mouse
           val---> false when brings out his mouse*/
          ),
        ),
      ),
    );
``` 


> Tip: You can add vertical padding to give a slanting hover animation effect.



## Kudos 🎉🎉
Hayyyy, you made it till the end. I hope you enjoyed working with animated Containers.

<iframe src="https://giphy.com/embed/ILV8xetoPJO92" width="480" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/thread-discussion-august-ILV8xetoPJO92">via GIPHY</a></p>

## Little Bit About Me🧑‍💻🧑‍💻🧑‍💻
Hey developers, I'm Monikinderjit Singh, working on Flutter for more than a year now. My interest in cloud technology is fueled by my need to learn more about it. I would appreciate you giving it a like if you find it interesting and leaving a comment if you have a better solution for this topic. It would be awesome if you could give me some feedback on improving my content.
You can connect with me on my [Twitter](https://twitter.com/intent/follow?screen_name=monikIJS), [Github](https://github.com/Monik09) and  [LinkedIn](https://www.linkedin.com/in/monikinderjit-singh/) .  












