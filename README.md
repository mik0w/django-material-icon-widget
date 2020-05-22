# Icon Picker Widget   for admin panel

# How to start:
Download the module 

Include it in the settings (Installed apps):
```
INSTALLED_APPS = [
    ...
    'django.contrib.staticfiles',
    'icon_picker_widget', #<---- 
    ...
```
Add static path files of widget:

```
STATICFILES_DIRS = [
    ('icon_picker_widget',os.path.join(BASE_DIR, 'icon_picker_widget/static'))
]
```
# Insalattion is done

Example of Usage:

model.py:
```
from django.db import models

class BlogPost(models.Model):
    name = models.TextField()
    icon = models.TextField()
```

admin.py
```
from django import forms
from django.contrib import admin
from icon_picker_widget.widgets import IconPickerWidget
from .models import BlogPost

class BlogPostAdminForm(forms.ModelForm):
    def __init__(self, *args, **kwargs):
        super(BlogPostAdminForm, self).__init__(*args, **kwargs)
        self.fields['icon'].widget = IconPickerWidget()

class BlogPostAdmin(admin.ModelAdmin):
    form = BlogPostAdminForm

admin.site.register(BlogPost, BlogPostAdmin)
```




