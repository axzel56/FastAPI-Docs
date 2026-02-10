Dependency Injection achieves Inversion of Control between classes and their dependencies. DI increases testablility and modularity by externalizing the building and control of dependencies

Dependency Injection involves injecting a class's dependencies rather than letting class generate them on its own.


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