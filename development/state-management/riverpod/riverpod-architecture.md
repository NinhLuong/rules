# Riverpod Architecture Guide

## Table of Contents
1. [Overview](#overview)
2. [Clean Architecture Layers](#clean-architecture-layers)
3. [Advanced Architecture: Modular Monorepo](#advanced-architecture-modular-monorepo)

---

## Overview

This document defines architectural best practices and conventions for Flutter projects using **Riverpod** for state management. The goal is to ensure code quality, maintainability, and scalability across teams.

### Why Riverpod?

- **Compile-time safety**: Catches provider access errors at compile time
- **No BuildContext required**: Access providers anywhere in the app
- **Excellent testing**: Easy to override providers for testing
- **Auto-disposal**: Automatic memory management with autoDispose
- **Developer experience**: Great tooling and debugging support
- **Performance**: Fine-grained reactivity and selective rebuilds

---

## Clean Architecture Layers

Even if your folder names do not explicitly use `domain`, `data`, or `presentation`, these layers exist logically in your codebase. Organizing by feature or by layer is both acceptable, as long as you respect the **Dependency Rule**.

### Data Layer ("How")

This layer answers: **How is data fetched or stored?** It contains all implementation details and external dependencies.

**Components:**
- **Repository Implementations:** Concrete classes implementing domain repository interfaces as providers (e.g., `authRepositoryProvider`)
- **Data Sources:** Provider-based classes responsible for interacting with a single data source (e.g., `userRemoteDataSourceProvider`, `userLocalDataSourceProvider`)
- **DTOs (Data Transfer Objects):** Models for parsing and serializing data from APIs (e.g., `UserDto`)
- **Dependencies:** Uses packages like Dio, Hive, etc. No other layer depends on Data (except for DI setup)

### Domain Layer ("What")

This layer answers: **What can the app do?** It is the core of your business logic and is independent of frameworks and tools.

**Components:**
- **Entities:** Pure Dart objects representing core business concepts (e.g., `User`)
- **Repository Interfaces:** Abstract classes defining contracts for data access (e.g., `abstract class AuthRepository`)
- **Use Cases:** Provider-based classes encapsulating specific business actions (e.g., `loginUseCaseProvider`). In small/medium apps, UI providers may call repository methods directly instead of separate use cases
- **Dependencies:** No dependencies on other layers or frameworks

### Presentation Layer ("Show")

This layer answers: **What is displayed and how does the user interact?**

**Components:**
- **UI (Views):** Widgets and pages using `ConsumerWidget` or `HookConsumerWidget`
- **State Management:** StateNotifierProvider, Provider, and their States. Providers interact with the Domain layer and expose state to the UI

### Example Folder Structure (Layered)

```text
lib/
├── data/
│   ├── datasources/
│   │   ├── user_remote_datasource.dart
│   │   └── user_local_datasource.dart
│   ├── models/  # DTOs
│   │   └── user_dto.dart
│   ├── providers/
│   │   ├── datasource_providers.dart
│   │   └── repository_providers.dart
│   └── repositories/
│       └── user_repository_impl.dart
│
├── domain/
│   ├── entities/
│   │   └── user.dart
│   ├── providers/
│   │   ├── repository_providers.dart
│   │   └── usecase_providers.dart
│   ├── repositories/
│   │   └── user_repository.dart # Abstract class
│   └── usecases/
│       └── login_usecase.dart
│
└── presentation/
    ├── pages/
    │   └── login/
    │       └── login_page.dart
    ├── providers/
    │   ├── ui_providers.dart
    │   └── viewmodel_providers.dart
    ├── notifiers/
    │   ├── login_notifier.dart
    │   └── login_state.dart
    └── widgets/
        └── common_button.dart
```

### Example Folder Structure (Feature-Based)

```text
lib/
├── features/
│   ├── auth/
│   │   ├── data/
│   │   │   ├── datasources/
│   │   │   ├── models/
│   │   │   ├── providers/
│   │   │   └── repositories/
│   │   ├── domain/
│   │   │   ├── entities/
│   │   │   ├── providers/
│   │   │   ├── repositories/
│   │   │   └── usecases/
│   │   └── presentation/
│   │       ├── notifiers/
│   │       ├── providers/
│   │       ├── pages/
│   │       └── widgets/
│   └── home/
│       ├── data/
│       ├── domain/
│       └── presentation/
└── shared/
    ├── data/
    ├── domain/
    └── presentation/
```

### Dependency Rule

The most important rule is to respect the **Dependency Rule**:

**Presentation → Domain ← Data**

This ensures a clean, maintainable architecture regardless of folder naming:
- **Presentation layer** can depend on Domain layer
- **Data layer** can depend on Domain layer  
- **Domain layer** cannot depend on any other layer
- **Data and Presentation** layers cannot depend on each other directly

---

## Advanced Architecture: Modular Monorepo

For large-scale projects with multiple teams, consider a modular monorepo structure where each feature is a separate package. This approach improves maintainability, enables team autonomy, and supports better testing and deployment strategies.

### Monorepo Structure

```
my_app/
├── packages/
│   ├── auth/                    # Authentication module
│   │   ├── lib/
│   │   │   ├── data/
│   │   │   ├── domain/
│   │   │   ├── presentation/
│   │   │   └── module.dart      # Module exports
│   │   └── pubspec.yaml
│   ├── user/                    # User management module
│   │   ├── lib/
│   │   │   ├── data/
│   │   │   ├── domain/
│   │   │   ├── presentation/
│   │   │   └── module.dart
│   │   └── pubspec.yaml
│   ├── dashboard/               # Dashboard module
│   │   ├── lib/
│   │   │   ├── data/
│   │   │   ├── domain/
│   │   │   ├── presentation/
│   │   │   └── module.dart
│   │   └── pubspec.yaml
│   └── shared/                  # Shared utilities
│       ├── lib/
│       │   ├── constants/
│       │   ├── utils/
│       │   ├── widgets/
│       │   └── core/
│       └── pubspec.yaml
├── lib/                         # Main app
│   ├── app.dart
│   └── main.dart
└── pubspec.yaml
```

### Module Package Structure

Each module follows Clean Architecture internally with Riverpod providers:

```dart
// packages/auth/lib/module.dart
library auth_module;

// Data layer exports
export 'data/providers/datasource_providers.dart';
export 'data/providers/repository_providers.dart';

// Domain layer exports
export 'domain/entities/user.dart';
export 'domain/providers/repository_providers.dart';
export 'domain/providers/usecase_providers.dart';

// Presentation layer exports
export 'presentation/providers/auth_providers.dart';
export 'presentation/notifiers/auth_notifier.dart';
export 'presentation/pages/login_page.dart';
export 'presentation/widgets/auth_widgets.dart';
```

### Cross-Module Dependencies

**Guidelines:**
- Shared providers are defined in the `shared` package
- Feature modules can depend on `shared` but not on each other directly
- Use provider overrides to manage cross-module dependencies

```dart
// shared/lib/providers/app_providers.dart
final restClientProvider = Provider<RestClient>((ref) {
  return RestClient();
});

final storageProvider = Provider<Storage>((ref) {
  return HiveStorage();
});

// auth/lib/data/providers/repository_providers.dart
final authRepositoryProvider = Provider.autoDispose<AuthRepository>((ref) {
  return AuthRepositoryImpl(
    restClient: ref.read(restClientProvider),
    storage: ref.read(storageProvider),
  );
});

// Main app provider overrides
final overrides = [
  // Override shared providers if needed
  restClientProvider.overrideWith((ref) => ProductionRestClient()),
];
```

### Provider Scope Management

**Module-level providers:**
- Use `autoDispose` for feature-specific providers
- Keep shared infrastructure providers without `autoDispose`
- Use `family` modifiers for parameterized providers

```dart
// Feature-specific (auto-dispose)
final userProfileProvider = StateNotifierProvider.autoDispose<UserProfileNotifier, UserProfileState>((ref) {
  return UserProfileNotifier(ref.read(userRepositoryProvider));
});

// Shared infrastructure (persistent)
final httpClientProvider = Provider<Dio>((ref) {
  return Dio();
});

// Parameterized providers
final userByIdProvider = FutureProvider.family.autoDispose<User, String>((ref, userId) {
  return ref.read(userRepositoryProvider).getUserById(userId);
});
```

### Testing in Modular Architecture

```dart
// Test setup with module overrides
testWidgets('auth module integration test', (tester) async {
  await tester.pumpWidget(
    ProviderScope(
      overrides: [
        // Override only the providers needed for this test
        authRepositoryProvider.overrideWith((ref) => MockAuthRepository()),
        restClientProvider.overrideWith((ref) => MockRestClient()),
      ],
      child: AuthModule(),
    ),
  );
  
  // Test implementation
});
```

This modular approach with Riverpod provides:
- **Clear boundaries** between features
- **Easy testing** with provider overrides  
- **Independent deployment** of modules
- **Team autonomy** for feature development
- **Compile-time safety** across module boundaries 


## Ultra-Advanced Architecture: Micro-App Architecture

Micro-App architecture (often referred to as Micro-Frontends in mobile) takes modularization to the extreme. In this model, features are not just packages; they are **independent applications** that can be developed, tested, and versioned in completely separate repositories.

### The Micro-App Ecosystem

In a Micro-App setup, the project is split into three distinct categories:

1. **The Shell App (Host):** The main entry point. It handles global navigation, theme configuration, and orchestrates the lifecycle of Micro-Apps.
2. **Micro-Apps (Feature Apps):** Independent business units (e.g., "Payments", "Shopping", "Profile"). They can run as standalone apps during development.
3. **Core/Common Library:** A shared foundation for UI Kits, Networking, and State Management utilities (Riverpod base configurations).

### Project Structure (Multi-Repo)

Unlike a Monorepo, each Micro-App typically has its own lifecycle:

```text
/repository-shell-app
  ├── lib/main.dart (Global ProviderScope)
  └── pubspec.yaml (Depends on Micro-Apps via Git or Private Pub Server)

/repository-payment-app
  ├── example/ (Standalone runner for Payment team)
  ├── lib/ (Feature logic + Providers)
  └── pubspec.yaml

/repository-core-ui
  ├── lib/ (Design system, Theme providers)
  └── pubspec.yaml

```

### Riverpod in Micro-Apps: The Communication Challenge

The biggest challenge in Micro-Apps is **State Isolation**. Since Micro-Apps are developed independently, they must communicate without tight coupling.

#### 1. Contract-Based Dependency Injection

Micro-Apps should never depend on each other. Instead, they depend on **Abstract Interfaces** defined in a "Shared Contract" layer.

```dart
// In shared_contracts package
abstract class UserSession {
  String? get userId;
}
final userSessionProvider = Provider<UserSession>((ref) => throw UnimplementedError());

// In Shell App (Main)
final userSessionImplementationProvider = Provider<UserSession>((ref) => MyUserSessionImpl());

// Overriding in Shell App's ProviderScope
ProviderScope(
  overrides: [
    userSessionProvider.overrideWith((ref) => ref.read(userSessionImplementationProvider)),
  ],
  child: const MyApp(),
)

```

#### 2. Cross-App Navigation via Deep Linking

To navigate from the *Payment Micro-App* to the *Support Micro-App*, use a URL-based routing system (like `go_router`) rather than direct class references.

```dart
// Inside Payment Micro-App
ref.read(routerProvider).push('/support/ticket/123'); 
// The Shell App handles where this route leads.

```

### Strategic Riverpod Scoping

To prevent one Micro-App from accidentally breaking another, use **Nested ProviderScopes** if necessary, though a single root `ProviderScope` is preferred for simplicity unless memory management for specific modules is critical.

* **Global Scope:** Authentication, Theme, User Profile.
* **Micro-App Scope:** Feature-specific states (Cart, Payment Flow).

> **Important:** When using Micro-Apps, ensure all teams agree on a single version of Riverpod to avoid "Dependency Hell" (version mismatch in the final binary).

### Comparison: Why Choose Micro-App?

| Feature | Modular Monorepo | Micro-App Architecture |
| --- | --- | --- |
| **Repo Strategy** | Single Repository | Multiple Repositories |
| **Team Size** | 2–5 Teams | 10+ Teams |
| **Build Time** | Increases with app size | Faster (Build only your Micro-App) |
| **Refactoring** | Easy (IDE handles all) | Hard (Requires cross-repo coordination) |
| **Best For** | Most Enterprise Apps | Super-Apps (Grab, Shopee, WeChat) |

### Implementation Checklist

* [ ] **Melos or Mason:** Use Melos for local development if you use a Monorepo-Micro-App hybrid, or Mason for templating new Micro-Apps.
* [ ] **Private Pub Server:** Use `bytebeam` or `pub.dev` private to host Micro-App packages.
* [ ] **CI/CD:** Each Micro-App must have its own pipeline for unit and integration testing.
* [ ] **Contract Registry:** A shared package where all interfaces and global Providers are defined.
