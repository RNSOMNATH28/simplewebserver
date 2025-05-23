# EX01 Developing a Simple Webserver
## Date: 03-04-2025
## Name: R N Somnath
## register no.: 212224240158
## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:
### views.py
```
from django.shortcuts import render
def sun(request):
    return render(request,'exp1.html')
```
### settings.py
```
"""
Django settings for employeeapp project.

Generated by 'django-admin startproject' using Django 5.1.7.

For more information on this file, see
https://docs.djangoproject.com/en/5.1/topics/settings/

For the full list of settings and their values, see
https://docs.djangoproject.com/en/5.1/ref/settings/
"""

from pathlib import Path
import os

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent


# Quick-start development settings - unsuitable for production
# See https://docs.djangoproject.com/en/5.1/howto/deployment/checklist/

# SECURITY WARNING: keep the secret key used in production secret!
SECRET_KEY = 'django-insecure-8&_7qezsf0_qhwv(r!s%ky$qvtrp-)0#2y1k0nnprz)x_+%^2%'

# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = True

ALLOWED_HOSTS = []


# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'emp',
]

MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'employeeapp.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR,'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'employeeapp.wsgi.application'


# Database
# https://docs.djangoproject.com/en/5.1/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'somnath',
        'USER':'root',
        'PASSWORD':'root',
        'HOST':'localhost',
        'PORT':3306,
    }
}


# Password validation
# https://docs.djangoproject.com/en/5.1/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]


# Internationalization
# https://docs.djangoproject.com/en/5.1/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True


# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/5.1/howto/static-files/

STATIC_URL = 'static/'

# Default primary key field type
# https://docs.djangoproject.com/en/5.1/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```
### urls.py
```
from django.contrib import admin
from django.urls import path
from emp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('emp/',views.sun),
]
```
### exp1.html
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Laptop Specifications</title>
  <style>
    /* Reset default styles */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    /* Body styling */
    body {
      font-family: 'Arial', sans-serif;
      background: linear-gradient(to right, #7f7880, #3a9dcb);
      color: #9c2323;
      padding: 20px;
      text-align: center;
    }

    /* Container styling */
    .specifications-container {
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      background-color: rgba(103, 35, 35, 0.452);
      border-radius: 12px;
      box-shadow: 0 8px 16px rgba(94, 86, 86, 0.2);
    }

    .specifications-container h1 {
      font-size: 28px;
      color: #090909;
      margin-bottom: 20px;
    }
    .spec-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    .spec-table thead {
      background: linear-gradient(to right, #ff6f61, #f06292);
      color: white;
    }

    .spec-table th, .spec-table td {
      padding: 14px;
      text-align: left;
      border: 1px solid #ddd;
    }

    .spec-table th {
      font-size: 18px;
      font-weight: bold;
    }
    .spec-table tbody tr:nth-child(1) td {
      background-color: #578257; 
    }
    .spec-table tbody tr:nth-child(2) td {
      background-color: #1c4e65; 
    }
    .spec-table tbody tr:nth-child(3) td {
      background-color: #1f6077; 
    }
    .spec-table tbody tr:nth-child(4) td {
      background-color: #f8bbd0; /* Light pink */
    }
    .spec-table tbody tr:nth-child(5) td {
      background-color: #592ab0; /* Light purple */
    }
    .spec-table tbody tr:nth-child(6) td {
      background-color: #d5840c; /* Peach */
    }
    .spec-table tbody tr:nth-child(7) td {
      background-color: #e2e7e6; /* Mint green */
    }
    .spec-table td {
      font-size: 16px;
      color: #333;
    }
    .spec-table tbody tr:hover td {
      background-color: #f1f8e9; /* Light lime */
      transition: background-color 0.3s ease;
    }
  </style>
</head>
<body>
  <div class="specifications-container">
    <h1>Laptop Specifications</h1>
    <table class="spec-table">
      <thead>
        <tr>
          <th>Specification</th>
          <th>Details</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Processor</td>
          <td>13th Gen Intel(R) Core(TM) i5-1335U 1.30 GHz</td>
        </tr>
        <tr>
          <td>RAM</td>
          <td>16.0 GB (15.7 GB usable)</td>
        </tr>
        <tr>
          <td>Storage</td>
          <td>350GB SSD</td>
        </tr>
        <tr>
          <td>Display</td>
          <td>15.6-inch Full HD</td>
        </tr>
        <tr>
          <td>Graphics</td>
          <td>NVIDIA GeForce GTX 1650</td>
        </tr>
        <tr>
          <td>Battery Life</td>
          <td>Up to 10 hours</td>
        </tr>
        <tr>
          <td>Operating System</td>
          <td>Windows 11 Home</td>
        </tr>
      </tbody>
    </table>
  </div>
</body>
</html>
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/82a9512d-3e36-4294-939b-86bd47d001f2)
## RESULT:
The program for implementing simple webserver is executed successfully.
