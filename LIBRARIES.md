# Tài Liệu Mô Tả Thư Viện - LE Backend

Tài liệu này mô tả chi tiết về các thư viện được sử dụng trong dự án, tác dụng, lý do sử dụng và lợi ích của từng thư viện.

---

## 📦 DEPENDENCIES (Thư Viện Sản Phẩm)

### Core Framework - NestJS

#### `@nestjs/common` (^11.0.1)
- **Tác dụng**: Module cốt lõi của NestJS, cung cấp các decorators, exceptions, pipes, guards, interceptors và các utilities cơ bản.
- **Tại sao dùng**: Đây là thư viện bắt buộc cho mọi ứng dụng NestJS, cung cấp nền tảng cho dependency injection và kiến trúc modular.
- **Lợi ích**: 
  - Cung cấp các decorators như `@Injectable()`, `@Controller()`, `@Module()`
  - Xử lý exceptions và HTTP status codes
  - Hỗ trợ pipes cho validation và transformation

#### `@nestjs/core` (^11.0.1)
- **Tác dụng**: Core engine của NestJS, quản lý dependency injection container, module system và application lifecycle.
- **Tại sao dùng**: Cần thiết để khởi tạo và chạy ứng dụng NestJS.
- **Lợi ích**:
  - Quản lý dependency injection
  - Xử lý module loading và initialization
  - Cung cấp `NestFactory` để bootstrap ứng dụng

#### `@nestjs/platform-express` (^11.0.1)
- **Tác dụng**: Adapter để tích hợp NestJS với Express.js framework.
- **Tại sao dùng**: NestJS mặc định sử dụng Express làm HTTP server, cần adapter này để kết nối.
- **Lợi ích**:
  - Tận dụng hệ sinh thái Express phong phú
  - Hiệu suất cao và ổn định
  - Hỗ trợ middleware của Express

---

### Configuration & Environment

#### `@nestjs/config` (^4.0.2)
- **Tác dụng**: Module quản lý cấu hình ứng dụng từ environment variables và file config.
- **Tại sao dùng**: Cần quản lý cấu hình một cách tập trung và type-safe.
- **Lợi ích**:
  - Load config từ `.env` files
  - Validation schema cho environment variables
  - Type-safe configuration với TypeScript
  - Hỗ trợ nhiều môi trường (dev, staging, production)

---

### API Documentation

#### `@nestjs/swagger` (^11.2.2)
- **Tác dụng**: Tích hợp Swagger/OpenAPI vào NestJS để tự động generate API documentation.
- **Tại sao dùng**: Cần tài liệu API tự động, dễ bảo trì và cập nhật.
- **Lợi ích**:
  - Tự động generate OpenAPI spec từ decorators
  - Interactive API documentation UI
  - Validation schema tự động
  - Giảm công sức viết tài liệu thủ công

#### `swagger-ui-express` (^5.0.1)
- **Tác dụng**: Giao diện web để hiển thị Swagger documentation.
- **Tại sao dùng**: Cung cấp UI đẹp và dễ sử dụng để test API trực tiếp.
- **Lợi ích**:
  - UI trực quan, dễ sử dụng
  - Test API trực tiếp từ browser
  - Hỗ trợ authentication trong UI

---

### Health Checks & Monitoring

#### `@nestjs/terminus` (^11.0.0)
- **Tác dụng**: Module cung cấp health check endpoints cho ứng dụng.
- **Tại sao dùng**: Cần monitor trạng thái ứng dụng, database, Redis, và các services khác.
- **Lợi ích**:
  - Health check endpoints chuẩn
  - Tích hợp với database, Redis, memory checks
  - Hữu ích cho Kubernetes liveness/readiness probes
  - Monitoring và alerting

---

### Rate Limiting & Throttling

#### `@nestjs/throttler` (^6.4.0)
- **Tác dụng**: Module rate limiting tích hợp sẵn cho NestJS.
- **Tại sao dùng**: Bảo vệ API khỏi abuse, DDoS attacks và đảm bảo fair usage.
- **Lợi ích**:
  - Dễ cấu hình với decorators
  - Hỗ trợ in-memory và Redis storage
  - Flexible rate limiting strategies
  - Tích hợp tốt với NestJS guards

#### `rate-limiter-flexible` (^8.2.1)
- **Tác dụng**: Thư viện rate limiting mạnh mẽ và linh hoạt.
- **Tại sao dùng**: Cần rate limiting phức tạp hơn, với nhiều strategies và storage options.
- **Lợi ích**:
  - Nhiều algorithms (fixed window, sliding window, token bucket)
  - Hỗ trợ Redis, MongoDB, MySQL, PostgreSQL
  - Distributed rate limiting
  - Blocking và queueing strategies

