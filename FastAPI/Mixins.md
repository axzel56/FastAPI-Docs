A small reusable classes that provides specific functionalities to other classes, primarily class-based views (CBVs) and models, using multiple inheritance.
## Django Class-Based View Mixins
- `LoginRequiredMixin` : Ensures that the current user is authenticated to access the view.
- `PermissionRequiredMixin` : Verifies that the user has specific permissions.
- `UserPassesTestMixin` : Allows defining a custom test function that the user must pass to access the view.

- `SingleObjectMixin` : Provides functionality for working with a single Django object (e.g. retrieving an object based on primary key from a URL)
- `MultipleObjectMixin` : 