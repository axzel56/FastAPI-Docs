`viewSet` is a class that combines the logic for a set of related views into single unit, allowing developers to focus on the API interactions rather than URL configurations.

`ViewSets` provide actions like:
- `list()`  -> Get all
- `retrieve()` -> Get one
- `create()` -> POST
- `update()` -> Put/Patch
- `destroy()` -> DELETE
which are then bound to specific HTTP methods (GET, POST, PUT, DELETE etc) only when the final view are instantiated, typically using a `Router` class.

## Key Concepts and Benefits

### Code Consolidation:
	
A single `ViewSet` class can manage all CRUD operations for a model, reducing boilerplate code compared to using separate class-based views for each operations.

### Automatic URL Routing:

`ViewSets` are typically used with RDF `Router` classes (like `DefaultRouter` or `SimpleRouter`), which automatically generate the URL patterns for the defined actions.

### Abstractions:

They offer a higher level of abstractions, allowing us to define the behavior of an API resources more intuitively.


# Type of ViewSet

DRF provides several built-in `ViewSet` classes for different use cases:

- `ViewSet` : The most basic `ViewSet`, inheriting from [[APIView]]. It does not provide any action implementations by default.
- `GenericViewSet` : Inherits from `GenericAPIView` and provides base methods like `get_object()` and `get_queryset()` , but no actions by default.
- `ModelViewSet`: It inherits from `GenericViewSet` and all the standard mixins to provide a complete set of CRUD actions 

### `get_queryset()`

  a method that returns the "base query" for the ViewSet.
  - In `GenericModelViewSet`:
	  ```python
	  def get_queryset(self):
		  return self.db.query(self.model)
	  ```
	  It returns all the rows of the model's table as a `SQLAlchemy` query.

	  
	  