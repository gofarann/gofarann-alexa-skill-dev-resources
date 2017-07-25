# helpful-alexa-skill-resources
A list of resources I found helpful to create an alexa skill from start to finish with the Alexa Skills Kit Node.js SDK.

## Tutorials & Sample Code
I looked over quite a few tutorials and found these three to be the most helpful to get started. I would do them in this order. 
* [Step-By-Step Environment Setup](https://github.com/alexa/skill-sample-nodejs-howto)
* [Hello World](https://github.com/alexa/skill-sample-nodejs-hello-world)
* [City Guide Tutorial](https://github.com/alexa/skill-sample-nodejs-city-guide/blob/master/README.md)

## Trouble-Shooting
* [CloudWatch Error Logs](https://console.aws.amazon.com/cloudwatch/home) - make sure it's in the same region as where Lambda code is hosted, which is probably US East (N. Virginia)
* [Alexa Card Responses](http://alexa.amazon.com/spa/index.html) 
* [Stack Overflow Alexa Skills Kit Tag](https://stackoverflow.com/questions/tagged/alexa-skills-kit) - good for beginner problems. 
* [Amazon Developer Forums](https://forums.developer.amazon.com/spaces/23/Alexa+Skills+Kit.html) - good for advanced problems and finding out if there are systematic issues happening across the Alexa platform. 


## Tips & Common Mistakes
### Beginner
  * Make sure your Echo is on your Amazon account. "Alexa, which account am I on?"
  * Run 'npm install' each time you want to add a new package; you then have to re-zip the files with your src file and reupload to Lambda. 
  * In order for your code to work, you must zip up your node modules as well as your src file in one folder and then upload to Lambda. 
  * Organize your code! 
    * You can either have different files and "require" them to create the relationships, or put them all in one index.js. 
    * There are four sections you must have, think through them like so:
      * States - What different states must my skill go through in order for Alexa to know how to make decisions about how to respond? 
      * Intents - What does the User want to do at each state?
      * Utterances (Interaction Model) - What must the user say in order to get the skill to execute correctly?
      * Intent Handler - What function do I want to call when my user signals an 'Intent'? 
  * Make sure the intent under each state 'calls' the intent handler function. You may need to pass the 'this' object as argument. 
 
### Intermediate
  * Some errors won't show up in error logs -- check your card response on the app, but note that only actual voice testing will result in a card error return. 
  * API responses are limited to 24576 bytes. To handle this error by checking the size of objects, install the [object-sizeof](https://www.npmjs.com/package/object-sizeof) package. 
  * If you have secret keys that need to be kept secret, install the [dotenv](https://www.npmjs.com/package/dotenv) npm package. You will need to manually submit them to Lambda on the same page you upload your zip file. 
  * If you are using an API, JSON response must be manipulated within the function of the call using the '.then' syntax. This is due to Javascript's asynchronous nature. Additionally, at this point, the JSON response object has become the 'this' of the function, so the object that the function is being called from, aka, the Alexa JSON request object, has to be reidentified as 'that'. 
  
