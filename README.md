# django-designpattern-notes
Django design patterns note

# Models
### abstract models : using abstract classes as  `base models` for other models that have similar fields. example:
```
class BaseModel(modesl.Model):
  created_datetime = models.CharField(max_length=255)
  
  class Meta:
    abstract_class =True
    
    
class Post(BaseModel):
  title = models.CharField(max_length=255)
  description = models.Text()
  
class Comment(BaseModel):
  name = models.CharField(max_length=255)
  opinion = models.CharField(max_length=450)
  
```
---

### multi models.py files: use seperate modules of `models.py`:  
```
app1
 --models/
   -- __init__.py
   -- post.py
   -- category.py
```
###### __init__.py :
```
from post.py import Post
from category import Category

```
