
``` python
@action(
    response_model=SignUpInitialDataResponseSchema,
    permission_classes=[AllowAny],
    url_path="api/v2/signup-initial-data",
)
```
# @action 

`@action` is used in a *ViewSet* to add a custom endpoint that isnot one of the standard CRUD  actions (`list, retrieve, create` )
so this creates an extra route on the `viewset`.

##### `permission_classes = [AllowAny]`

- No authentication required
- Anyone logged in or not can hit the endpoint
- Common for signup/login/public metadata endpoints
- Overrides whatever permissions are set on the viewset

#####  `url_path="api/v2/signup-initial-data"`

- This controls the URL fragment added by the router.
- W/O this DRF would auto generate a name from the method.
- The endpoint will be exposed as:
		`/<viewset-base>/api/v2/signup-initial-data`


## `add_to(app)`

- `add_to` is a helper that registers all the HTTP routes of the viewset to a FastAPI app.
- It knows the prefix, the methods and the paths.
- so without writing `@app.get('specific/route')`, its implicitly registered by the `add_to` method

Those routes lives in the routers.


- How Fast API handles the request:
1. `uvicorn` *running the app* receives the request.
2. FastAPI looks up the route in its routing table.
3. The route exists because `OnboardingViewSet.add_to(app)` registered the path.
4. Dependencies are automatically injected before the method runs.
5. The method returns JSON -> FastAPI serializes and returns it