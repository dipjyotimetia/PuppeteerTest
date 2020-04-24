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
### Github actions
```yml
name: PuppeteerCI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    container: dipjyotimetia/puppeteertest

    strategy:
      matrix:
        node-version: [12.x]

    steps:
      - uses: actions/checkout@v1
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}
      - name: npm install and test
        run: |
          npm install
          npm run test:ci
        env:
          CI: true

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
    "jest": "^25.4.0",
    "puppeteer": "^3.0.1"
  },
```
