# jinja (Jinja Template and Flask)

## Statement
```
{%    %}
```

## Expression
```
{{    }}
```

## Comments
```
{#   #}
```

## jinja variable
```
FLASK
@app.route("/")
def home():
    return render_template("home.html", name='Sophia', email="sophia@gmail.com")

HTML
<h2>{{ name }}</h2>
<h2>{{ email }}</h2>
```

## jinja for loop
```
FLASK
@app.route("/")
def home():
    colors = ['red', 'green', 'blue', 'pink', 'yellow']
    return render_template("home.html", colors=colors)
    
HTML
<ul>
    {% for color in colors %}
        <li>{{ color }}</li>
    {% endfor %}
</ul>
```

## jinja if statement
```
FLASK
@app.route("/")
def home():
    return render_template("home.html", name="James")
    
HTML
{% if name == 'James' %}
    <h1>{{ name }}</h1>
{% endif %}
```

## jinja if else statement
```
FLASK
@app.route("/")
def home():
    return render_template("home.html", name="Jo")
    
HTML
{% if name == 'James' %}
    <h1>{{ name }}</h1>
{% else %}
    <h1>not James</h1>
{% endif %}
```

## jinja if else statement
```
FLASK
@app.route("/")
def home():
    return render_template("home.html", name="Jo")
    
HTML
{% if name == 'James' %}
    <h1>{{ name }}</h1>
{% else %}
    <h1>not James</h1>
{% endif %}
```

## base.html([Base Template](https://jinja.palletsprojects.com/en/3.0.x/templates/#template-inheritance))
```
<!DOCTYPE html>
<html lang="en">
<head>
    {% block head %}
    <link rel="stylesheet" href="style.css" />
    <title>{% block title %}{% endblock %} - My Webpage</title>
    {% endblock %}
</head>
<body>
    <div id="content">{% block content %}{% endblock %}</div>
    <div id="footer">
        {% block footer %}
        &copy; Copyright 2008 by <a href="http://domain.invalid/">you</a>.
        {% endblock %}
    </div>
</body>
</html>
```

## [Child Template, super(), self](https://jinja.palletsprojects.com/en/3.0.x/templates/#template-inheritance)
```
{% extends "base.html" %}
{% block title %}Index{% endblock %}
{% block head %}
    {{ super() }}
    <style type="text/css">
        .important { color: #336699; }
    </style>
{% endblock %}
{% block content %}
    <h1>{{self.title()}}</h1>
    <p class="important">
      Welcome to my awesome homepage.
    </p>
{% endblock %}
```
## [url_for](https://flask.palletsprojects.com/en/2.0.x/tutorial/templates/)
```
<a href="{{url_for('add')}}">Helo</a>
```
