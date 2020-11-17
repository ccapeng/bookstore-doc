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

* [https://swagger.io/tools/swagger-codegen/](https://swagger.io/tools/swagger-codegen/) : this is swagger code generator home page, not telling too much detail.
* Go to the download page [https://github.com/swagger-api/swagger-codegen](https://github.com/swagger-api/swagger-codegen)
* Since, I use windows. So just open PowerShell to download it : `Invoke-WebRequest -OutFile swagger-codegen-cli.jar https://repo1.maven.org/maven2/io/swagger/swagger-codegen-cli/2.4.15/swagger-codegen-cli-2.4.15.jar`
* To generate code, run `java -jar swagger-codegen-cli.jar generate -i http://127.0.0.1:8000/swagger.yaml -l go-server -o samples/bookstore/goserver`  

  Some other code options :
  * python-flask
  * go
  * go-server
  * java
  * java-play-framework
  * javascript
  * nodejs-server
  * spring
  * And a lot more.
  
* Actually, \[django REST framework support\] OpenAPI\([https://www.django-rest-framework.org/community/3.10-announcement/](https://www.django-rest-framework.org/community/3.10-announcement/)\); however, the way to download yaml file is odd. Need further investigate.

## Go Server

-Coming

