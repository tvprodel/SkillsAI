# NestJS Architecture

## Objectif
Concevoir architecture backend NestJS modulaire (controllers, services, modules, dependency injection, guards, interceptors).

## Quand l'utiliser (triggers)
- « NestJS », « architecture NestJS », « modules », « dependency injection », « guards », « interceptors », « API NestJS ».
- Création backend Node.js structuré.
- Refacto Express → NestJS.

## Hors périmètre
- Frontend → skill React Hooks Patterns ou typescriptJavascript (frontend).
- BDD migrations → l'agent bases de données.
- Tests → l'agent qualité.

## Inputs requis
- Architecture cible (monolithe modulaire, micro-services).
- Modules (users, auth, products, etc.).
- Auth (JWT, OAuth, Passport strategies).
- BDD (TypeORM, Prisma, Mongoose).

## Sorties attendues
- Structure projet NestJS (modules, controllers, services).
- Configuration DI (dependency injection).
- Guards (auth), Interceptors (logging, transform), Pipes (validation).

## Workflow recommandé
1. **Modules** (organisation) :
   ```bash
   nest g module users
   nest g controller users
   nest g service users
   ```
   ```typescript
   @Module({
     imports: [TypeOrmModule.forFeature([User])],
     controllers: [UsersController],
     providers: [UsersService],
     exports: [UsersService],  // si utilisé par autres modules
   })
   export class UsersModule {}
   ```
2. **Controllers** (routes) :
   ```typescript
   @Controller('users')
   export class UsersController {
     constructor(private usersService: UsersService) {}  // DI
     
     @Get()
     findAll() { return this.usersService.findAll(); }
     
     @Post()
     @UseGuards(JwtAuthGuard)
     create(@Body() dto: CreateUserDto) { return this.usersService.create(dto); }
   }
   ```
3. **Services** (business logic) :
   ```typescript
   @Injectable()
   export class UsersService {
     constructor(@InjectRepository(User) private repo: Repository<User>) {}
     
     async findAll() { return this.repo.find(); }
     async create(dto: CreateUserDto) { return this.repo.save(dto); }
   }
   ```
4. **Guards** (auth) :
   ```typescript
   @Injectable()
   export class JwtAuthGuard extends AuthGuard('jwt') {}
   ```
5. **Pipes** (validation) :
   ```typescript
   @Post()
   create(@Body(new ValidationPipe()) dto: CreateUserDto) { ... }
   ```
6. **Interceptors** (logging, transform) :
   ```typescript
   @Injectable()
   export class LoggingInterceptor implements NestInterceptor {
     intercept(context, next) {
       console.log('Before...');
       return next.handle().pipe(tap(() => console.log('After...')));
     }
   }
   ```

## Garde-fous
- Modules délimités (single responsibility).
- DI utilisé (pas new Service() manuel).
- DTOs séparés (class-validator decorators).
- Guards auth (JwtAuthGuard, RolesGuard).
- Interceptors logging (Winston, Pino).

## Template d'entrée (copier/coller)
```text
[Architecture]
- Type : monolithe/micro-services
- Modules : ...

[Auth]
- Type : JWT/OAuth

[BDD]
- Provider : TypeORM/Prisma
```

## Template de sortie (copier/coller)
```text
[Structure]
- Modules : ...
- Controllers : ...
- Services : ...

[DI]
- Providers : ...

[Guards]
- JwtAuthGuard : ...

[Interceptors]
- Logging : ...
```

## Checklist QA interne
- Modules délimités.
- DI utilisé.
- DTOs avec validation.
- Guards auth.
- Interceptors logging.

## KPI reliés
- Nb modules (complexité).
- Couverture validation DTOs (%).
- Temps réponse API (ms).

## Definition of done
- Architecture NestJS créée.
- Modules/controllers/services validés.
- Guards/interceptors configurés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]