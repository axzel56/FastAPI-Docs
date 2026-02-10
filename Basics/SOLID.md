SOLID principles are five essential guidance of software design.

- The SOLID principle helps in enhancing loose coupling. Loose coupling means a group of classes are less dependent on one another.

S - Single Responsibility Principle
O - Open Closed Principle
L - Liskov Substitution Principle
I - Interface Segregation Principle
D - Dependency Inversion Principle

# 1. Single Responsibility Principle

A principle that states that A class should have one reason to change.

# 2. Open/Closed Principle

This principle states that the "Software entities (classes. modules, functions, etc.) should be open for extension, but closed for modification" which means that we should be able to extend a class behavior without modifying it.

```python
from abc import ABC, abstractmethod

class PaymentProcessor(ABC):
	@abstractmethod
	def processPayment(self, amount): # virtual function
		pass
		
class CreditCardPaymentProcessor(PaymentProcessor):
	def processPayment(self, amount):
		print(f"Processing credit card payment of ${amount}")
```


### Note : Virtual Function:
A member function in a base class that can be redefined (overridden) in a derived class to provide a specific implementation, enabling runtime polymorphism (late binding) in OOP.

## Extending Functionality:

Now adding support for PayPal payments, you we create a new class `PayPalPaymentProcessor` that extends `PaymentProcessor`

```python
class PayPalPaymentProcessor(PaymentProcessor):
	def processPayment(self, amount):
		print(f"Processing PayPal payment of ${amount}")
```

##  Usage

We can use either `payment processor` without modifying the existing code for `PaymentProcessor` or `CreditCardPaymentProcessor`

```python
def processPayment(processor, amount):
	processor.processPayment(amount)
	
def main():
	creditCardProcessor = CreditCardPaymentProcessor()
	payPalProcessor = PayPalPaymentProcessor()
	
	processPayment(creditCardProcessor, 100.00)
	# Processing Credit Card Payment
	
	processPayment(payPalProcessor, 150.00)
	
if __name__ = "__main__":
	main()
	
	
```