# Overview
This is a sdk package that can be used in your Node.js code as a plugin to be able to transfer a properly encoded string that represents stamp points to SnowShoe servers and get a response with stamp information.

## Installing

You can install `snowshoe-stamp-sdk` via [the npm package](https://www.npmjs.com/package/snowshoe-stamp-sdk).

  `$ npm install snowshoe-stamp-sdk`

# Getting Started

1. To get the app running, you will need to create an app on our site. Go to https://app.snowshoestamp.com/ and Sign In if you have an account or sign up if you don't have one. Once you are logged in, click “New App” to create a new one.

2. After you have created the new application look at it's settings and you will find 'API Key 1' and 'API Key 2'. These can both be used to pass through as the needed param `api_key` to get stamp data back from our servers.

3. The stamp data passed to our servers is encoded in Base64 and then sent through as form-data. If you use our snowshoe jquery plugin to capture stamp touch point data ( located here: https://cdn.snowshoestamp.com/snowshoe-jquery/0.3.3/jquery.snowshoe.js ) then you don't have to worry about this because the data passed through will already be encoded. In this example we will use mock data of points in Base64 (`W1swLDBdLFszNiwzNl0sWzM2LDBdLFsyMCw0XSxbOCwzNl1d`) to get a stamp return when we send the request.

# Test App

Make a new javascript file named test.js to use. You will need to `'require'` the `snowshoe-stamp-sdk` in the app. We will also use the mock data here for testing and you will need your API Key also for testing. Here is a sample piece of code to use for testing. Copy and add this to the test.js file.

```javascript
var Snowshoe = require('snowshoe-stamp-sdk');

var client = new Snowshoe.client('YOUR_API_KEY');
    var data = "W1swLDBdLFszNiwzNl0sWzM2LDBdLFsyMCw0XSxbOCwzNl1d";

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

The information returned here is the data about the stamp relating to the points and api key you sent in the request.

# More info

- This sdk extension is made for simplistic retrieval of stamp data from our servers through the node.js language when your server uses this as it's primary code.
- For more info on how to use our product visit: 
    https://snowshoe.readme.io/v3.0/docs
