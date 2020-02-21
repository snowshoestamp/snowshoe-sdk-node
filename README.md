# Overview
This is a sdk package that can be used in your Node.js code as a plugin to be able to transfer a properly encoded string that represents stamp points to SnowShoe servers and get a response with stamp information.

## Installing

You can install `snowshoe-stamp-sdk` via [the npm package](https://www.npmjs.com/package/snowshoe-stamp-sdk).

  `$ npm install snowshoe-stamp-sdk`

# Getting Started

1. To be able to use this SDK tool you need to create an app first. You can learn how to [HERE](https://snowshoe.readme.io/v3.0/docs/part-1-create-a-snowshoe-application)

2. Make sure you get the API Key that you will need to run requests. You can learn more about the API Keys [HERE](https://snowshoe.readme.io/v3.0/docs/part-1-create-a-snowshoe-application#get-api-keys)

3. The stamp data passed to our servers is an array of x,y coordinates. These represent the touch points from the stamp that you are trying to get data for. If you are using our front-end jquery plugin (more info on this located [HERE](https://snowshoe.readme.io/v3.0/docs/maintained-libraries)) to capture stamp touch point data, then you can just pass that data directly through for the request with no need to change.

# Test App

Make a new javascript file named test.js to use. You will need to `'require'` the `snowshoe-stamp-sdk` in the app. We will also use some mock data the represent the points here for testing and you will need your API Key also for testing. Here is a sample piece of code to use for testing. Copy and add this to the test.js file.

```javascript
var Snowshoe = require('snowshoe-stamp-sdk');

var client = new Snowshoe.client('YOUR_API_KEY');
    var data = "[[264,172],[267,371],[242,286],[69,375],[66,221]]";

client.post(data, function(error, data) {
    if (error) {
        console.log(error);
    }
    else {
        console.log(data);
    }
});
```

After you save the file go to console and navigate to the folder the file is in. Run the file with:

`node test.js`

This should print out a status code of 200 and a JSON showing a "serial" of "DEVA". The whole JSON should look something like this:

```
{
  stamp: { serial: 'DEVA', customName: 'DEVA' },
  receipt: '0d8e3aa3-4a34-407c-95a7-db62acab2269',
  created: '2020-02-17T22:15:03.7571485Z'
}
```

The information returned here is the data about the stamp relating to the points and api key you sent in the request. For more info on stamp data requests and returns go [HERE](https://snowshoe.readme.io/v3.0/docs/part-3-api-request)

# More info

- This sdk extension is made for simplistic retrieval of stamp data from our servers through the node.js language when your server uses this as it's primary code.
- For more info on how to use our product visit: 
    https://snowshoe.readme.io/v3.0/docs
