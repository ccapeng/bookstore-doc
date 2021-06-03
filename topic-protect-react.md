# Server Side react javascript

* The source repository is [https://github.com/ccapeng/bookstore\_pro](https://github.com/ccapeng/bookstore_pro)
* Once you have react deployed to public web site, then you have exposed your code logic.
* So, put it to server side and only allow login user to accept.  
  In `frontend/templates/index.html`

  ```markup
        <div id="app"></div>
        <script src="/js/main.js"></script>
  ```

  and in `fontend/urls.py`, map `js` to `urlpatterns`.

  ```python
    urlpatterns = [
            path('', views.index),
            path('login/', views.login),
            path('logout/', views.logout),
            path('login_submit/', views.login_submit),
            path('js/<filename>', views.js)
    ]
  ```

  I have js output from django view.

* In `frontend/views.py`, the js file is only available after login. JS is a protected file, then just output file system.

  ```python
    @login_required(login_url='/login/')
    def js(request, filename):
            file_path = os.path.join(settings.BASE_DIR, "frontend", "js", filename)
            print("Load js", file_path)
            if os.path.exists(file_path):
                    with open(file_path, 'rb') as fh:
                            response = HttpResponse(fh.read(), content_type="application/javascript")
                            return response

            raise Http404
  ```

  Through this concept, server side react can be in any kind back end server.

* Also in the django restframework, all views are login required.  
  `LoginRequiredMixin` is always the first argument in the class.

  ```python
    class CategoryViewSet(LoginRequiredMixin, viewsets.ModelViewSet):
            """ Category ViewSet """
            login_url = '/login/'
            serializer_class = CategorySerializer
            queryset = Category.objects.all()
  ```

