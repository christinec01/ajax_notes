Partials:
Use them when you want to load a piece of html into another webpage. 
So, in Sinatra, anything that isn't a full html file, you name it with _filename.html.erb
in the controller:
```
get '/users/new/' do
  erb :'/users/_new.html', layout: false
end
```

This will render a form that exists in the _new.html.erb file without reloading the page or changing the url.

then we have a listener on the form that will take the data and make it an Ajax request, and send it back to the server. 
var headerListener = function( response ) {
console.log( response )


