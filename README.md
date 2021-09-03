# jinja (Jinja Template, Bootstrap and Flask)

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

## [connect with Bootstrap](https://getbootstrap.com/)
### base.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    {% block head %}
    <title>{% block title %}{% endblock %}</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-KyZXEAg3QhqLMpG8r+8fhAXLRk2vvoC2f3B09zVXn8CA5QIVfZOJ3BCsw2P0p/We" crossorigin="anonymous">
    {% endblock %}
</head>
<body>
{% block content %}
    <h1>helo</h1>
{% endblock %}
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.3/dist/umd/popper.min.js" integrity="sha384-eMNCOe7tC1doHpGoWe/6oMVemdAVTMs2xqW4mwXrXsW0L84Iytr2wi5v2QjrP/xp" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.0/dist/js/bootstrap.min.js" integrity="sha384-cn7l7gDp0eyniUwwAZgrzD06kc/tftFf19TOAs2zVinnD/C7E91j9yyk5//jjpt/" crossorigin="anonymous"></script>
</body>
</html>
```

### child.html
```
{% extends "base.html" %}

{% block title %}
    My Website
{% endblock %}

{% block content %}
<div class="alert alert-primary" role="alert">
  A simple primary alert—check it out!
</div>
<div class="alert alert-secondary" role="alert">
  A simple secondary alert—check it out!
</div>
{{ super() }}
{% endblock %}
```
-------------------------------