---

### Validation & Transformation

#### `class-validator` (^0.14.2)
- **Tác dụng**: Validation library sử dụng decorators để validate DTOs và classes.
- **Tại sao dùng**: Cần validate dữ liệu đầu vào một cách type-safe và declarative.
- **Lợi ích**:
  - Decorator-based validation (dễ đọc, dễ maintain)
  - Nhiều validators có sẵn (email, min, max, custom)
  - Tích hợp tốt với NestJS pipes
  - TypeScript support tốt

#### `class-transformer` (^0.5.1)
- **Tác dụng**: Transform plain objects thành class instances và ngược lại.
- **Tại sao dùng**: Cần convert JSON từ HTTP requests thành DTO classes và transform data.
- **Lợi ích**:
  - Transform objects thành class instances
  - Exclude/include properties
  - Transform property names
  - Type-safe transformations

#### `nestjs-zod` (^5.0.1)
- **Tác dụng**: Tích hợp Zod schema validation vào NestJS.
- **Tại sao dùng**: Zod cung cấp validation mạnh mẽ hơn với TypeScript inference tốt.
- **Lợi ích**:
  - Type inference tự động từ schema
  - Validation mạnh mẽ và linh hoạt
  - Có thể dùng chung cho frontend và backend
  - Better error messages

---

### Security

#### `helmet` (^8.1.0)
- **Tác dụng**: Set các HTTP security headers để bảo vệ ứng dụng khỏi các lỗ hổng phổ biến.
- **Tại sao dùng**: Bảo mật là ưu tiên hàng đầu, cần set headers đúng cách.
- **Lợi ích**:
  - Bảo vệ khỏi XSS attacks
  - Ngăn clickjacking
  - HSTS (HTTP Strict Transport Security)
  - Content Security Policy
  - Dễ cấu hình, một dòng code

#### `csurf` (^1.11.0)
- **Tác dụng**: CSRF (Cross-Site Request Forgery) protection middleware.
- **Tại sao dùng**: Bảo vệ ứng dụng khỏi CSRF attacks.
- **Lợi ích**:
  - Token-based CSRF protection
  - Tích hợp với cookie-parser
  - Tự động generate và validate tokens

#### `cookie-parser` (^1.4.7)
- **Tác dụng**: Parse HTTP cookies từ request headers.
- **Tại sao dùng**: Cần xử lý cookies cho authentication, sessions, CSRF tokens.
- **Lợi ích**:
  - Parse cookies thành object dễ sử dụng
  - Hỗ trợ signed cookies
  - Middleware đơn giản, hiệu quả

---

### Logging

#### `pino` (^10.1.0)
- **Tác dụng**: Fast JSON logger cho Node.js, rất nhanh và hiệu quả.
- **Tại sao dùng**: Cần logging hiệu suất cao, structured logging cho production.
- **Lợi ích**:
  - Rất nhanh (asynchronous logging)
  - Structured JSON logging
  - Child loggers
  - Low overhead

#### `nestjs-pino` (^4.4.1)
- **Tác dụng**: NestJS module tích hợp Pino logger.
- **Tại sao dùng**: Cần Pino logger tích hợp sẵn với NestJS dependency injection.
- **Lợi ích**:
  - Tích hợp sẵn với NestJS
  - Auto-logging cho HTTP requests
  - Request ID tracking
  - Dễ cấu hình

#### `pino-pretty` (^13.1.2)
- **Tác dụng**: Pretty printer cho Pino logs trong development.
- **Tại sao dùng**: Logs JSON khó đọc trong development, cần format đẹp hơn.
- **Lợi ích**:
  - Format logs dễ đọc trong development
  - Color-coded output
  - Chỉ dùng trong dev, không ảnh hưởng production performance

---

### Reactive Programming

#### `rxjs` (^7.8.1)
- **Tác dụng**: Reactive Extensions library cho JavaScript, xử lý asynchronous và event-based programming.
- **Tại sao dùng**: NestJS sử dụng RxJS cho observables, streams và reactive patterns.
- **Lợi ích**:
  - Powerful operators cho data transformation
  - Xử lý async operations tốt
  - Error handling tốt
  - Backpressure handling

---

### Metadata & Reflection

