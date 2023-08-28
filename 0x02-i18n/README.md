# 0x02. i18n

## Description
This project focuses on internationalization (i18n) and localization in Flask applications. It covers the setup and usage of Flask-Babel for translating and localizing content in web applications. The project aims to teach parametrizing Flask templates for different languages, inferring the correct locale based on URL parameters or user settings, localizing timestamps, and more.

## Table of Contents
- [Description](#description)
- [Resources](#resources)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [Tasks](#tasks)
  - [Task 0: Basic Flask app](#task-0-basic-flask-app)
  - [Task 1: Basic Babel setup](#task-1-basic-babel-setup)
  - [Task 2: Get locale from request](#task-2-get-locale-from-request)
  - [Task 3: Parametrize templates](#task-3-parametrize-templates)
  - [Task 4: Force locale with URL parameter](#task-4-force-locale-with-url-parameter)
  - [Task 5: Mock logging in](#task-5-mock-logging-in)
  - [Task 6: Use user locale](#task-6-use-user-locale)
  - [Task 7: Infer appropriate time zone](#task-7-infer-appropriate-time-zone)
  - [Task 8: Display the current time (Advanced)](#task-8-display-the-current-time-advanced)

## Resources
- [Flask-Babel](https://flask-babel.tkte.ch/)
- [Flask i18n tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xiii-i18n-and-l10n)
- [pytz](https://pypi.org/project/pytz/)

## Learning Objectives
Upon completing this project, participants will be able to:

- Parametrize Flask templates to display content in different languages.
- Infer the correct locale based on URL parameters, user settings, or request headers.
- Localize timestamps to display them in the user's preferred format.
- Utilize Flask-Babel extension for internationalization and localization.
- Create user login systems to emulate user preferences.
- Integrate user preferences such as preferred locale and time zone into web applications.

## Requirements
- Ubuntu 18.04 LTS
- Python 3.7
- Flask-Babel 2.0.0
- pytz
- pycodestyle 2.5

## Tasks
### Task 0: Basic Flask app
- Set up a basic Flask app with a single route.
- Create an HTML template for the route to display "Welcome to Holberton" as the page title and "Hello world" as the header.

### Task 1: Basic Babel setup
- Install Flask-Babel extension.
- Configure available languages and default locale using a Config class.
- Instantiate the Babel object in the app.

### Task 2: Get locale from request
- Create a function to determine the best matching locale from request headers.
- Use the `babel.localeselector` decorator.

### Task 3: Parametrize templates
- Parametrize templates using `_` or `gettext` function for translation.
- Initialize translations using `pybabel extract` and `pybabel init` commands.

### Task 4: Force locale with URL parameter
- Implement a way to force a specific locale using the `locale` parameter in URLs.
- Update the `get_locale` function to support this feature.

### Task 5: Mock logging in
- Create a mock user table to simulate user login.
- Define a function to get user details based on the `login_as` parameter in URLs.
- Use `app.before_request` decorator to set the user as a global variable.

### Task 6: Use user locale
- Modify the `get_locale` function to use the user's preferred locale if available.
- Set the order of priority for determining the locale.

### Task 7: Infer appropriate time zone
- Create a function to infer the appropriate time zone based on URL parameters, user settings, or request headers.
- Validate the time zone using `pytz.timezone`.

### Task 8: Display the current time (Advanced)
- Display the current time in the user's inferred time zone.
- Translate and localize the displayed time based on the user's preferred locale.

