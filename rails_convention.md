Controller's role- <strong>handling requests in Rails, hands off 'heavy code' to the Model.</strong>

Controller to View relationship:

From controller, there are three ways to create HTTP requests:
<br>
  -call render to create a full response to send back to the browser
  <br>
  -Call redirect_to to send an HTTP redirect status code to the browser
  <br>
 <strong> -Call head to create a response consisting solely of HTTP headers to send back to the browser</strong>
 <br>
 - If you dont explicitly render somthing, the controllr will look for a view named whatever method its in, so the index methoed will look for an index.html.erb file.
 -
