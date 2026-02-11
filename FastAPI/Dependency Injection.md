Dependency Injection achieves Inversion of Control between classes and their dependencies. DI increases testablility and modularity by externalizing the building and control of dependencies

Dependency Injection involves injecting a class's dependencies rather than letting class generate them on its own.

#### Dependency injection = "uses a"

```python
class Engine:
	def start(self):
		print("Engine started")

class Car:
	def __init__(self, dependency_class)
		self.dependency_class = dependency_class
	
	def drive(self):
		self.engine.start()
```

`Car` uses an `Engine`
`Car` is not an Engine. `Car` is not born with an engine, its a frame that can accept any engine.
No inheritance at all.

#### 1. Dynamic Behavior (Hot-swapping) Swapping

The `Car` uses whatever is injected into `self.engine` we can change the behavior of the car's behavior w/o touching the `Car` class. 

`Eg:
We can swap a gasoline for an electric one.`

#### 2. Lifetime Management:

When a class 'is-a' (inheritance), the child controls the parent lifecycle.
With `uses-a`, the injector controls it. This allows for:

- Shared Dependencies: Two different `Car` objects could use the same GPS_unit instance.
- Lazy Loading: We can delay creating `Engine` until the very moment `Car` actually needs to drive.


# Dependency Injection Techniques in Python

## Constructor Injection

It is supplying dependencies via a class's initializer, `__init__` method.
```python
class Service:
	def do_something(self):
		print("Service is doing Something")
class Client:
	def __init__(self, service: Service):
		self.service = service
	def perform_task(self):
		self.service.do_something()

service = Service()
client = Client(service)
client.perform_task()
``` 