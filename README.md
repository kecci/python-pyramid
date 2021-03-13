# python-pyramid

## Install Env And Pyramid

create virtual env
```
virtualenv venv
```

activate env
```
source venv/bin/activate
```

install pyramid
```
(venv) $ pip install pyramid
```

create project
```
(venv) $ mkdir quick_tutorial/hello_world
```

## Setup Project
create `quick_tutorial/hello_world/app.py`
```py
from waitress import serve
from pyramid.config import Configurator
from pyramid.response import Response


def hello_world(request):
    print('Incoming request')
    return Response('<body><h1>Hello World!</h1></body>')


if __name__ == '__main__':
    with Configurator() as config:
        config.add_route('hello', '/')
        config.add_view(hello_world, route_name='hello')
        app = config.make_wsgi_app()
    serve(app, host='0.0.0.0', port=6543)
```

## Run application
Run the application:
```
(venv) $ python quick_tutorial/hello_world/app.py
```

Open http://localhost:6543/ in your browser.