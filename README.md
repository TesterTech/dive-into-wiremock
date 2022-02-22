# dive-into-wiremock
Code for the YouTube videos:
- Part 1: https://youtu.be/0fyGWhGN6y8 
- Part 2: https://www.youtube.com/watch?v=hUv2rpqd3KU

## Getting started with WireMock
The easiest way is to run the JAR from command-line. To do that look at the WireMock docs under standalone (http://wiremock.org/docs/running-standalone/) and download the JAR file. Now from terminal (command-line) run the JAR file using the ```java -jar``` argument, for example ```java -jar wiremock-jre8-standalone-2.31.0.jar```.

You should see an ascii logo of WireMock and an indication of the port it's running at. 

Now you can interact with it using curl of a rest-client. The rest-client I'm using in the video is Insomnia REST client but you can use any other client. 

## Docker
```docker pull wiremock/wiremock```
```docker run -it --rm -p 8080:8080 wiremock/wiremock```
Note: depending on your setup, you might want to call wiremock with sudo (like also in the video). 


## Add new mappings

You can post to ```<url>/__admin/mappings/new```
for example
```
{
    "request": {
        "method": "GET",
        "url": "/api/mytest"
    },
    "response": {
        "status": 200,
        "body": "More content\n"
    }
}
```
You can also put the above snippet in the mappings dir.


## Files as JSON body
- Create a mapping and assign ```bodyFileName``` the value of the location of a JSON file. 
```
{
    "request": {
        "method": "GET",
        "url": "/body-file"
    },
    "response": {
        "status": 200,
        "bodyFileName": "example.json"
    }
}
```

## Running Wiremock and recoding 
In part 2 video I show an example of the recorder where I show behavior that is not expected https://youtu.be/hUv2rpqd3KU?t=461 ... Later I saw that using the command as shown below indeed works as expected. 
```
java -jar wiremock-jre8-standalone-2.31.0.jar --port 8080 \
  --proxy-all="http://example.mocklab.io" \
  --record-mappings \ 
  --verbose 
```
So use above command if you want to have rec and play. 

## Demo app 
- The demo app is based on the tutorial 
- https://github.com/miguelgrinberg/microblog/


## References
- WireMock http://wiremock.org
- Insomnia Rest client https://insomnia.rest 
- WireMock on Docker Hub https://hub.docker.com/r/wiremock/wiremock
- WireMock rec & play at the same time https://stackoverflow.com/questions/40743569/can-wiremock-play-and-record-be-used-at-the-same-time
-


