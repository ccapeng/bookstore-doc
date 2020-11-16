# Serializer Validation

* Implement `validate(self, data)` method

  File : `book/serializers.py`

  ```
  class AuthorSerializer(serializers.ModelSerializer):

      class Meta:
          model = Author
          fields = '__all__'

      def validate(self, data):
          """
          Check that start is before finish.
          """
          first_name = data["first_name"]
          last_name = data["last_name"]

          query = Author.objects.filter(
              first_name=first_name, last_name=last_name)
          authors = query.all()

          if len(authors) > 0:
              raise serializers.ValidationError("Author already exist")
          return data
  ```

* If invalid raise error; otherwise, return data.