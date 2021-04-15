# samplemed-package-structure-idea

### What files the package should have?

1. LICENCE
  1.1 The LICENCE file is specified to tell the rights the company has over the package.

2. MANIFEST.in
  2.1 Only python packages/folders (with __init__.py) will be recognized by the `setup.py`installation.
  Therefore, there are some folders and files that may need to come together in the app. Such as `statics/` or/and `templates/` for example or even some other files that are not recognized so the MANIFEST file will include these files too.
  As mentioned before, the MANIFEST.in file will make the opening of these folders and the inclusion of these files when the package be installed. 

  2.2 Example of the MANIFEST.in
      """
      include LICENSE
      include README.rst
      recursive-include samplemed-app/static *
      recursive-include samplemed-app/templates *
      """

3. README.rst

### How the app that will be within the package should structured?

- Important: The app has to have the initial migrations folder to only need to migrate.

"""
├── __init__.py
├── api
│   ├── __init__.py
│   ├── serializers.py
│   └── viewsets.py
├── migrations
│   ├── __init__.py
│   └── 0001_initial.py
├── tests
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
"""



"""
.
├── LICENSE
├── MANIFEST.in
├── README.md
├── README.rst
├── Users
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-38.pyc
│   │   ├── admin.cpython-38.pyc
│   │   ├── apps.cpython-38.pyc
│   │   ├── models.cpython-38.pyc
│   │   └── urls.cpython-38.pyc
│   ├── admin.py
│   ├── api
│   │   ├── __init__.py
│   │   ├── __pycache__
│   │   │   ├── __init__.cpython-38.pyc
│   │   │   ├── serializers.cpython-38.pyc
│   │   │   └── viewsets.cpython-38.pyc
│   │   ├── serializers.py
│   │   └── viewsets.py
│   ├── apps.py
│   ├── migrations
│   │   ├── 0001_initial.py
│   │   ├── __init__.py
│   │   └── __pycache__
│   │       └── __init__.cpython-38.pyc
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── dist
│   ├── django_samplemed_user_api-0.0.1.tar.gz
│   └── django_samplemed_user_api-0.0.2.tar.gz
├── django_samplemed_user_api.egg-info
│   ├── PKG-INFO
│   ├── SOURCES.txt
│   ├── dependency_links.txt
│   └── top_level.txt
├── setup.py
└── workspace.code-workspace
"""
