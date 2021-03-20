# Readings: Permissions & Postgresql

## [DRF Permissions](https://www.django-rest-framework.org/api-guide/permissions/)

> Together with authentication and throttling, permissions determine whether a request should be granted or denied access

> Permission checks are always run at the very start of the view, before any other code

| authentication method | used when? |
|---|---|
|request.user | Permission checks will typically use the authentication information in this property to determine if the incoming request should be permitted. |
|request.auth |Permission checks will typically use the authentication information in this property to determine if the incoming request should be permitted. |
|IsAuthenticated | simplest style of permission would be to allow access to any authenticated user, and deny access to any unauthenticated user. |
|IsAuthenticatedOrReadOnly | slightly less strict style of permission would be to allow full access to authenticated users, but allow read-only access to unauthenticated users|

> Permissions in REST framework are always defined as a list of permission classes.

> Before running the main body of the view each permission in the list is checked.

**exceptions if permission check fails exceptions.PermissionDenied or exceptions.NotAuthenticated**

> REST framework permissions also support object-level permissioning. Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.

> Object level permissions run when when .get_object() is called

> writing your own views and want to enforce object level permissions? Want to override the get_object method on a generic view?

> explicitly call the .check_object_permissions(request, obj) method on the view at the point at which you've retrieved the object.

example:

``` python
def get_object(self):
    obj = get_object_or_404(self.get_queryset(), pk=self.kwargs["pk"])
    self.check_object_permissions(self.request, obj)
    return obj
```

> when you're using object level permissions you'll also want to filter the queryset appropriately

> The default permission policy may be set globally, using the DEFAULT_PERMISSION_CLASSES:

``` python
REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticated',
    ]
}
```

> not specified, unrestricted access:

``` python
'DEFAULT_PERMISSION_CLASSES': [
   'rest_framework.permissions.AllowAny',
]
```

> set the authentication policy on a per-view, or per-viewset basis, using the APIView class-based views

``` python
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response
from rest_framework.views import APIView

class ExampleView(APIView):
    permission_classes = [IsAuthenticated]

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```

> using the @api_view decorator with function based views.

``` python
from rest_framework.decorators import api_view, permission_classes
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response

@api_view(['GET'])
@permission_classes([IsAuthenticated])
def example_view(request, format=None):
    content = {
        'status': 'request was permitted'
    }
    return Response(content)
```

> If they inherit from rest_framework.permissions.BasePermission, you can compose using standard Python bitwise operators.IsAuthenticatedOrReadOnly could be written:

``` python
from rest_framework.permissions import BasePermission, IsAuthenticated, SAFE_METHODS
from rest_framework.response import Response
from rest_framework.views import APIView

class ReadOnly(BasePermission):
    def has_permission(self, request, view):
        return request.method in SAFE_METHODS

class ExampleView(APIView):
    permission_classes = [IsAuthenticated|ReadOnly]

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```

### API Reference

[AllowAny](https://www.django-rest-framework.org/api-guide/permissions/#allowany)
[IsAuthenticated](https://www.django-rest-framework.org/api-guide/permissions/#isauthenticated)
[IsAdminUser](https://www.django-rest-framework.org/api-guide/permissions/#isadminuser)
[IsAuthenticatedOrReadOnly](https://www.django-rest-framework.org/api-guide/permissions/#isauthenticatedorreadonly)
[DjangoModelPermissions](https://www.django-rest-framework.org/api-guide/permissions/#djangomodelpermissions)
[DjangoModelPermissionsOrAnonReadOnly](https://www.django-rest-framework.org/api-guide/permissions/#djangomodelpermissionsoranonreadonly)
[DjangoObjectPermissions](https://www.django-rest-framework.org/api-guide/permissions/#djangoobjectpermissions)
[Custom permissions](https://www.django-rest-framework.org/api-guide/permissions/#custom-permissions)


## Bookmark/Skim

-[x] [Classy Django REST](http://www.cdrf.co/)
-[x] [DRF Generic Views](https://www.django-rest-framework.org/api-guide/generic-views/)