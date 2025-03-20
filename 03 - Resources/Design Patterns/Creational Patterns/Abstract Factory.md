#### Purpose
___
Abstract Factory Pattern is a creational design pattern used in object-oriented programming. It provides an interface for creating families of related or dependent objects without specifying their concrete classes. This pattern is a way to encapsulate the creation of objects and ensure that they are compatible and properly configured.

#### Components
___
- *Abstract Factory Interface:* This interface defines a set of methods for creating various abstract product types. Each method in the interface corresponds to a different product family.
- *Concrete Factories:* Concrete factory classes implement the Abstract Factory interface. Each concrete factory is responsible for creating a specific family of related products.
- *Abstract Product Interfaces:* These interfaces define the structure and behavior of the product objects created by the factory. Each product family has its set of abstract product interfaces.
- *Concrete Products:* Concrete product classes implement the abstract product interfaces. These classes represent the actual objects that the client code will use.
- *Client:* The client code works with the abstract factory and abstract product interfaces. It doesn't need to know the concrete classes of the products it uses. Instead, it relies on the factory to create compatible objects.
___
Tags : #programming #design-patterns #creational-pattern 