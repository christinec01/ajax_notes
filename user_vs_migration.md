if you want your user to see one field 'full name'
but your model has a first name and a last name, you can write a method in the user class to handle that...

class User < ApplicationRecord
```
def fullname=(name)
split = name.split(' ' , 2)
self.first_name = split.first
self.last_name = split.last
end
```
```
def full_name
[first_name, last_name].join(' ')
end

end
```
