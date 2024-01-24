# Word Counter

## About This Project

This is a project I have created while I was following a course called ***Django 2 & Python | The Ultimate Web Development Bootcamp***, created by ***Nick Walter***.

It’s a website that counts the number of words in a text and how many times each word is mentioned.

## Pages
* **Home** - a simple page where you write your text
<img src="https://i.imgur.com/8NfvkQK.png" width="500px">

* **Count** - a page that displays the number of words in your text and how many times each word is mentioned  
<img src="https://i.imgur.com/nL6sBJS.png" width="500px">

* **About** - a page that tells you some information about this project
<img src="https://i.imgur.com/dbIMMho.png" width="500px">

## Things I've Learned
### URLS
File **`urls.py`** contains a list called *urlpatterns*. URL patterns are used to map URLs to views. 

The list consists of three paths that are needed for this website: ***home***, ***count*** and ***about***.  

```python
urlpatterns = [
    path('', views.home, name='home'),
    path('count/', views.count, name='count'),
    path('about/', views.about, name='about')
]
```

Each of these paths consists of three parameters: 
1. ***route*** - a route that is added on top of a local IP address `http://127.0.0.1:8000/`. A full URL leads us to a specific view. 
2. ***view***  - a function that takes a web request and returns a web response
3. ***name*** - a nickname for a previously mentioned view

### Views

File **`views.py`** contains all the functions that are responsible for returning a web response.

For example, the following function will return a template called **`about.html`** .

```python
def about(request):
    return render(request, 'about.html')
```

Also, in render function we can pass some variables to a template, like we did in a view for Count page.
```python
return render(request, 'count.html', {'fulltext': fulltext, 'count': len(wordlist), 'word_dictionary': sorted_words})
```
The parameters are passed in a dictionary that contains pairs of keys and their coresponding values.

### Templates

A template is a text document or a Python string marked-up using the Django template language. It is written in a `.html` files.

We can show a passed parameter with `{{ fulltext }}`.

Here's an example of a for loop:
```python
{% for word, totalcount in word_dictionary %}
    {{ word }} - {{ totalcount }}
{% endfor %}
```

Also, this is how you pass a view name:
```python
<a href="{% url 'about' %}">About</a>
```