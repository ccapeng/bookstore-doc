# Use Open API data model

# Prepare the REST API to Open API (swagger).

- To be simple comparison, I migrated [bookstore_api](https://github.com/ccapeng/bookstore_api) project to [bookstore_openapi](https://github.com/ccapeng/bookstore_openapi).

- What's in the bookstore_openapi project?
	
	- Install [drf-yasg](https://github.com/axnsan12/drf-yasg) : `pip install -U drf-yasg`

- The lastest `djangorestframework` is 3.12, which is not compatible with `drf-yasg`.

	Make sure you have `pip install djangorestframework==3.11.1`
	
- Also check drf-yasg document [https://github.com/axnsan12/drf-yasg](https://github.com/axnsan12/drf-yasg)
	for how to set up `settings.py` and `urls.py`

- Then copy the whole book models, serializers, api.

- Start server. In browser, open `http://127.0.0.1:8000/swagger.yaml`.
	
# Code generator

- [https://swagger.io/tools/swagger-codegen/](https://swagger.io/tools/swagger-codegen/) : this is swagger code generator home page, 
	not telling too much detail.
	
- Go to the download page [https://github.com/swagger-api/swagger-codegen](https://github.com/swagger-api/swagger-codegen)

- Since, I use windows. So just open PowerShell to download it :
	`Invoke-WebRequest -OutFile swagger-codegen-cli.jar https://repo1.maven.org/maven2/io/swagger/swagger-codegen-cli/2.4.15/swagger-codegen-cli-2.4.15.jar`
	
- To generate code, run
	`java -jar swagger-codegen-cli.jar generate -i http://127.0.0.1:8000/swagger.yaml -l go-server -o samples/bookstore/goserver`
	
	What kind code you can be generated in the `-l` option?
	```
	ada-server
	akka-scala
	android
	apache2
	apex
	aspnetcore
	bash
	csharp
	clojure
	cwiki
	cpprest
	csharp-dotnet2
	dart
	dart-jaguar
	elixir
	elm
	eiffel
	erlang-client
	erlang-server
	finch
	flash
	python-flask
	go
	go-server
	groovy
	haskell-http-client
	haskell
	jmeter
	jaxrs-cxf-client
	jaxrs-cxf
	java
	inflector
	jaxrs-cxf-cdi
	jaxrs-spec
	jaxrs
	msf4j
	java-pkmst
	java-play-framework
	jaxrs-resteasy-eap
	jaxrs-resteasy
	javascript
	javascript-closure-angular
	java-vertx
	kotlin
	lua
	lumen
	nancyfx
	nodejs-server
	objc
	perl
	php
	powershell
	pistache-server
	python
	qt5cpp
	r
	rails5
	restbed
	ruby
	rust
	rust-server
	scala
	scala-gatling
	scala-lagom-server
	scalatra
	scalaz
	php-silex
	sinatra
	slim
	spring
	dynamic-html
	html2
	html
	swagger
	swagger-yaml
	swift5
	swift4
	swift3
	swift
	tizen
	typescript-aurelia
	typescript-angular
	typescript-inversify
	typescript-angularjs
	typescript-fetch
	typescript-jquery
	typescript-node
	ue4cpp
	undertow
	ze-ph
	kotlin-server
	```
	
	