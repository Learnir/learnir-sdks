
[<img src="https://learnir.co/logo.svg" width="50"/>](https://learnir.co/logo.svg)

## Hello you!
Welcome to the learnir-sdks repositories

Much of the sdk interacts with sdk api endpoints and in turn we relied on open-api-generator.tech to
automate building the sdk api bindings.
- Below we provide guides for all the environments we generate sdks for
- We currently support the browser based javascript, for any extra environments, do request for it using team@learnir.co
- Build command added, repo setup, package tested and deployed to packages manager distribution platform for that specific language.



## Install the Javascript SDK
```javascript
npm install learnir-javascript-sdk
```

## Get content & Add Consumer details
````javascript
const learnir = require("learnir-javascript-sdk");
const client = new learnir.LearnirApi({baseOptions:{headers:{"key":"port-access-key-from-console-dashboard"}}});

// Get content without tying it to a consumer
client.content().then(response => {
    console.log("response", response.data);
}).catch(error => {
    console.log("error", error);
})

// Get content and tye it to an added consumer 
client.content("consumer-id").then(response => {
    console.log("response", response.data);
}).catch(error => {
    console.log("error", error);
})

// (If you have users already): Call and add then with this method, best in batches
// (As a default): In auth flow, add this right in the browser in the signup process
client.consumer({ id: 'consumer-id', name: 'John Doe', email: 'consumer@email.com' }).then(response => {
    console.log("consumer-create", response.data);
}).catch(error => {
    console.log("consumer-create-error", error);
})


// (Recording consumer learning experience events) 
// Call this method on various official and custom events
// Official events are found in console.learnir.co/build
// Official events are highlighted in the reports feature.
//---------------------------------------------------------

// Attach to a consumer:
client.record({ consumer: "consumer-id", event: 'active', context: {} }).then(response => {
    console.log("create-consumer-event", response.data);
}).catch(error => {
    console.log("create-consumer-error", error);
})

// Unattached to a consumer (Not recommended)
client.record({ event: 'active', context: {} }).then(response => {
    console.log("create-consumer-event", response.data);
}).catch(error => {
    console.log("create-consumer-error", error);
})

// Consumers events - used for answering learning state questions
client.records("consumer-id").then(response => {
    console.log("consumer-events", response.data);
}).catch(error => {
    console.log("consumer-events", error);
})

// Official events - Highlighted in learnir console.
let official_events = [
    "box.visit", // pass box id
    "box.enrolled", // pass box id
    "section.visit", // pass box & section id
    "section.video.watch",  // pass box & section id
    "section.video.complete", // pass box & section id
    "section.complete",  // pass box & section id
    "box.complete" // pass box id
];

// Official events etc are already setup in templates
// If making use of custom development(e.g from scratch) - recording these events is required
// Other events if tyed to a consumed a consumer are welcome per your use case.
`````