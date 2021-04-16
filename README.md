# samplemed-package-structure-idea

### What files the package should have?

1. LICENCE
- The LICENCE file is specified to tell the rights the company has over the package.

2. MANIFEST.in
- Only python packages/folders (with __init__.py) will be recognized by the `setup.py`installation.
  Therefore, there are some folders and files that may need to come together in the app. Such as `statics/` or/and `templates/` for example or even some other files that are not recognized so the MANIFEST file will include these files too.
  As mentioned before, the MANIFEST.in file will make the opening of these folders and the inclusion of these files when the package be installed. 

- Example of a MANIFEST.in
  ```
  include LICENSE
  include README.rst
  recursive-include samplemed-app/static *
  recursive-include samplemed-app/templates *
  ```
3. README.rst
- The readme.rst has the same purpose of a readme.md file but with different markdown. [check its documentation](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#sections)

### How the app that will be within the package should structured?

- Important: The app may have the initial migrations folder to only need to migrate when installed again.

4. setup.py
- The setup.py will serve as the installation file in PYPI. A kind of Procfile. See how it should be and also can be used in other python packages:


### Installation:

1. Create a django app with its own url file. Following the app structure you can also see that it has its own url to easy the installation.
Since these apps will represent a software layer with many viewsets to be served by an url each. Then it wouldnt be a nice idea having to include ten or more urls commands by the orchestrator into the main url file in the project folder. Also, there are folders called `api/` that will separate the `serializers` and `viewsets` from the rest of the django app and the `tests/` folder to handle all the tests regarding that app.

 App structure example:
```
 Samplemed-django-app/
├── __init__.py
├── api/
│   ├── __init__.py
│   ├── serializers.py
│   └── viewsets.py
├── migrations/
│   ├── __init__.py
│   └── 0001_initial.py
├── tests/
│   ├── __init__.py
│   ├── test_models.py
│   ├── test_serializers.py
│   ├── test_urls.py
│   └── test_viewsets.py
├── admin.py
├── apps.py
├── models.py
├── urls.py
└── views.py
```

2. Now start the installation for the program adding the following command:
- ``` python setup.py sdist```
- This command will create the `dist/` folder to hold all different versions of the app.

3. Install the `twine` package that will be used to upload packages to pypi.
-```pip install twine```
  
4. Upload the package to pypi.
- ```twine upload dist/*```

Once you uploaded the package to pypi, this is how the package structure should look like:

```
django-samplemed-package/
├── LICENSE
├── MANIFEST.in
├── README.md
├── README.rst
|
├── dist/                  # <-------------
│   ├── django_samplemed_user_api-0.0.1.tar.gz
│   └── django_samplemed_user_api-0.0.2.tar.gz
|
├── Samplemed-django-app/
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-38.pyc
│   │   ├── admin.cpython-38.pyc
│   │   ├── apps.cpython-38.pyc
│   │   ├── models.cpython-38.pyc
│   │   └── urls.cpython-38.pyc
│   ├── admin.py
│   ├── api/
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   │   ├── __init__.cpython-38.pyc
│   │   │   ├── serializers.cpython-38.pyc
│   │   │   └── viewsets.cpython-38.pyc
│   │   ├── serializers.py
│   │   └── viewsets.py
│   ├── apps.py
│   ├── migrations/
│   │   ├── 0001_initial.py
│   │   ├── __init__.py
│   │   └── __pycache__
│   │       └── __init__.cpython-38.pyc
│   ├── models.py
│   ├── tests/
│   │   ├── __init__.py
│   │   ├── test_models.py
│   │   ├── test_serializers.py
│   │   ├── test_urls.py
│   │   └── test_viewsets.py
│   ├── urls.py
│   └── views.py
├── django_samplemed_user_api.egg-info
│   ├── PKG-INFO
│   ├── SOURCES.txt
│   ├── dependency_links.txt
│   └── top_level.txt
├── setup.py
└── workspace.code-workspace

