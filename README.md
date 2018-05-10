# Django practice nº 4

### Setup Instruction

```bash
$ mkvirtualenv -p $(which python3) django_practice_4
$ pip install -r requirements.txt
$ make migrate
```

You can now run the development server and point the browser to the correct URL:

```bash
$ make runserver
```


### Your Tasks

The goal for this practice is to keep working with forms, but in this case we'll make usage of the tools provided by Django instead of writing them by hand in HTML. As always, the structure of the Django project is built for you and you'll have your work divided in a couple of tasks.

If you run the development server with `$ make runserver`, you'll be able to test the project in the browser pointing to the URL that Cloud9 provides to you.


#### Part 1 - Working with Basic Django Forms

We'll keep using the `Artist` and `Song` models from previous practices, and our template with the list of Artists and forms for creating proper objects.
For this part, you'll have to reply the "Add a new Artist" form like in the last practice but in this case, you must use a [Django basic Form](https://docs.djangoproject.com/en/2.0/topics/forms/).

There's a `forms.py` module inside `artists` app where the Form needs to be implemented. The rest of the logic must be done inside `artists` view in `artists/views.py` and in the `index.html` template.

You will have to handle both `GET` and `POST` requests in the same `artists` view, analysing what value comes in `request.method`.
- If 'request.method == GET', you just have to make an instance of the form and return it as context to the template for later rendering, along with the list of all artists stored in the database
- If 'request.method == POST', you make an instance of the form with the data that comes in request.POST, and then, if the form is valid, create the proper Artist object with the provided values.


#### Part 2 - Working with Django ModelForms

In this case the idea is to reply the form in charge of adding a new Song, but this time using a [Django ModelForm](https://docs.djangoproject.com/en/2.0/topics/forms/modelforms/).

The model form must be also implemented in `artists/forms.py` and the logic that handles the song creation will be once again inside `artists` view.

The view will keep working in the same way as before for either GET or POST requests, but now it have to handle two forms at the same time. One of the differences between the Model Form used in this part is that you don't need to create the Song object by hand. You can just `.save()` your form once you're sure that it is valid, and it will create the object in the database for you.