# Nestjs

This project aim to handle the fundamental of nestjs framework, step by step in this readme I will explain how it work, core concept to get good understanding of this technologoies.

## Core concept

### `@Decorators`

In Nest, Decorators are everywhere, so this why need to see this notion at first.

#### Decorators are not magic, there a functions

These functions can be apply to classes, methods, and even method parameter. A decorators will add extra functionalities, metadata to the class, method or parameters they apply to, and some decorators will have extra parameters to control they behavior. That we can see on the `app.module.ts` file:

```ts app.module.ts
@Module({
  imports: [],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

This `Decorators` take a configuration object as argument, to apply a specific behavior to the `AppModule` class. It is use specifically for `Module` classes. Explanation of the code above:

- `@Module` organizes related controllers, services, and other elements.

- `imports: []` allowing to import other modules into this module. In this case, it's empty because we don't importing anything.

- `controllers: [AppController]` is the lists of controllers that are aprt of this module. In this case, we have `AppController`, which likely handles routing and requests.

- `providers: [AppService]` is the lists of services (like `AppService`) that can be **injected** into controllers or other providers via dependency injection. These services are used to handle business logic, connect to databse, or interact with external API's.

- `AppModule` is the class that becomes the root module of our application. This is where NestJS looks for how to wire the application components together.

Types of `Decorators`:

- **Class Decorators**: We have other `Decorators` for different type of class like `@Controllers`, `@Injectable`, etc.

- **Method Decorators**: Also for methods as mentioned above, often use for routes or middlewares.
  For instance, `@Get()`, `@Post()`, `@useGuards()`, etc.
- **Parameter Decorators**: Applied to parameters to inject specific types of data. Examples include `@Params()`, `@Body()`, and `@Query`.

- **Property Decorators**: Used to inject dependencies into class properties, like `@Inject()` or `@Optional()`.
