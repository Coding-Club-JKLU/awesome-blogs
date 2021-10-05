---
title: "Add Features to your Jarvis"
author: "Devanapally Charan Tej"
github: "charan-143"
date: "2021-10-03"
canonicalUrl: "https://charantej.hashnode.dev/jarvis-virtual-assistant-project-for-beginners"
---

![Add Features to your Jarvis](https://charantej.hashnode.dev/_next/image?url=https%3A%2F%2Fcdn.hashnode.com%2Fres%2Fhashnode%2Fimage%2Fupload%2Fv1632231560269%2FoDH-6T6ie.jpeg%3Fw%3D1600%26h%3D840%26fit%3Dcrop%26crop%3Dentropy%26auto%3Dcompress%2Cformat%26format%3Dwebp&w=1920&q=75)



In the previous blog, we made our Jarvis speak, listen and take command. Now In is a blog, we will make our Jarvis perform some tasks by taking commands from the user.
### Libraries Needed
- wikipedia
- webbrowser
- os
- pywhatkit


``` The webbrowser module is an inbuilt one. you no need to install it.```
# Let's Add Features.

We are going to code in the ```main()``` from now.
### ```main``` Function
```
if __name__ == "__main__":
    wishMe()
    while True:
    # The code for the Features will be added here.
```
### Get summary from Wikipedia
You want a summary on a particular topic from Wikipedia. Let Jarvis do it.
Add the following code in the ```main()```.


you need a module called wikipedia for the above code to execute.
copy the code below to Install Wikipedia


#### Install Wikipedia:

```
pip install wikipedia
```
#### Code:
```
import wikipedia
if 'wikipedia' in query:  #if wikipedia found in the query then this block will be executed
    speak('Searching Wikipedia...')
    query = query.replace("wikipedia", "")
    results = wikipedia.summary(query, sentences=2) 
    speak("According to Wikipedia")
    print(results)
    speak(results)

``` 
### Open Youtube

You want to open youtube on your laptop. Let Jarvis do it for you.
Add the following code in the ```main()```.
#### Code:
```
import webbrowser
elif "open youtube" in query:
    webbrowser.open("www.youtube.com")
#  you need the "os" module to execute this command.
#  It is inbuilt library in python
``` 
### Open any website
Want to open any website. Just Tell the name of the website to Jarvis. It will be done for you.write the following code for the task to be completed by Jarvis.
#### Code:
```
elif "open {website name}" in query:
    webbrowser.open("www.{websitename}.com")
# In place of website name you write name of that particular website you want to open.
``` 
### Open "CMD"
If you code regularly then you must know "Command line" in windows. which is known as "CMD" in shortcut. If you want your Jarvis to open "CMD" for you then 
write the following code:
#### Code:
```
import os
elif "open cmd" in query:
    os.system("start cmd")
#  you need "os" module to execute this command.
#  It is inbuilt library in python
```
### Play video on youtube
By all the coding stuff you do in a day. You may get tired and wanna watch some videos on youtube. Let Jarvis play it for you.
we need a module pywhatkit for this code to execute.
#### Install:
```
pip install pywhatkit

``` 
write the following code:
#### Code:
```
import pywhatkit
elif "play on youtube" in query:
    query.replace("play on youtube","")
    kit.playonyt(query,open_video=True)

```
### Open NotePad
Want to open a notepad for writing notes. let Jarvis do it for you by giving command "open notepad" . write the following code.

```
elif "open notepad" in query:
    os.system("notepad")
``` 
### Open an application on your PC
Want to open an application on your PC. Then write the following code and jarvis to open that particular application.


```
elif "open {application name}" in query:
#example :
#path ="C:\\Program Files\\Microsoft VS Code\\Code.exe"
    path ="provide the path of the application\\application_name.exe"
    os.startfile(path)
``` 
make sure you have double "\\" for no errors.


# Complete Code Upto now:

```
import pyttsx3
import speech_recognition as sr
import datetime
import wikipedia
import webbrowser
import os
import pywhatkit

engine = pyttsx3.init('sapi5')
voices= engine.getProperty('voices') 
engine.setProperty('voice', voice[0].id)

def speak(audio):
engine.say(audio) 
engine.runAndWait() #Without this command, speech will not be audible to us.

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

if __name__ == "__main__":
    wishMe()
    while True:
    # The code for the Features will be added here.
        if 'wikipedia' in query:  #if wikipedia found in the query then this block will be 
        executed
            speak('Searching Wikipedia...')
            query = query.replace("wikipedia", "")
            results = wikipedia.summary(query, sentences=2) 
            speak("According to Wikipedia")
            print(results)
            speak(results)
        elif "open youtube" in query:
            webbrowser.open("www.youtube.com")
            #  you need the "os" module to execute this command.
            #  It is inbuilt library in python
        elif "open {website name}" in query:
            webbrowser.open("www.{websitename}.com")
            # In place of website name you write name of that particular website you 
            want to open.
        elif "open cmd" in query:
            os.system("start cmd")
            #  you need "os" module to execute this command.
            #  It is inbuilt library in python
         elif "play on youtube" in query:
             query.replace("play on youtube","")
             kit.playonyt(query,open_video=True)
         elif "open notepad" in query:
             os.system("notepad")
         elif "open {application name}" in query:
             #example :
             #path ="C:\\Program Files\\Microsoft VS Code\\Code.exe"
             path ="provide the path of the application\\application_name.exe"
             os.startfile(path)
``` 


> Times up for this blog we will learn more libraries and functions. And add more features to our Jarvis. Follow to add more features.


