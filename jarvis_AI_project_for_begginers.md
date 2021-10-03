---
title: "Jarvis Virtual Assistant Project for Beginners"
author: "Devanapally Charan Tej"
github: "charan-143"
date: "2021-10-03"
canonicalUrl: "https://charantej.hashnode.dev/jarvis-virtual-assistant-project-for-beginners"
---

![Jarvis Virtual Assistant Project for Beginners](https://charantej.hashnode.dev/_next/image?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1631028966878%2FFDhIjj2eK.jpeg%3Fw%3D1600%26h%3D840%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp&w=1920&q=75)





Everyone wants their work to be done by a person. Nowadays, on every smartphone, there is a virtual assistant which is helping everyone in their day-to-day tasks. But for our PC there is no such assistant. so now, we going to make our personal assistant for our pc/laptop by python.


# Prerequisites

- Basic Knowledge of python
- Text editor 


### ** Basic Libraries**

- datetime
- pyttsx3
- speechRecognition

### ** Basic Tasks**

- Our AI assistant basic task is to listen and speak out.
- Wishing the user.
- Perform the tasks given

### **Code for Installing Packages**

```
pip install Package Name
``` 

# Code Time!
In this article, we will write the basic code of Jarvis.

- First and foremost we should import the libraries on which we are working.

#### **Import**


```
import pyttsx3
import speech_recognition as sr
import datetime
``` 

Now, let us go with writing the code of functions.

### speak()

The first thing of a virtual assistant is to speak. To make our Jarvis speak we are gonna write a function named ***speak()***. For Jarvis to speak we need to provide some input. So, our function is going to take the ```audio```  argument as a parameter.


```
def speak(audio):
    pass     # for now we will pass the function and write the body later.
``` 

Now, we will arrange the code for the ```audio``` parameter.

#### code for the audio parameter:


```
import pyttsx3
engine = pyttsx3.init('sapi5')
voices= engine.getProperty('voices') 
engine.setProperty('voice', voice[0].id)

``` 

### Explanation of the above code

- ***In, the first line we imported the library pyttsx3.***

**What is pyttsx3 ?**


```pyttsx3 ``` is a text-to-speech conversion library in Python. Unlike alternative libraries, it works offline and is compatible with both Python 2 and 3.

- ***In, the second line we initialized the library pyttsx3 with sapi5 API.***

**What is spai5? **

"sapi5" is a Microsoft-developed speech API that helps in the synthesis and recognition of voice.

- ***In, the third line we get all voices in our machine (Laptop/PC).***
- ***In, the fourth line we assign a certain voice to ur assistant.***

**What Is VoiceId?**

In, the machine we may have several voices. To, assign a certain voice we use the voice id command which helps us to select different voices.

- voice[0].id = voice one
- voice[1].id = voice two etc..

Now, it's done with the parameter ```audio```. We will write the body of the ***speak()***.


```
def speak(audio):
engine.say(audio) 
engine.runAndWait() #Without this command, speech will not be audible to us.
``` 

### wishme() 

In the movie, Jarvis used to wish Tony stark. Now, our Jarvis has to wish, to do so we are going to a function called ***wishme()***.


```
import datetime
def wishme():
    hour= int(datetime.datetime.now().hour)
    minute=int(datetime.datetime.now().minute)
    if hour>=0 and hour<=11:
        speak('good morning')
        speak('the time is '+str(hour)+":"+str(minute)+ " AM")
    elif hour>=12 and hour<=18:
        if hour>12:
            hour = hour-12
        elif hour==12:
            hour = hour
        speak('good afternoon')
        speak('the time is '+str(hour)+":"+str(minute)+ " PM")
    else:
        if hour>12:
            hour = hour-12
        speak('good evening')
        speak('the time is '+str(hour)+":"+str(minute)+ " PM")
    speak('Iam Jarvis. what can i do for you sir.')

``` 

So this is a simple function. ```hour``` , ```minute``` means current time in your area. If it is greater than or equal to 00:00 and lesser than 12:00, Jarvis says "Good Morning!"

If the time is between 12:00 and 18:00, it's "Good Afternoon!".
Else, it means between 18:00 and 00:00, it is "Good Evening!".
Each time when Jarvis wishes it will tell the current time of your area.


### takecommand()

The next most important thing for our Jarvis is that it should take command with the help of the microphone of the user's system. So, now we will write a takeCommand() function. With the help of the takeCommand() function, our Jarvis will return a string output by taking microphone input from the user. Cool right? 

```
def takeCommand():
    #It takes microphone input from the user and returns string output

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")    
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")

    except Exception as e:
        # print(e)    
        print("Say that again please...")  
        return "None"
    return query.lower()
``` 

Yay! You've successfully created ```takeCommand()```. Well done buddy!

### Time to run!

We have completed the functions now we need to run them.
write the following code for execution of the above functions.
### ```main()``` Function

```
if __name__ == "__main__":
    wishme()
    takeCommand()
``` 


> This is the end of this article. In the next article, we will add features to our Jarvis. Like opening Youtube, sending emails, playing music, etc...