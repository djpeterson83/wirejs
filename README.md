# wirejs
WireJS is a library for quickly and easily making JavaScript AJAX calls.  It has no dependencies on other libraries and works on good-old-fashion JavaScript.  Plus, it's small and portable!

# Usage
Wire is easy to use.  It uses RESTful method names to help you make access to online resources.  Then, use its promise-like result to add your own response handlers.  Here's a quick example:

    wire.get('some-text-file.txt').then(function(text) {
      alert(text); // Display the text!
    });
    
Wire can send `get`, `put`, `post`, `delete`, `patch`, and `head` requests natively. Of course, if wire only worked with text it would only be mildly useful.  Wire can also detect when a response is sending JSON and automatically convert the response to JSON for you:

    wire.get('api/some-resource').then(function(jsonObject) {
      console.log(jsonObject); // If the server returns 'application/json', you get a JSON object back!
    });
    
You can also configure wire.  The most common configuration change is to alter the sent MIME-type when making a `POST` or `PUT` request:

    wire.post('api/some-resource', jsonObjectToSend, wire.config().json()).then(function(){
      alert('JSON object serialized and sent to API!');
    });
    
Wire also lets you handle failures.  In fact, you can handle both success and failure operations at the same time, as well as chain multiple callbacks to success or failure.  Here's a simple example of handling both responses:

    wire.post('api/might-fail', someData)
      .then(function(responseObject, info){
        alert("Success! Status code: " + info.status);
      })
      .fail(function(data, info) {
        alert('Failed to send object! Status code: ' + info.status);
      });
      
The `info` parameter has the following properties:
      
      xhr:  The XMLHttpRequest object
      status:  The status code of the response
      responseText:  The raw response text.
      
We hope you like Wire!  It's ease, efficiency and portability is great for getting a project up and running quickly.  Give it a shot.  We know you'll love it!
