Kendo-Email Finder API NodeJS Wrapper
---
[![Build Status](https://travis-ci.org/NeverBounce/NeverBounceApi-NodeJS.svg?branch=master)](https://travis-ci.org/NeverBounce/NeverBounceApi-NodeJS)

This is the official Kendo API NodeJS/Typescript wrapper. It provides helpful methods to quickly implement our API in your NodeJS applications.

Usage
===

To start using the wrapper sign up for an account [here](https://kendoemailapp.com/) and get your api keys [here](https://kendoemailapp.com/accountetl). This wrapper utilizes ES6/Typescript Promises to handle the API calls.

To initialize the wrapper use the following snippet, substituting in your `api key` and `api secrete key`...

You can now access the find and verify method from this object. To validate a single email use the following...

```
Kef.verify(EMAIL_TO_VALIDATE).then(
    function(result) {
        // do stuff
    },
    function(error) {
        // errors will bubble up through the reject method of the promise.
        // you'll want to console.log them otherwise it'll fail silently
    }
);
```

The `result` returned in from the verification promise will be a `Result` object. It provides several helper methods documented below...

```
result.getResult(); // Numeric result code; ex: 0, 1, 2, 3, 4
result.getResultTextCode(); // Textual result code; ex: valid, invalid, disposable, catchall, unknown
result.is(0); // Returns true if result is valid
result.is([0,3,4]); // Returns true if result is valid, catchall, or unknown
result.not(1); // Returns true if result is not invalid
result.not([1,2]); // Returns true if result is not invalid or disposable
```

To set a client side timeout use the `timeout` config option.

```
var Kef = require('KendoEmailfind')({
    apiKey: API_KEY,
    timeout: 30000 // timeout in milliseconds
});
```
