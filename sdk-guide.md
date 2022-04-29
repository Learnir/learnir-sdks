## Introductiton
- We generate our sdk via open-api-generator.tech
- We simply have a yaml of the endpoints of our API's, we run 


## Generating an sdk
- Verify the sdk-spec.yaml and then run the following command to generate the sdk


## Foundations
- We label our sdks learnir-language , learnir-javascript, learnir-nodejs, learnir-java,  learnir-golang etc


## Building
- Generation at best should be automated always.

### Javascript
- openapi-generator-cli generate -g typescript-axios -i ./sdk-spec.yaml -o builds/sdks/learnir-javascript-sdk -p npmName=learnir-javascript-sdk,supportsES6=true,modelPropertyNaming=original


### Nodejs
- openapi-generator-cli generate -g typescript-node  -i ./sdk.yaml -o sdks/learnir-nodejs -p npmName=learnir-nodejs,supportsES6=true,modelPropertyNaming=original


## Testing
npm install .\sdks\learnir-javascript


## Resources
https://phrase.com/blog/posts/using-openapi-to-generate-api-client-code/
https://openapi.tools/