Youtube videos to get started / get prod ready
1. [Key Concepts](https://www.youtube.com/watch?v=IdsBwplQAMw&list=PLnsTzQ998QGQRY_8SaeMyd3_RuLyegJyx)
2. [Crash Course](https://www.youtube.com/watch?v=2n3xS89TJMI&list=PLlaDAvA2MhR2jb8zavu6I-w1BA878aHcB)
3. [Website with Code Samples](https://wanago.io/courses/api-with-nestjs/)

# Nest CLI

- installing nest cli
```bash
npm install -g @nestjs/cli
```
- Starting a new project (creates a folder by default):
```bash
nest new my-project-api
npm run start:dev
```
- The server will run on localhost:3000

# Nest.js vs Express.js

## 1. App init
- Express
```js
const express = require('express');
const app = express();

app.get('/hello', (req, res) => {
  res.send('Hello World');
});

app.listen(3000, () => console.log('Server running'));
```
- Nest
```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```
- Nest just wraps Express (or Fastify). Instead of writing routes directly on the app, you structure them into modules and controllers.

---

## 2. Routes and Controllers
- Express
```js
app.get('/users', (req, res) => {
  res.json([{ id: 1, name: 'Alice' }]);
});
```
- Nest
```ts
import { Controller, Get } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return [{ id: 1, name: 'Alice' }];
  }
}
```
- In Nest, the routes are grouped inside the controllers, making them more cleaner and testable.
---

## 3. Middleware
- Express
```js
app.use((req, res, next) => {
  console.log('Request:', req.url);
  next();
});
```
- Nest
```ts
import { Injectable, NestMiddleware } from '@nestjs/common';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: Function) {
    console.log('Request:', req.url);
    next();
  }
}
```
- Applied inside a module (configure method of Module class)

---

## 4. Dependency Injection
- In **Express** we usually require or import services and call them directly 
- **Nest** uses **DI containers**. Services are classes with the *@Injectable()* decorator. Nest will inject them where ever needed.
```ts
@Injectable()
export class UsersService {
  findAll() {
    return ['Alice', 'Bob'];
  }
}

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  findAll() {
    return this.usersService.findAll();
  }
}
```
- This makes the code cleaner, testable and scalable 

## 5. Error Handling
- Express
```js
app.use((err, req, res, next) => {
  res.status(500).send('Something broke!');
});
```
- Nest
	- built-in exception filters
```ts
import { Catch, ExceptionFilter, ArgumentsHost } from '@nestjs/common';

@Catch()
export class AllExceptionsFilter implements ExceptionFilter {
  catch(exception: any, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse();
    response.status(500).json({ message: 'Something broke!' });
  }
}
```

## 6. Project Sturcture
- Express: flat, flexible, can get messy quick if project grows
```js
app.js
routes/
  users.js
services/
  usersService.js
```
- Nest: 
```ts
src/
  app.module.ts
  users/
    users.module.ts
    users.controller.ts
    users.service.ts
```
- Nest is opinionated but keeps large codebases maintainable.


## 7. Advanced Features (Baked-in)
With Express, you install and wire everything manually:

- Validation → express-validator
    
- Config → dotenv
    
- Swagger → swagger-ui
    
- Guards / Auth → passport / jwt
    
- Testing → supertest + mocha/jest
    

  
In Nest:

- Built-in **Validation Pipes** (with class-validator)
    
- **ConfigModule** for env variables
    
- **SwaggerModule**
    
- **Guards & Interceptors**
    
- Testing with Jest out of the box