#### `reflect-metadata` (^0.2.2)
- **Tác dụng**: Polyfill cho Metadata Reflection API, cần thiết cho decorators và dependency injection.
- **Tại sao dùng**: NestJS sử dụng metadata để implement decorators và DI container.
- **Lợi ích**:
  - Hỗ trợ decorators và metadata
  - Cần thiết cho TypeScript decorators
  - Runtime type information

---

## 🛠️ DEV DEPENDENCIES (Thư Viện Phát Triển)

### NestJS Development Tools

#### `@nestjs/cli` (^11.0.0)
- **Tác dụng**: Command-line interface để generate code, build và run NestJS applications.
- **Tại sao dùng**: Tăng tốc độ phát triển với code generation và scaffolding.
- **Lợi ích**:
  - Generate modules, controllers, services
  - Build và compile TypeScript
  - Hot reload trong development
  - Project scaffolding

#### `@nestjs/schematics` (^11.0.0)
- **Tác dụng**: Code generation schematics cho NestJS CLI.
- **Tại sao dùng**: Cung cấp templates và rules cho code generation.
- **Lợi ích**:
  - Consistent code structure
  - Tự động generate boilerplate
  - Customizable templates

#### `@nestjs/testing` (^11.0.1)
- **Tác dụng**: Testing utilities cho NestJS, cung cấp testing module và mocks.
- **Tại sao dùng**: Cần test NestJS modules, controllers, services một cách dễ dàng.
- **Lợi ích**:
  - `TestingModule` để test modules
  - Mock providers dễ dàng
  - Integration testing support
  - Override providers trong tests

---

### Database & ORM

#### `prisma` (^6.19.0)
- **Tác dụng**: Next-generation ORM với type-safe database client và migration tool.
- **Tại sao dùng**: Cần ORM mạnh mẽ, type-safe và dễ sử dụng.
- **Lợi ích**:
  - Type-safe database queries
  - Auto-generated TypeScript types
  - Migration management
  - Database introspection
  - Hỗ trợ nhiều databases (PostgreSQL, MySQL, SQLite, MongoDB)

#### `@prisma/client` (^6.19.0)
- **Tác dụng**: Generated Prisma Client để query database với type safety.
- **Tại sao dùng**: Runtime client được generate từ Prisma schema.
- **Lợi ích**:
  - Type-safe queries
  - Auto-completion trong IDE
  - Query builder mạnh mẽ
  - Relations handling tốt

---

### Caching

#### `@nestjs/cache-manager` (^3.0.1)
- **Tác dụng**: NestJS module cho caching với nhiều storage backends.
- **Tại sao dùng**: Cần caching để tăng performance và giảm database load.
- **Lợi ích**:
  - Decorator-based caching (`@CacheKey`, `@CacheTTL`)
  - Hỗ trợ nhiều stores (memory, Redis)
  - Tích hợp tốt với NestJS
  - Easy to use

#### `cache-manager` (^7.2.5)
- **Tác dụng**: Cache abstraction layer, hỗ trợ nhiều cache stores.
- **Tại sao dùng**: Cần flexible caching solution với nhiều storage options.
- **Lợi ích**:
  - Unified API cho nhiều cache stores
  - Memory, Redis, MongoDB stores
  - TTL support
  - Cache invalidation

#### `ioredis` (^5.8.2)
- **Tác dụng**: Redis client cho Node.js, hiệu suất cao và feature-rich.
- **Tại sao dùng**: Cần Redis cho caching, sessions, rate limiting.
- **Lợi ích**:
  - Hiệu suất cao
  - Hỗ trợ Redis Cluster và Sentinel
  - Promise-based API
  - Auto-reconnection
  - Pub/Sub support

#### `ioredis-mock` (^8.13.1)
- **Tác dụng**: Mock Redis client cho testing.
- **Tại sao dùng**: Cần test code sử dụng Redis mà không cần Redis server thật.
- **Lợi ích**:
  - Test không cần Redis server
  - Fast tests
  - In-memory implementation
  - Compatible với ioredis API

---

### TypeScript & Compilation

#### `typescript` (^5.7.3)
- **Tác dụng**: TypeScript compiler và language service.
- **Tại sao dùng**: Dự án sử dụng TypeScript cho type safety và better developer experience.
- **Lợi ích**:
  - Type safety
  - Better IDE support
  - Modern JavaScript features
  - Compile-time error checking

#### `@swc/core` (^1.10.7)
- **Tác dụng**: Super-fast TypeScript/JavaScript compiler viết bằng Rust.
- **Tại sao dùng**: Cần compile nhanh hơn tsc, đặc biệt trong development với hot reload.
- **Lợi ích**:
  - Nhanh hơn tsc 10-20 lần
  - Hỗ trợ TypeScript và JSX
  - Minification và bundling
  - Used bởi NestJS CLI cho fast builds

