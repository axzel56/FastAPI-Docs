`GenericViewSet and ModelViewSet`


## GenericViewSet

A base viewset that provides
 - Viewset behaviour (routing via router)
 - Integration with generic API views
 - No CRUD actions by default
*Need to write methods ourselves*

It gives methods:
- `get_queryset()`
- `get_serializer_class()`
- `lookup_field()`
- Works with routers
