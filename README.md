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
app1/
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

---
# Views  
### implement crud by generic views:
```
class ImpDateDetail(generic.DetailView):
    model = models.ImportantDate

class ImpDateCreate(generic.CreateView):
    model = models.ImportantDate
    form_class = ImportantDateForm

class ImpDateUpdate(generic.UpdateView):
    model = models.ImportantDate
    form_class = ImportantDateForm

class ImpDateDelete(generic.DeleteView):
    model = models.ImportantDate
    success_url = reverse_lazy("formschapter:impdate_list")
```
