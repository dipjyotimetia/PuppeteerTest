# Puppeteer Test Docker Image  
[Nodejs > 12.0](https://nodejs.org/en/)  
[Puppeteer](https://github.com/GoogleChrome/puppeteer)

### Jenkins file uses:
```groovy  
agent {  
  docker {      
      image 'dipjyotimetia/puppeteertest'      
      args '--privileged'  
   }  
 }  
```   
### Puppetter launch config:
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
### package.json  
```json
"dependencies": {
    "jest": "^24.8.0",
    "puppeteer": "^1.17.0"
  },
```
