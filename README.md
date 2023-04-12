# History of Fetch API 

The Fetch API is a relatively new interface for fetching resources (including across the network) in web browsers. It was introduced in the year 2015, as a part of the ES6 (ECMAScript 2015) specification.


## Table of Contents
- [Introduction](#introduction)
- [History](#history)
- [Fetch API](#fetchapi)
- [References](#references) 

## Introduction
The Fetch API is a relatively new interface for fetching resources (including across the network) in web browsers. It was introduced in the year 2015, as a part of the ES6 (ECMAScript 2015) specification.


## History
Before the introduction of the Fetch API, XMLHttpRequest (XHR) was the most commonly used technique for making asynchronous network requests in JavaScript. However, XHR had some drawbacks, such as its inability to abort a request, lack of support for streaming, and the need to manually set up headers and parse response data. One of the main drawbacks of using XHR was the possibility of __callback hell__, which could make code difficult to read and maintain. These limitations led to the development of the Fetch API, which aimed to provide a more modern and intuitive interface for making network requests.

Here's an example of how to use XHR to make an asynchronous GET request to a server and receive a response:

```javascript
function fetchData() {
  const request = new XMLHttpRequest();  // creates a new instance of the XMLHttpRequest object using the new keyword
  request.open('GET', `https://restcountries.com/v2/name/usa`); //uses open() method to specify the HTTP method (GET) and the URL of the API endpoint to fetch    data from
  request.send();  // sends the request to the server

  request.addEventListener('load', function() { 
    const [data] =  JSON.parse(this.responseText) 
    console.log('🗣️',data.languages[0].name);  
  });
}
```
*This is a JavaScript function named fetchData() that uses XMLHttpRequest (XHR) to fetch data from a REST API endpoint.*
* *It first creates a new instance of the XMLHttpRequest object using the new keyword.*
* *It then uses the open() method to specify the HTTP method (GET) and the URL of the API endpoint to fetch data from. In this case, the URL is constructed dynamically using a string template literal with the value of the country variable interpolated into it.*
* *It then sends the request to the server using the send() method of the XHR object.*
* *It registers an event listener for the load event, which fires when the server responds with data. The event handler function extracts the response data from the responseText property of the XHR object using JSON.parse(), and then passes it to the renderCountry() function to display it on the page.*
*Overall, this function fetches data from a REST API endpoint using XHR, and then renders the response data on the page.*

## Fetch API
The Fetch API is based on promises, which makes it easier to write asynchronous code compared to callbacks. It also provides a streamlined interface for setting headers and handling responses. The API is designed to work with a wide range of data formats, including JSON, text, HTML, and binary data. Fetch API has a more consistent and intuitive error handling mechanism than XHR. In XHR, errors were handled in a non-standard way and required a lot of boilerplate code. Fetch API, on the other hand, uses the standard JavaScript error handling mechanism, making it easier to write error-handling code.

Here's the equivalent implementation of the fetchData() function using the Fetch API:

```javascript
const fetchData = () => {
  fetch('https://restcountries.com/v2/name/usa')
    .then(response => response.json()) // extract JSON data from response object
    .then(data => console.log('🗣️', data.languages[0].name))
    .catch(error => console.error(error)); // handle errors
};
```
*In this implementation:*
* *We use the fetch() function to make the HTTP request and fetch the data from the API endpoint.*
* *We then chain the .then() method to extract the JSON data from the response object using the json() method.*
* *We then chain another .then() method to process the extracted data and log the name of the first language to the console.*

*While we could certainly explore how async/await keywords can handle rejected and fulfilled promises from fetch() and response.json() separately, our focus here is on appreciating how much cleaner and more streamlined modern API fetching has become.*



Overall, the Fetch API has become a popular choice for making network requests in JavaScript, and it has been widely adopted by modern web browsers. Its ease of use, improved error handling, and support for modern web features have made it a preferred alternative to XHR for many web developers.


## References
- [Fetch API documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [XMLHttpRequest on MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
