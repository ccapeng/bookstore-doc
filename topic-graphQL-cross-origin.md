# GraphQL Cross Origin

- Repository : [https://github.com/ccapeng/bookstore_graphQL](https://github.com/ccapeng/bookstore_graphQL)

- Implement middleware `corsapp.middle.py` to handle it.  

	``` python
	from django.http import HttpResponse


	class CorsMiddleware(object):

			def __init__(self, get_response):
					self.get_response = get_response

			def __call__(self, request):
					is_graphQL = True if request.path == "/graphql/" else False
					is_method_options = True if request.method == "OPTIONS" else False
					if is_graphQL and is_method_options:
							response = HttpResponse("")
							response["Access-Control-Allow-Origin"] = "*"
							response["Access-Control-Allow-Headers"] = "*"
							response["Access-Control-Allow-Methods"] = "*"
							return response

					response = self.get_response(request)
					if is_graphQL:
							response["Access-Control-Allow-Origin"] = "*"
							response["Access-Control-Allow-Headers"] = "*"
							response["Access-Control-Allow-Methods"] = "*"

					return response
	```  
	
	- To bypass cross origin, 3 access control attributes were added to response.
	
	- Furthermore, browser will poke cross site server with `OPTIONS` method.  
		So for the `graphQL` url, we need to return `response` in here; otherwise exception will throw out when passing into graphQL process.

	