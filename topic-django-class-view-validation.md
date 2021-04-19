# Django Class View Validation

* In the class view, implement `form_valid(self, form)` method

  File : `book/views.py`
  ``` Python
  class AuthorCreate(CreateView):
      ...

      def form_valid(self, form):
          data = self.request.POST
          first_name = data.get('first_name')
          last_name = data.get('last_name')
          query = Author.objects.filter(
              first_name=first_name, last_name=last_name)
          authors = query.all()
          if len(authors) > 0:
              form.errors['input invalid'] = 'Author is already exist.'
              return self.form_invalid(form)
          return super(AuthorCreate, self).form_valid(form)
  ```
  
* If invalid, set 
  `form.errors[]`  
  and  
  `return self.form_invalid(form)`
  
* The tricky part is how to show in the template.

  File : `book/templates/book.author_form.html`
  ```
  {% load dict_key %}
  ...
  <form method="post">{% csrf_token %}

    {% if form.errors %}
    <div class="mt-3 mb-3">
      {%for k in form.errors %}
      <div class="text-danger">
        {{ form.errors|dict_key:k }}
      </div>
      {% endfor %}
    </div>
    {% endif %}
    ...
  </form>
  ```
  The validation messages are generic and allow to take more than one.  
  In order to display them, customized filter `dict_key` is applied.
  
* dict_key was learned from [stackoverflow](https://stackoverflow.com/questions/19745091/accessing-dictionary-by-key-in-django-template).

  File : `book/templatetags/dict_key.py`
  ``` python
  from django import template
  from django.template.defaultfilters import register


  register = template.Library()


  @register.filter(name='dict_key')
  def dict_key(d, k):
      '''Returns the given key from a dictionary.'''
      return d[k]
  ```
  