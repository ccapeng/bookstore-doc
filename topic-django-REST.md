# Django REST framework

- The source repository is [https://github.com/ccapeng/bookstore_api](https://github.com/ccapeng/bookstore_api)

- Installation  
	```pip install djangorestframework```

- In the regular django, you need to implement view in order to output data.  
	with REST framework, only need to implement serializer 
	`book.serializers.py`
	in order to save data.  
	And, register url in 
	```book.urls.py```  
	When server startup, then you can view api in  
	http://127.0.0.1:8000/



- Snake-case to camel-case
	Python is a language like all against c syntax, no curly brace block match and use snake-case for the variables.  
	In general, we also use camel-case in javascript, json.  
	The following implementation totally take the extra translation.
	
	Add
	```
	utils.api.parsers.py
	utils.api.renders.py
	```
	This parser was copied from [https://gist.github.com/vbabiy/5842073](https://gist.github.com/vbabiy/5842073).
	
	So in the settings.py, also update:
	``` python
	REST_FRAMEWORK = {

			'DEFAULT_RENDERER_CLASSES': (
					'utils.api.renderers.CamelCaseJSONRenderer',
					'rest_framework.renderers.BrowsableAPIRenderer',
			),

			'DEFAULT_PARSER_CLASSES': (
					'utils.api.parsers.CamelCaseJSONRenderer',
					'rest_framework.parsers.FormParser',
					'rest_framework.parsers.MultiPartParser'
			),
	}
	```

- To bypass cross Origin, you need to add the following middleware implementation into order to have browser accept the cross site permission.
	Middleware implement at bookstore_api.corsapp.middleware.py

	``` python
	class CorsMiddleware(object):

			def __init__(self, get_response):
					self.get_response = get_response

			def __call__(self, request):
					response = self.get_response(request)
					response["Access-Control-Allow-Origin"] = "*"
					response["Access-Control-Allow-Headers"] = "*"
					response["Access-Control-Allow-Methods"] = "*"

					return response
	```