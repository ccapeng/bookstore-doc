# Use Open API data model

## Use Open API data model

## Prepare the REST API to Open API \(swagger\).

* To be simple comparison, I migrated [bookstore\_api](https://github.com/ccapeng/bookstore_api) project to [bookstore\_openapi](https://github.com/ccapeng/bookstore_openapi).
* What's in the bookstore\_openapi project?
  * Install [drf-yasg](https://github.com/axnsan12/drf-yasg) : `pip install -U drf-yasg`
* The lastest `djangorestframework` is 3.12, which is not compatible with `drf-yasg`.

  Make sure you have `pip install djangorestframework==3.11.1`

* Also check drf-yasg document [https://github.com/axnsan12/drf-yasg](https://github.com/axnsan12/drf-yasg) for how to set up `settings.py` and `urls.py`
* Then copy the whole book models, serializers, api.
* Start server. In browser, open `http://127.0.0.1:8000/swagger.yaml`.

## Code Generator

* [https://openapi-generator.tech/](https://openapi-generator.tech/) : this is openapi code generator home page,   
  you may got lost in here.
* [jar file repository page](https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/),  
  to download the latest one.  
  Or in windows, open PowerShell to download it :  
  
  `Invoke-WebRequest -OutFile swagger-codegen-cli.jar https://repo1.maven.org/maven2/io/swagger/swagger-codegen-cli/2.4.15/swagger-codegen-cli-2.4.15.jar`
  
* To use cli
  * Generate Flask code
      ```
      d:\dvp\swagger>java -jar openapi-generator-cli.jar generate ^
        -i bookstore.yaml ^
        -g python-flask ^
        -o samples/bookstore/flask
      ```
  * Generate nodejs code : use the swagger-codegen-cli.jar.
      ```
      d:\dvp\swagger>java -jar swagger-codegen-cli.jar generate ^
        -i bookstore.yaml ^
        -l nodejs-server ^
        -o samples/bookstore/nodejs
      ```
  
  * Generate go code  
      ```
      d:\dvp\swagger>java -jar openapi-generator-cli.jar generate ^
        -i bookstore.yaml ^
        -g go-gin-server ^
        -o samples/bookstore/gin
      ```
  
      ```
      d:\dvp\swagger>java -jar openapi-generator-cli.jar generate ^
        -i bookstore.yaml ^
        -g go-server ^
        -o samples/bookstore/go
      ```
      
  * [More generators](https://openapi-generator.tech/docs/generators)
  
* Actually, \[django REST framework support\] OpenAPI\([https://www.django-rest-framework.org/community/3.10-announcement/](https://www.django-rest-framework.org/community/3.10-announcement/)\); however, the way to download yaml file is odd. Need further investigate.

