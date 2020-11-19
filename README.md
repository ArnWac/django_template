<!-- ABOUT THE PROJECT -->
## About The Project

Whenever I start a new project, I have to set up all the settings again. In order to reduce my work I have created a starter template based on my previous experience on which all my Django projects are based.
Beside a good project structure it offers the possibility to insert different settings and Bootstrap is already integrated.

<!-- GETTING STARTED -->
## Getting Started

1. Clone the repo
```sh
git clone https://github.com/ArnWac/django_template <your_project>
```
2. Create your virtual environment
```sh
python3 -m venv /path/to/new/virtual/environment
```
3. Install requirements from `requirements.txt`
```JS
pip install -r requirements.txt
```

<!-- Changes -->
## Changes

1. Changed `settings.py` to directory `settings`

    `__init__.py` makes it a Python module allowing the import of `base.py`, `production.py` and `local.py` importing settings 
for different environments like development and production.

    ```
    from .base import *
    from .production import *
    
    try:
        from .local import *
    except:
        pass 
    ```

    All you need to do is add `local.py` file in the settings directory for your local settings e.g.
`DEBUG = True`

2. Correcting `BASE_DIR` path

    By moving the settings file, the `ROOT_DIR` changed. Fixing this with:
`BASE_DIR = os.path.dirname(os.path.dirname(os.path.dirname(os.path.abspath(__file__))))`

2. Instead of hardcoding the secret key in your settings module, consider loading it from a file:

    ```
    with open(os.path.join(BASE_DIR, 'core', 'secret_key.txt')) as f:
        SECRET_KEY = f.read().strip()
    ```

    or environment variable:

    ```
    import os
    SECRET_KEY = os.environ['SECRET_KEY']
    ```

    you should do the same with your database credentials, before you go in production.

3. Adding `PROJECT_APPS` to settings for a better overview of your own apps

4. Moved all apps into subfolder apps for a better project structur, create new app like:
    ```
    cd apps
    mkdir <your_app>
    python manage.py startapp <your_app> apps/<your_app>
    ```

4. Adding `CustomerUser` Model

5. Adding Bootstrap with `base.html` template

5. Adding a list of directories for static assets not tied to a particular app
    ```
    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, 'static'),
    ]
    ```

<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/ArnWac/django_template/issues) for a list of proposed features (and known issues).

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- CONTACT -->
## Contact

Arne Wacker - arnewacker@outlook.com

GitHub Link: [https://github.com/ArnWac](https://github.com/ArnWac)

Project Link: [https://github.com/ArnWac/django_template](https://github.com/ArnWac/django_template)