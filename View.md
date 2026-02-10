A python function/class that receives a web request and returns a web response, such as an HTML page, a redirect or an error.

View Contains core logic for processing data and generating the content a user sees in their browser.

View acts as the bridge between data(models) and the user interface in `Model-View-Template` architecture.

It explains - "When someone hits this URL, what code should run?"


## Types of Views

### Function-Based Views (FBVs)

```python

from rest_framework.decorators import api_view
from rest_framework.response import Response

@api_view(["GET"])
def hello(request)
	return Response({"msg" : "Hello"})
```

### Class-Based View

