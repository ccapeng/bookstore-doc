# Migrate from REST to gRPC

\[Under construction\]

* Repositories
  * REST : [https://github.com/ccapeng/bookstore\_api](https://github.com/ccapeng/bookstore_openapi)
  * gRPC : [https://github.com/ccapeng/bookstore\_grpc](https://github.com/ccapeng/bookstore_grpc)
* Create protobuf
  * \[django-grpc-framework\] \([https://djangogrpcframework.readthedocs.io/en/latest/protos.html\#generate-proto-for-model](https://djangogrpcframework.readthedocs.io/en/latest/protos.html#generate-proto-for-model)\) document.
* Backend differences
  * REST :
    * djangorestframework

      * Implementation of  

      book.apis.py

      book.serializers.py

    * Middleware cors : bypass the cross site origin.
    * Handle snake-case and camel-case inconsistency.
  * grpc :
    * djangorestframework + djangogrpcframework + grpcio + grpcio-tools
    * Implementation of

      book.schema.py
* Frontend differences The difference is only the database query service.
  * REST : Use URL end point.  
    category.js

    ```javascript
      const CategoryService = {
          list: () => {
              let url = "api/category/";
              return Request.get(url);
          }
      }
    ```

    request.js

    ```javascript
      const Request = {

          get: async (url) => {

              try {
                  let result = await axios.get(
                      getFullURL(url),
                      getHeaderConfig()
                  );
                  return Promise.resolve(result.data);
              } catch (error) {
                  console.log(error);
                  return Promise.reject("get error");
              }

          }
      }
    ```

  * grpc : Always use `POST` method to submit `query`. category.js

    ```javascript
      const CategoryService = {

      }
    ```

    request.js

    \`\`\`javascript const Request = {

    ```text
      get: async (query) => {
    ```

```text
      }
  }
```
```

