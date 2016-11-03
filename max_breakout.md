Difference between AJAX request and http request:
  -Ajax:
  -HTTP: request goes out and the browser will wait for the server to respond back with information, 
    then the whole page will re-load.
  
 -Partial: you can reload just one small part of the page using Ajax
 
 - Ajax:
  when you send an Ajax call to the controller, you can set up your controller to do .to_json
 then
 
 in controller:
 ```
 get /users/ do
 @users_json = User.all.to_json
 end
 ```
 in model
 ```
 def self.get_users_json
  User.all
  return self.all.to_json
 end
 ``` 

 in your .js file:
 ```
 $.ajax({
 method: "get"
 url link.attr('href')
 })
 .done( function (resoponse) {
 console.log(response);
 console.log($.parseJSON(resonse));
  ```
  
 Alternatively, if you do this in the controller:
 
  ```
 get /users/ do
 @users_json = User.all.to_json
 end
 ```
 You can take out the $.parsJSON line in your .js file:
  ```
 $.ajax({
 method: "get"
 url link.attr('href')
 })
 .done( function (resoponse) {
 console.log(response);
  ```
