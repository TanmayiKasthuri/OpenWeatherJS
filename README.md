# OpenWeatherJS
APPLICATION PROGRAMMING INTERFACES. 
Metaphorically APIs are waiters, you are customers, other service providers like openweatherapp are chefs where you order the food through a waiter and the waiters gets you your order from the chef. Similarly we request info for our app from other service providers through the help of API.

PROMISES IN JAVASCRIPT

To avoid nested callback i.e;multiple function calls with one another, we use promises for asynchronous functions in order to avoid callback hell and make the code more maintainable and readable.
Example of nested callback
asyncFunction1((result1) => {
  asyncFunction2(result1, (result2) => {
    asyncFunction3(result2, (result3) => {
      // More nested callbacks...
    });
  });
});

Promises have 3 states namely pending, fulfilled and rejected. And to execute promises we have 2 main keywords then and catch. The execution pointer is transferred to then if the promise returned is fulfilled and if it is rejected, the execution pointer is transferred to catch where the errors are caught.

Fetch is another important keyword that represents a promise. Fetch is usually used to fetch data from a url. If the data can be fetched, then the promise value would be fulfilled else it is rejected. The intermediate state would be pending.
Ex-let promise= fetch(url)
promise.then(gotData)
promise.catch(gotError)
These 3 lines can also be consolidated into a single line as fetch(Url).then(gotData).catch(gotError) where gotData and gotError in this like act as callbacks to those articular functions
This can also be written as 
fetch(Url)
.then(function(data)=>{
console.log(data);/*block inside gotData function is directly written within then by removing function name*/
})
.catch(function(error)=>{
console.log(error);
})
This can further be written as
fetch(Url)

.then((data)=>{
console.log(data);
})
.catch((error)=>{
console.log(error);
})/* as (=>) distinctively represents function itself in javascript, you don’t need to mention the keyword function again*/
You can also take away the curly braces if it’s just 1 line of data by writing it further in the below way
fetch(Url).then(data=>console.log(data)).catch(error=>console.log(error))
Another problem here is for data retrieved from fetch to be in readable form,(since given that we are fetching data from an API), we need to convert it to json format for it to be readable
i.e;FINAL REPRESENTATION gives
fetch(Url)
.then(response=>response.json()/*converting response to json*/)
.then(console.log(response)/*printing data that has been converted to json format*/)
.catch(error=>console.log(error))

YOU MAY ALSO CREATE YOUR OWN PROMISES, FOR THAT WATCH THE YOUTUBE VIDEO.

Aysnc and Await keywords.
These are introduced in the ES8 version and this specify that
If a function returns a promise, then it can use await keywords that stops other executions until the promise is resolved and provides a state.
In order to use await keyword you need to specify that the function in which await keyword is used as asynchronous function
These keywords help us avoid multiple thens.
This so works that, you can put all the promises in the function that is termed async and while calling the function you can mention then and catch.
Ex; function named wordGIF() is termed async and has promises. Now while calling that function,
wordGIF().then(/*contains returned onus from the function*/).catch(error=>console.log(error))

Asynchronous functions are commonly used when dealing with tasks that may take some time to complete, such as fetching data from a server, reading files, or making network requests. By making these functions asynchronous, you can execute other code while waiting for the asynchronous task to finish, improving the responsiveness and efficiency of your program.
