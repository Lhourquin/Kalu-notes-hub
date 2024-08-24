# Service

## What is a service ?

* A service is a program that performs a specific task and conforms to system or network protocols to ensure that other programs or systems can use its functionality.
* The term "service" is more commonly used in Windows operating systems, whereas "daemon"" is the equivalent term used in Unix or Linux.
* Services can be managed by the operating system's service manager which allows starting, stoping, and monitoring them.
* They can be either interactive (responding to user inputs) or non-interactive (running in the background).
* An example of a service might be the Print Spooler service in Windows that manages all print jobs sent to the printer.

Services are a broader concept that could include daemons but also refers to any software providing functionality to other software or systems,
often managed through a specific framework by the operating system.

> [!WARNING]
> The term service can have some distinction in different context:
>
> * Services in Operating System (What we say above)
> * Services in High-Level Software: In software development, particuarly when discussing architectre like microservices, a "service" refers to a self-contained unit of software that performs a specific function or group of functions.
> These services communicate with each other using well-defined interfaces, often over a network.
> This use of "service" is more abstract and aligns with business logic and application functionnality rather than just backgournd tasks.
> For instance, an "email service" might handle all aspects of sending and receiving emails for a larger application.
>
> * Key Differences:
>   * **Scope and Functionality**, System-level services are often lower-level and more concerned with the operation of the hardware and core software components.
> High-level services in development are usually focused on specific business needs and functionnalities.
>   * **Interaction and Integration**, System services usually operate independentaly of direct user interactions and are often managed by the system or network administrators.
> In contrast, high-level application services are designed to interact with other parts of an application or external services to deliver complex functionnalities.
>