#### `@swc/cli` (^0.6.0)
- **Tác dụng**: Command-line interface cho SWC compiler.
- **Tại sao dùng**: Cần CLI tool để compile với SWC.
- **Lợi ích**:
  - Compile từ command line
  - Watch mode
  - Source maps support

#### `ts-node` (^10.9.2)
- **Tác dụng**: TypeScript execution engine cho Node.js, chạy TypeScript trực tiếp không cần compile.
- **Tại sao dùng**: Cần chạy TypeScript files trực tiếp trong development và testing.
- **Lợi ích**:
  - Chạy `.ts` files trực tiếp
  - Không cần compile trước
  - Hỗ trợ tsconfig.json
  - Fast startup

#### `ts-loader` (^9.5.2)
- **Tác dụng**: TypeScript loader cho Webpack.
- **Tại sao dùng**: Nếu sử dụng Webpack để bundle, cần loader này.
- **Lợi ích**:
  - TypeScript compilation trong Webpack
  - Source maps
  - Type checking

#### `tsconfig-paths` (^4.2.0)
- **Tác dụng**: Resolve TypeScript path mappings trong runtime.
- **Tại sao dùng**: Cần sử dụng path aliases (như `@/`) trong runtime và tests.
- **Lợi ích**:
  - Hỗ trợ path aliases trong runtime
  - Cần cho Jest và ts-node
  - Clean imports

#### `source-map-support` (^0.5.21)
- **Tác dụng**: Hỗ trợ source maps trong Node.js để stack traces chính xác hơn.
- **Tại sao dùng**: Cần stack traces chỉ đến source TypeScript thay vì compiled JavaScript.
- **Lợi ích**:
  - Better error messages
  - Debug dễ hơn
  - Stack traces chính xác

---

### Code Quality & Linting

#### `eslint` (^9.18.0)
- **Tác dụng**: Linter và code quality tool cho JavaScript/TypeScript.
- **Tại sao dùng**: Cần enforce coding standards và tìm bugs sớm.
- **Lợi ích**:
  - Tìm bugs và code smells
  - Enforce coding standards
  - Auto-fix nhiều issues
  - Plugin ecosystem lớn

#### `typescript-eslint` (^8.20.0)
- **Tác dụng**: ESLint rules và parser cho TypeScript.
- **Tại sao dùng**: Cần lint TypeScript code với type-aware rules.
- **Lợi ích**:
  - TypeScript-specific linting rules
  - Type-aware linting
  - Better error messages
  - Recommended rule sets

#### `@eslint/eslintrc` (^3.2.0)
- **Tác dụng**: ESLint configuration utilities.
- **Tại sao dùng**: Cần cho ESLint flat config format mới.
- **Lợi ích**:
  - Hỗ trợ flat config
  - Migration từ legacy config

#### `@eslint/js` (^9.18.0)
- **Tác dụng**: Core ESLint rules và recommended configurations.
- **Tại sao dùng**: Cần base rules cho JavaScript/TypeScript.
- **Lợi ích**:
  - Recommended rules
  - Best practices
  - Core linting rules

#### `eslint-config-prettier` (^10.0.1)
- **Tác dụng**: Tắt các ESLint rules conflict với Prettier.
- **Tại sao dùng**: Dùng Prettier cho formatting, cần tắt formatting rules trong ESLint.
- **Lợi ích**:
  - Tránh conflicts giữa ESLint và Prettier
  - Prettier handle formatting, ESLint handle logic
  - Clean configuration

#### `eslint-plugin-prettier` (^5.2.2)
- **Tác dụng**: Chạy Prettier như một ESLint rule.
- **Tại sao dùng**: Cần Prettier formatting errors hiển thị như ESLint errors.
- **Lợi ích**:
  - Unified error reporting
  - Auto-fix trong ESLint
  - Consistent workflow

#### `prettier` (^3.4.2)
- **Tác dụng**: Code formatter tự động cho JavaScript/TypeScript/CSS/JSON.
- **Tại sao dùng**: Cần consistent code formatting trong team.
- **Lợi ích**:
  - Automatic code formatting
  - Consistent style
  - Support nhiều languages
  - Configurable

#### `globals` (^16.0.0)
- **Tác dụng**: Global variables definitions cho ESLint.
- **Tại sao dùng**: Cần define globals (như `process`, `Buffer`) cho ESLint.
- **Lợi ích**:
  - Define globals cho ESLint
  - Tránh "undefined variable" errors
  - Node.js, browser globals

