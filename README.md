# Proyecto django-admin-soft-dashboard 1.0.12

Proyecto de prueba con el template moderno de Django admin interface 

["Django Admin Soft"](https://pypi.org/project/django-admin-soft-dashboard/)

## Comandos base de Proyecto

1. Crear entorno virtual
   ```  
      python -m venv ./venv
    ```
   
2.  Activar el entorno virtual
   ```
    python -m venv ./venv/bin/activate
   ```

3. Crear un proyecto 
   ```   
     django-admin startproject <my_project>
   ```  
   
4. Crear una aplicación 
   ```   
     django-admin startapp <my_app>
   ```  
   
5. Compilar el proyecto 
   ```   
     python manage.py runserver
   ``` 
   
6. Generar archivo requirements.txt, si no lo tenemos o queremos actualizarlo
    ```   
      pip freeze > requirements.txt
   ```  
   
7. Install requirements 
    ```   
      pip install -r requirements.txt
    ```

8. Crear migraciones 
   ```   
      python manage.py migrate
   ```

9. Crear super usuario
   ```   
     python manage.py createsuperuser
   ```
   
10. Crear archivos estaticos
    ```
       python manage.py collectstatic
    ```  
   
### Instalar Dependencias 

##### Django
   ```   
     pip install django
   ```  
##### Instalar django rest framework ✅
   ```   
     pip install djangorestframework
   ```

   - Documentacion [djangorestframework](https://www.django-rest-framework.org/)
   - Requiere configurar el archivo settings.py, para agregar rest_framework
  
   ```  
     INSTALLED_APPS = [
         ...
         'rest_framework',
     ]
   ```  
##### Instalar drf-yasg ✅

  ```
    pip install -U drf-yasg
  ```
- Requiere configurar el archivo settings.py, para agrear drf_yasg
- Requiere configurar el archivo settings.py, para definir rutas estaticas
- Requiere configurar el archivo urls.py, para agrear drf_yasg
- Documentacion [drf-yasg](https://drf-yasg.readthedocs.io/en/stable/readme.html#usage)
  ```
    pip install setuptools
  ```
- Se debe instalar para que funcione correctamente otras dependencias
- Generar achivos estaticos
    ```
       python manage.py collectstatic
    ```
- Agregar los archivos estaticos y configurar la dependencia en settings.py 
    ```
       INSTALLED_APPS = [
         ...
         'django.contrib.staticfiles',  # required for serving swagger ui's css/js files
         'drf_yasg',
       ]
       STATIC_URL = '/static/'
       STATIC_ROOT = './static/'
    ```
  
- Configurar la dependencia en urls.py

    ```
    from rest_framework import permissions
    from drf_yasg.views import get_schema_view
    from drf_yasg import openapi
    
    name_api = 'Django Project'
    schema_view = get_schema_view(
       openapi.Info(
          title=f"Documentación de la API {name_api}",
          default_version='v1',
          description=f"Documentación de la API {name_api}",
          terms_of_service="https://www.google.com/policies/terms/",
          contact=openapi.Contact(email="djangoproject@correo.com"),
          license=openapi.License(name="BSD License"),
       ),
       public=True,
       permission_classes=(permissions.AllowAny,),
    )
    
    urlpatterns = djgentelellaurls + [
        path('admin/', admin.site.urls),
        path('docs/', schema_view.with_ui('swagger', cache_timeout=0), name='schema-swagger-ui'),
        path('redocs/', schema_view.with_ui('redoc', cache_timeout=0), name='schema-redoc'),
    ]
    ```
  
##### Instalar django-admin-soft-dashboard ✅
    ```
       pip install django-admin-soft-dashboard
    ```
-  Configurar la dependencia en settings.py
    ```
    INSTALLED_APPS = (
        ...
       'admin_soft.apps.AdminSoftDashboardConfig', # Debe quedar sobre 'django.contrib.admin'
       'django.contrib.admin',
    )
    ```
   
- Crear archivos estaticos
    ```
       python manage.py collectstatic
    ```
  