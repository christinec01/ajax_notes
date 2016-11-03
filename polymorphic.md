Polymorphic Associations:
One model can belong to more than one other model through one association.

```
class Picture < ApplicationRecord
  belongs_to :imageable, polymorphic: true
end
```
```
class Employee < ApplicationRecord
  has_many :pictures, as: :imageable
end
```
```
class Product < ApplicationRecord
  has_many :pictures, as: :imageable
end
```
