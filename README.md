# golang_chat_example

This is an example of a realtime chat application using Go and websockets.

# Configuration Files

The *Godeps* folder contains dependency management files for deploying to Heroku.

*Procfile* is a configuration file for deploying to Herkou.

If you deploy to Google App Engine you'll have to add an *app.yaml* file and delete the aforementioned config files.

The *.project* file enables you to open this project in Eclipse ( make sure you have the Goclipse plugin ). Otherwise, it's yet another config file. You can delete it if you'd like.

# Run Locally - Terminal

0) Have Go installed: https://golang.org

1) Set the GOPATH environment variable to the root directory of this project. Of course if you have other GOPATH routes just add

```
;C:\Users\YourName\Desktop\golang_chat_example
```

to the end of the value. Of course this is if you clone this repository to your Desktop :)

2) Open git bash terminal and change directory to be root of the project

```
cd Desktop/golang_chat_example
```

3) In the same terminal enter the command:

```
go run src/server/server.go
```

The application should be running and listening to port 8081

If you are deploying the application, change the websocket address/port in the *html/client.html* file.

# Deploy - Heroku

0) Have a heroku account (don't worry, it's free for your first few applications): https://heroku.com/

1) If this is your firt time using Heroku, get the toolbelt: https://toolbelt.heroku.com/ and after installation, open the git bash terminal and enter the following commands:

```
heroku login
```

Enter your information and continue to the next step.

2) Enter the following commands while in the root directory of the project:

```
git init
git add -A .
git commit -m "initial commit"
heroku create -b https://github.com/kr/heroku-buildpack-go.git
```

After the last line completes, an application name should be provided. It may look like something funky.. As you can see from the *html/client.html* file, the pubAddr variable is set to application_name.herokuapp.com where application_name was tranquil-gorge-4724 in my case.

3) Take the application name given to you and change the pubAddr variable in *html/client.html* and comment out and replace the addr variable.

```javascript
// var addr = "localhost:8081"
var pubAddr = "application_name.herokuapp.com"

var conn = new Websocket("wss://" +  pubAddr + "/ws");
```

4) In the *html/client.html* file there is a section of code that's commented out.. Go ahead and uncomment that.

5) Finally deploy!! In the git bash terminal enter the following commands:

```
git add -A .
git commit -m "changed websocket address"
git push heroku master
```

To open, just go to the URL provided -or- enter the command:
```
heroku open
```

Enjoy!