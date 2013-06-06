#coathanger

Current Version: 0.0.0

A JSON API Client framework for Python

Core Idea: handle all the connection and auth boilerplate so you don't have to.

##Planned Features
* Configurable Auth
* Model/Resource driven routing (can be overridden)
* Rate Limiting

##What I'm thinking it might end up looking like

__Your API Project:__
```
api_client/
    __init__.py
    resources/
        SomeResource.py
```

__\_\_init\_\_.py__
```python
from coathanger import Coathanger
from resources import SomeResource

my_app = Coathanger(endpoint='http://api.myendpoint.whereveritis.com/', resources=my_resources)
```

__SomeResource.py__
```python
from coathanger import Resource

class SomeResource(Resource):
    # What you expect to be returned
    def __init__(self, name, company):
        self.name = name
        self.company = company
```

__Client's code:__
```python
import my_app

my_app.auth.api_key = 'hey_look_a_test_api_key'

what_i_want = my_app.SomeResource.get(5)
# GET 'http://api.myendpoint.whereveritis.com/someresources/5'

print(what_i_want.name)
# 'the name of that thing you wanted'

print(what_i_want.company)
# 'the company that makes that thing'
```
