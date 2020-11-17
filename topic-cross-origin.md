# How to handle cross origin?

## Why do we do that?
Browser will poke cross site server with `OPTIONS` method to determine the access right. 
* If browser don't see the right header, then it won't take the data.
* If server side don't handle `OPTIONS` method correctly, a server side  exception may be raised.


## REST
* Repository : [https://github.com/ccapeng/bookstore\_openapi](https://github.com/ccapeng/bookstore_openapi)
* To handle corss site origin `request` and `response`,  
  implement middleware `corsapp.middleware.CorsMiddleware`

  ```python
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

  And adjust settings in `bookstore_openapi.settings.py`

  ```python
    MIDDLEWARE = [
        ...
        'corsapp.middleware.CorsMiddleware',
    ]
  ```

* To bypass cross origin, 3 access control attributes were added to `response`.


## GraphQL
* Repository : [https://github.com/ccapeng/bookstore\_graphQL](https://github.com/ccapeng/bookstore_graphQL)
* To handle corss site origin `request` and `response`,  
  implement middleware `corsapp.middleware.CorsMiddleware`

  ```python
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

  And adjust settings in `bookstore_graphql.settings.py`

  ```python
    MIDDLEWARE = [
        ...
        'corsapp.middleware.CorsMiddleware',
    ]
  ```

* To bypass cross origin, 3 access control attributes were added to `response`.


## gRPC
* It's handled by proxy Envoy.
  File : [envoy-bookstore-grpc.yaml](https://github.com/ccapeng/bookstore_grpc/blob/main/envoy/envoy-bookstore-grpc.yaml)
  ```
  ...
  cors:
    allow_origin_string_match:
      - prefix: "*"
    allow_methods: GET, PUT, DELETE, POST, OPTIONS
    allow_headers: keep-alive,user-agent,cache-control,content-type,content-transfer-encoding,custom-header-1,x-accept-content-transfer-encoding,x-accept-response-streaming,x-user-agent,x-grpc-web,grpc-timeout
    max_age: "1728000"
    expose_headers: custom-header-1,grpc-status,grpc-message
  ...
  ```