---

### Testing

#### `jest` (^29.7.0)
- **Tác dụng**: JavaScript testing framework, phổ biến và mạnh mẽ.
- **Tại sao dùng**: Cần testing framework với nhiều features và good TypeScript support.
- **Lợi ích**:
  - Fast và reliable
  - Snapshot testing
  - Code coverage
  - Mocking mạnh mẽ
  - Parallel test execution

#### `ts-jest` (^29.2.5)
- **Tác dụng**: TypeScript preprocessor cho Jest.
- **Tại sao dùng**: Cần Jest compile TypeScript files trước khi test.
- **Lợi ích**:
  - TypeScript support trong Jest
  - Type checking trong tests
  - Source maps
  - Fast compilation

#### `supertest` (^7.0.0)
- **Tác dụng**: HTTP assertion library để test API endpoints.
- **Tại sao dùng**: Cần test HTTP endpoints một cách dễ dàng.
- **Lợi ích**:
  - Test HTTP requests/responses
  - Chaining assertions
  - Easy integration với Jest
  - Hỗ trợ cookies, headers

---

### Type Definitions

#### `@types/express` (^5.0.0)
- **Tác dụng**: TypeScript type definitions cho Express.js.
- **Tại sao dùng**: Cần type safety khi làm việc với Express.
- **Lợi ích**:
  - Type safety cho Express
  - Auto-completion
  - Better IDE support

#### `@types/node` (^22.10.7)
- **Tác dụng**: TypeScript type definitions cho Node.js APIs.
- **Tại sao dùng**: Cần types cho Node.js built-in modules và globals.
- **Lợi ích**:
  - Type safety cho Node.js APIs
  - Process, Buffer, FileSystem types
  - Standard library types

#### `@types/jest` (^29.5.14)
- **Tác dụng**: TypeScript type definitions cho Jest.
- **Tại sao dùng**: Cần type safety cho Jest APIs và matchers.
- **Lợi ích**:
  - Type safety cho Jest
  - Auto-completion cho matchers
  - Better test writing experience

#### `@types/supertest` (^6.0.2)
- **Tác dụng**: TypeScript type definitions cho Supertest.
- **Tại sao dùng**: Cần type safety khi test HTTP endpoints.
- **Lợi ích**:
  - Type safety cho Supertest
  - Auto-completion
  - Better test writing

---

### Schema Validation

#### `zod` (^4.1.12)
- **Tác dụng**: TypeScript-first schema validation library.
- **Tại sao dùng**: Cần validation mạnh mẽ với type inference tự động.
- **Lợi ích**:
  - Type inference từ schema
  - Validation mạnh mẽ
  - Có thể dùng chung frontend/backend
  - Better error messages
  - Composable schemas

---

### Environment Variables

#### `cross-env` (^10.1.0)
- **Tác dụng**: Set environment variables cross-platform (Windows, Linux, macOS).
- **Tại sao dùng**: Windows và Unix có syntax khác nhau cho environment variables, cần tool này để consistent.
- **Lợi ích**:
  - Cross-platform compatibility
  - Consistent scripts
  - Không cần viết scripts riêng cho mỗi OS

---

## 📊 Tổng Kết

### Kiến Trúc Tổng Thể

Dự án này sử dụng một stack hiện đại và mạnh mẽ:

1. **Framework**: NestJS - Enterprise-grade Node.js framework
2. **Database**: Prisma ORM - Type-safe database access
3. **Caching**: Redis (ioredis) + Cache Manager
4. **Validation**: Class Validator + Zod (dual approach)
5. **Security**: Helmet, CSURF, Rate Limiting
6. **Documentation**: Swagger/OpenAPI
7. **Logging**: Pino (high-performance)
8. **Testing**: Jest + Supertest
9. **Code Quality**: ESLint + Prettier + TypeScript

### Lợi Ích Tổng Thể

- ✅ **Type Safety**: TypeScript + Prisma + Zod đảm bảo type safety end-to-end
- ✅ **Performance**: SWC compiler, Pino logger, Redis caching
- ✅ **Security**: Helmet, CSURF, Rate Limiting, Validation
- ✅ **Developer Experience**: Hot reload, code generation, auto-documentation
- ✅ **Maintainability**: Clean architecture, testing, linting, formatting
- ✅ **Scalability**: Modular design, caching, rate limiting, health checks

---

*Tài liệu này được tạo tự động dựa trên package.json của dự án LE Backend.*

