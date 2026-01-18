<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  # NestJS Backend – Architecture Overview

## 1. General Overview

This project is a basic NestJS backend application initialized as a foundation for a scalable and maintainable server-side system.

The goal of this stage is not to implement business logic, but to:
- properly initialize a NestJS project,
- establish a clean modular structure,
- define architectural boundaries,
- prepare the project for future scaling.

The project follows NestJS best practices and focuses on clarity, maintainability, and explicit architecture.

---

## 2. Architectural Principles

The architecture is based on the following principles:

- **Modularity** – each business domain is isolated in its own module  
- **Separation of concerns** – controllers, services, and configuration are clearly separated  
- **Scalability** – new features can be added without refactoring existing code  
- **Environment awareness** – application behavior depends on runtime environment  
- **Explicit configuration** – configuration is centralized and predictable  

NestJS was chosen because it enforces architectural discipline and provides a strong foundation for production-ready backend systems.

---

## 3. Project Structure

```text
src/
├── app.module.ts
├── main.ts
├── users/
│   ├── users.module.ts
│   ├── users.controller.ts
│   ├── users.service.ts
│   └── dto/
├── config/
│   ├── app.config.ts
│   └── index.ts
.env.local
.env.production
```

Structure Explanation

**main.ts**
Application entry point. Responsible only for bootstrapping the application and starting the HTTP server.

**app.module.ts**
Root module that composes all feature modules and global infrastructure (configuration, middleware, etc.).

**users/** */
Feature module representing a business domain.
Contains:

controller (HTTP layer),

service (business logic),

DTOs (data contracts).

This structure ensures that each domain is self-contained and can evolve independently.

## 4.Modules, Controllers and Providers

The project follows NestJS core building blocks:

- **Modules** - Organize related functionality and define dependency boundaries.

- **Controllers** - Handle incoming HTTP requests and delegate logic to services.

- **Providers (Services)** - Contain business logic and can be injected into other components.

This separation improves readability, testability, and long-term maintainability.

## 5. Environment Configuration Strategy

The application uses @nestjs/config for environment-based configuration.

Environment Variables

Different environments are supported via separate .env files:
```text
.env.local
.env.production
```
The active environment is selected using the NODE_ENV variable.
```bash
"start": "cross-env NODE_ENV=production nest start",
"start:dev": "cross-env NODE_ENV=local nest start --watch"
```
This approach ensures:

- **cross-platform compatibility**,
- **explicit environment selection**,
- **predictable runtime behavior.**
```bash
ConfigModule.forRoot({
  isGlobal: true,
  envFilePath: `.env.${process.env.NODE_ENV}`,
});
```

## 6. Why This Architecture Was Chosen

This architecture was intentionally designed to:

- **avoid tightly coupled code,**

- **minimize future refactoring,**

- **clearly express intent and responsibility,**

- **align with real-world backend team practices.**

Even at an early stage, the structure reflects production-oriented thinking rather than a quick prototype.

## 7. Future Improvements

The current architecture allows easy extension in the future, such as:

- **adding new feature modules,**

- **introducing database modules,**

- **implementing authentication and authorization,**

- **adding logging and observability,**

- **extending configuration into domain-specific configs.**


## Project setup

Requirements

  -**Node.js (LTS version)**
  -**npm or yarn**

```bash
$ fit clone git@github.com:Pozdnya/ecommerce-nest.git
```

```bash
$ cd ecommers-nest
```

```bash
$ npm install
```

## Compile and run the project

```bash
# production
$ npm run start

# development mode
$ npm run start:dev
```


<!-- ## Deployment

When you're ready to deploy your NestJS application to production, there are some key steps you can take to ensure it runs as efficiently as possible. Check out the [deployment documentation](https://docs.nestjs.com/deployment) for more information.

If you are looking for a cloud-based platform to deploy your NestJS application, check out [Mau](https://mau.nestjs.com), our official platform for deploying NestJS applications on AWS. Mau makes deployment straightforward and fast, requiring just a few simple steps:

```bash
$ npm install -g @nestjs/mau
$ mau deploy
```

With Mau, you can deploy your application in just a few clicks, allowing you to focus on building features rather than managing infrastructure. -->

