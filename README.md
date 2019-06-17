# Puppeteer Test Docker Image
Puppeteer test docker image   

<img src="https://user-images.githubusercontent.com/10379601/29446482-04f7036a-841f-11e7-9872-91d1fc2ea683.png" width="150">  

[Nodejs > 12.0](https://nodejs.org/en/)  
[Puppeteer](https://github.com/GoogleChrome/puppeteer)

### Jenkins file uses
```groovy  
agent {  
  docker {      
      image 'puppeteer:latest'      
      args '--privileged'  
   }  
 }  
```   
### Puppetter launch config
```javascript   
const browser = await puppeteer.launch(
      {
          headless: true,
          args: [
            `--no-sandbox`,
            '--start-maximized',
            '--disable-setuid-sandbox',
            `--disable-infobars`,
            `--disable-dev-shm-usage`,
          ],
          ignoreHTTPSErrors: true,
          dumpio: false,
       }
   );
```
```json
"dependencies": {
    "jest": "^24.8.0",
    "puppeteer": "^1.17.0"
  },
```
