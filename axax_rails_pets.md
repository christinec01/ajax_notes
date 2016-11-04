In the erb file you'd like to "ajaxify" an element on:
Add a div to the overall group of things you'd like to target then if you use the rails method link_to you'l actually have access to an href (because it makes a link), so to target the specific thing you want to trigger an event for,  you can say,

.JS FILE
```
$('group-your-talking-to').on(click, 'specific-thing-you-want-to-trigger-the-request', function(event){
event.preventDefault()
$.ajax({
method: 'get',
url: $(this).attr('href'),
})
.then((response) => console.log(response.toys)) <======= this toys is coming from the controller, so basically when the request is sent, it goes to the 'get' of the url $(this).attr('href') which if you console.log($(this)) is a whole object that has a nested href tag of href: "http://localhost:3000/pets/5/toys" inside 
});
})
```

toy_controller FILE:

in order for our URL from above to return the toys associated with a specific pet, we need to set up our toy controller. 
From rails routes we can tell that the /pet/pet_id/toys route shoudl hit the index method in toys. We'll need to define 1) what a toy is and 2) we'll need to send it back as JSON and target only the element of the toy object we want to display.
```
class ToysController < ApplicationController
  def index
    @pet = Pet.find(params[:pet_id])
    render json:{toys:@pet.toys.map{|toy| toy.description}}
  end
```


CUSTOM ROUTES
in the config/routes.rb file, you can set a custom route to hit any controller/method,  for instance, the 
get '/home' route is being set to hit the pets controller, and the index method.
```
Rails.application.routes.draw do
  resources :pets do
    resources :toys do
    end
  end
  root 'pets#index'
  get '/home' => 'pets#index' 

  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```
