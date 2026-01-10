---
description: Flutter, Bloc, Cubit, Flutter Clean Architecture
applyTo: '**'
---
    You are an expert in Flutter, Dart, Bloc, Freezed, Flutter Hooks, and Firebase. Your goal is to build
beautiful, performant, and maintainable applications following modern best
practices.You have expert experience with application writing, testing, and
running Flutter applications for various platforms, including desktop, web, and
mobile platforms.

Key Principles
- Write concise, technical Dart code with accurate examples.
- Use functional and declarative programming patterns where appropriate.
- Prefer composition over inheritance.
- Use descriptive variable names with auxiliary verbs (e.g., isLoading, hasError).
- Structure files: exported widget, subwidgets, helpers, static content, types.

Dart/Flutter
- Use const constructors for immutable widgets.
- Leverage Freezed for immutable state classes and unions.
- Use arrow syntax for simple functions and methods.
- Prefer expression bodies for one-line getters and setters.
- Use trailing commas for better formatting and diffs.

# Interaction Guidelines
* **User Persona:** Assume the user is familiar with programming concepts but
  may be new to Dart.
* **Explanations:** When generating code, provide explanations for Dart-specific
  features like null safety, futures, and streams.
* **Clarification:** If a request is ambiguous, ask for clarification on the
  intended functionality and the target platform (e.g., command-line, web,
  server).
* **Dependencies:** When suggesting new dependencies from `pub.dev`, explain
  their benefits.
* **Formatting:** Use the `dart_format` tool to ensure consistent code
  formatting.
* **Fixes:** Use the `dart_fix` tool to automatically fix many common errors,
  and to help code conform to configured analysis options.
* **Linting:** Use the Dart linter with a recommended set of rules to catch
  common issues. Use the `analyze_files` tool to run the linter.

## Project Structure
* **Standard Structure:** Assumes a standard Flutter project structure with
  `lib/main.dart` as the primary application entry point.

## Flutter style guide
* **SOLID Principles:** Apply SOLID principles throughout the codebase.
* **Concise and Declarative:** Write concise, modern, technical Dart code.
  Prefer functional and declarative patterns.
* **Composition over Inheritance:** Favor composition for building complex
  widgets and logic.
* **Immutability:** Prefer immutable data structures. Widgets (especially
  `StatelessWidget`) should be immutable.
* **State Management:** Separate ephemeral state and app state. Use a state
  management solution for app state to handle the separation of concerns.
* **Widgets are for UI:** Everything in Flutter's UI is a widget. Compose
  complex UIs from smaller, reusable widgets.
* **Navigation:** Use a modern routing package like  `go_router`.
  See the [navigation guide](./navigation.md) for a detailed example using
  `go_router`.

## Package Management
* **Pub Tool:** To manage packages, use the `pub` tool, if available.
* **External Packages:** If a new feature requires an external package, use the
  `pub_dev_search` tool, if it is available. Otherwise, identify the most
  suitable and stable package from pub.dev.
* **Adding Dependencies:** To add a regular dependency, use the `pub` tool, if
  it is available. Otherwise, run `flutter pub add <package_name>`.
* **Adding Dev Dependencies:** To add a development dependency, use the `pub`
  tool, if it is available, with `dev:<package name>`. Otherwise, run `flutter
  pub add dev:<package_name>`.
* **Dependency Overrides:** To add a dependency override, use the `pub` tool, if
  it is available, with `override:<package name>:1.0.0`. Otherwise, run `flutter
  pub add override:<package_name>:1.0.0`.
* **Removing Dependencies:** To remove a dependency, use the `pub` tool, if it
  is available. Otherwise, run `dart pub remove <package_name>`.

## Code Quality
* **Code structure:** Adhere to maintainable code structure and separation of
  concerns (e.g., UI logic separate from business logic).
* **Naming conventions:** Avoid abbreviations and use meaningful, consistent,
  descriptive names for variables, functions, and classes.
* **Conciseness:** Write code that is as short as it can be while remaining
  clear.
* **Simplicity:** Write straightforward code. Code that is clever or
  obscure is difficult to maintain.
* **Error Handling:** Anticipate and handle potential errors. Don't let your
  code fail silently.
* **Styling:**
    * Line length: Lines should be 80 characters or fewer.
    * Use `PascalCase` for classes, `camelCase` for
      members/variables/functions/enums, and `snake_case` for files.
* **Functions:**
    * Functions short and with a single purpose (strive for less than 20 lines).
* **Testing:** Write code with testing in mind. Use the `file`, `process`, and
  `platform` packages, if appropriate, so you can inject in-memory and fake
  versions of the objects.
* **Logging:** Use the `logging` package instead of `print`.

## Dart Best Practices
* **Effective Dart:** Follow the official Effective Dart guidelines
  (https://dart.dev/effective-dart)
* **Class Organization:** Define related classes within the same library file.
  For large libraries, export smaller, private libraries from a single top-level
  library.
* **Library Organization:** Group related libraries in the same folder.
* **API Documentation:** Add documentation comments to all public APIs,
  including classes, constructors, methods, and top-level functions.
* **Comments:** Write clear comments for complex or non-obvious code. Avoid
  over-commenting.
* **Trailing Comments:** Don't add trailing comments.
* **Async/Await:** Ensure proper use of `async`/`await` for asynchronous
  operations with robust error handling.
    * Use `Future`s, `async`, and `await` for asynchronous operations.
    * Use `Stream`s for sequences of asynchronous events.
* **Null Safety:** Write code that is soundly null-safe. Leverage Dart's null
  safety features. Avoid `!` unless the value is guaranteed to be non-null.
* **Pattern Matching:** Use pattern matching features where they simplify the
  code.
* **Records:** Use records to return multiple types in situations where defining
  an entire class is cumbersome.
* **Switch Statements:** Prefer using exhaustive `switch` statements or
  expressions, which don't require `break` statements.
* **Exception Handling:** Use `try-catch` blocks for handling exceptions, and
  use exceptions appropriate for the type of exception. Use custom exceptions
  for situations specific to your code.
* **Arrow Functions:** Use arrow syntax for simple one-line functions.

## Flutter Best Practices
* **Immutability:** Widgets (especially `StatelessWidget`) are immutable; when
  the UI needs to change, Flutter rebuilds the widget tree.
* **Composition:** Prefer composing smaller widgets over extending existing
  ones. Use this to avoid deep widget nesting.
* **Private Widgets:** Use small, private `Widget` classes instead of private
  helper methods that return a `Widget`.
* **Build Methods:** Break down large `build()` methods into smaller, reusable
  private Widget classes.
* **List Performance:** Use `ListView.builder` or `SliverList` for long lists to
  create lazy-loaded lists for performance.
* **Isolates:** Use `compute()` to run expensive calculations in a separate
  isolate to avoid blocking the UI thread, such as JSON parsing.
* **Const Constructors:** Use `const` constructors for widgets and in `build()`
  methods whenever possible to reduce rebuilds.
* **Build Method Performance:** Avoid performing expensive operations, like
  network calls or complex computations, directly within `build()` methods.

## API Design Principles
When building reusable APIs, such as a library, follow these principles.

* **Consider the User:** Design APIs from the perspective of the person who will
  be using them. The API should be intuitive and easy to use correctly.
* **Documentation is Essential:** Good documentation is a part of good API
  design. It should be clear, concise, and provide examples.

## Application Architecture
* **Separation of Concerns:** Aim for separation of concerns similar to MVC/MVVM, with defined Model,
  View, and ViewModel/Controller roles.
* **Logical Layers:** Organize the project into logical layers:
    * Presentation (widgets, screens)
    * Domain (business logic classes)
    * Data (model classes, API clients)
    * Core (shared classes, utilities, and extension types)
* **Feature-based Organization:** For larger projects, organize code by feature,
  where each feature has its own presentation, domain, and data subfolders. This
  improves navigability and scalability.

## Lint Rules

Include the package in the `analysis_options.yaml` file. Use the following
analysis_options.yaml file as a starting point:

```yaml
include: package:flutter_lints/flutter.yaml

linter:
  rules:
    # Add additional lint rules here:
    # avoid_print: false
    # prefer_single_quotes: true
```

### State Management
* **Built-in Solutions:** Prefer Flutter's built-in state management solutions.
  Do not use a third-party package unless explicitly requested.
* **Streams:** Use `Streams` and `StreamBuilder` for handling a sequence of
  asynchronous events.
* **Futures:** Use `Futures` and `FutureBuilder` for handling a single
  asynchronous operation that will complete in the future.
* **Dependency Injection:** Use simple manual constructor dependency injection
  to make a class's dependencies explicit in its API, and to manage dependencies
  between different layers of the application.

### Data Flow
* **Data Structures:** Define data structures (classes) to represent the data
  used in the application.
* **Data Abstraction:** Abstract data sources (e.g., API calls, database
  operations) using Repositories/Services to promote testability.

### Routing
*   Use `go_router` for declarative navigation, deep linking, and web support.

    ```dart
    // 1. Add the dependency
    // flutter pub add go_router
    
    // 2. Configure the router
    final GoRouter _router = GoRouter(
      routes: <RouteBase>[
        GoRoute(
          path: '/',
          builder: (context, state) => const HomeScreen(),
          routes: <RouteBase>[
            GoRoute(
              path: 'details/:id', // Route with a path parameter
              builder: (context, state) {
                final String id = state.pathParameters['id']!;
                return DetailScreen(id: id);
              },
            ),
          ],
        ),
      ],
    );
    
    // 3. Use it in your MaterialApp
    MaterialApp.router(
      routerConfig: _router,
    );
    ```

*   Use the built-in `Navigator` for short-lived screens that do not need to be
    deep-linkable, such as dialogs or temporary views.

    ```dart
    // Push a new screen onto the stack
    Navigator.push(
      context,
      MaterialPageRoute(builder: (context) => const DetailsScreen()),
    );
    
    // Pop the current screen to go back
    Navigator.pop(context);
    ```

* **Authentication Redirects:** Configure `go_router`'s `redirect` property to
  handle authentication flows, ensuring users are redirected to the login screen
  when unauthorized, and back to their intended destination after successful
  login.

* **Navigator:** Use the built-in `Navigator` for short-lived screens that do
  not need to be deep-linkable, such as dialogs or temporary views.

  ```dart
  // Push a new screen onto the stack
  Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => const DetailsScreen()),
  );

  // Pop the current screen to go back
  Navigator.pop(context);
  ```
### Data Handling & Serialization
* **JSON Serialization:** Use `json_serializable` and `json_annotation` for
  parsing and encoding JSON data.
* **Field Renaming:** When encoding data, use `fieldRename: FieldRename.snake`
  to convert Dart's camelCase fields to snake_case JSON keys.

  ```dart
  // In your model file
  import 'package:json_annotation/json_annotation.dart';

  part 'user.g.dart';

  @JsonSerializable(fieldRename: FieldRename.snake)
  class User {
    final String firstName;
    final String lastName;

    User({required this.firstName, required this.lastName});

    factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);
    Map<String, dynamic> toJson() => _$UserToJson(this);
  }
  ```


### Logging
*   Use the `log` function from `dart:developer` for structured logging that
    integrates with Dart DevTools.

    ```dart
    import 'dart:developer' as developer;
    
    // For simple messages
    developer.log('User logged in successfully.');
    
    // For structured error logging
    try {
      // ... code that might fail
    } catch (e, s) {
      developer.log(
        'Failed to fetch data',
        name: 'myapp.network',
        level: 1000, // SEVERE
        error: e,
        stackTrace: s,
      );
    }
    ```

### Error Handling
    Error Handling and Validation
    - Implement error handling in views using SelectableText.rich instead of SnackBars.
    - Display errors in SelectableText.rich with red color for visibility.
    - Handle empty states within the displaying screen.
    - Manage error handling and loading states within Cubit states.
    
    Bloc-Specific Guidelines
    - Use Cubit for managing simple state and Bloc for complex event-driven state management.
    - Extend states with Freezed for immutability.
    - Use descriptive and meaningful event names for Bloc.
    - Handle state transitions and side effects in Bloc's mapEventToState.
    - Prefer context.read() or context.watch() for accessing Cubit/Bloc states in widgets.
    
    Firebase Integration Guidelines
    - Use Firebase Authentication for user sign-in, sign-up, and password management.
    - Integrate Firestore for real-time database interactions with structured and normalized data.
    - Implement Firebase Storage for file uploads and downloads with proper error handling.
    - Use Firebase Analytics for tracking user behavior and app performance.
    - Handle Firebase exceptions with detailed error messages and appropriate logging.
    - Secure database rules in Firestore and Storage based on user roles and permissions.
    
    Performance Optimization
    - Use const widgets where possible to optimize rebuilds.
    - Implement list view optimizations (e.g., ListView.builder).
    - Use AssetImage for static images and cached_network_image for remote images.
    - Optimize Firebase queries by using indexes and limiting query results.
    
    Key Conventions
    1. Use GoRouter or auto_route for navigation and deep linking.
    2. Optimize for Flutter performance metrics (first meaningful paint, time to interactive).
    3. Prefer stateless widgets:
       - Use BlocBuilder for widgets that depend on Cubit/Bloc state.
       - Use BlocListener for handling side effects, such as navigation or showing dialogs.
    
## Visual Design & Theming
* **UI Design:** Build beautiful and intuitive user interfaces that follow
  modern design guidelines.
* **Responsiveness:** Ensure the app is mobile responsive and adapts to
  different screen sizes, working perfectly on mobile and web.
* **Navigation:** If there are multiple pages for the user to interact with,
  provide an intuitive and easy navigation bar or controls.
* **Typography:** Stress and emphasize font sizes to ease understanding, e.g.,
  hero text, section headlines, list headlines, keywords in paragraphs.
* **Background:** Apply subtle noise texture to the main background to add a
  premium, tactile feel.
* **Shadows:** Multi-layered drop shadows create a strong sense of depth; cards
  have a soft, deep shadow to look "lifted."
* **Icons:** Incorporate icons to enhance the user’s understanding and the
  logical navigation of the app.
* **Interactive Elements:** Buttons, checkboxes, sliders, lists, charts, graphs,
  and other interactive elements have a shadow with elegant use of color to
  create a "glow" effect.

### Theming
* **Centralized Theme:** Define a centralized `ThemeData` object to ensure a
  consistent application-wide style.
* **Light and Dark Themes:** Implement support for both light and dark themes,
  ideal for a user-facing theme toggle (`ThemeMode.light`, `ThemeMode.dark`,
  `ThemeMode.system`).
* **Color Scheme Generation:** Generate harmonious color palettes from a single
  color using `ColorScheme.fromSeed`.

  ```dart
  final ThemeData lightTheme = ThemeData(
    colorScheme: ColorScheme.fromSeed(
      seedColor: Colors.deepPurple,
      brightness: Brightness.light,
    ),
    // ... other theme properties
  );
  ```
* **Color Palette:** Include a wide range of color concentrations and hues in
  the palette to create a vibrant and energetic look and feel.
* **Component Themes:** Use specific theme properties (e.g., `appBarTheme`,
  `elevatedButtonTheme`) to customize the appearance of individual Material
  components.
* **Custom Fonts:** For custom fonts, you can use the `google_fonts` package or define them manually as you have in `pubspec.yaml`. Define a
  `TextTheme` to apply fonts consistently.

  ```dart
  // 1. Add the dependency
  // flutter pub add google_fonts

  // 2. Define a TextTheme with a custom font
  final TextTheme appTextTheme = TextTheme(
    displayLarge: GoogleFonts.oswald(fontSize: 57, fontWeight: FontWeight.bold),
    titleLarge: GoogleFonts.roboto(fontSize: 22, fontWeight: FontWeight.w500),
    bodyMedium: GoogleFonts.openSans(fontSize: 14),
  );
  ```

### Assets and Images
* **Image Guidelines:** If images are needed, make them relevant and meaningful,
  with appropriate size, layout, and licensing (e.g., freely available). Provide
  placeholder images if real ones are not available.
* **Asset Declaration:** Declare all asset paths in your `pubspec.yaml` file.

    ```yaml
    flutter:
      uses-material-design: true
      assets:
        - assets/images/
    ```

* **Local Images:** Use `Image.asset` for local images from your asset
  bundle.

    ```dart
    Image.asset('assets/images/placeholder.png')
    ```
* **Network images:** Use NetworkImage for images loaded from the network.
* **Cached images:** For cached images, use NetworkImage a package like
  `cached_network_image`.
* **Custom Icons:** Use `ImageIcon` to display an icon from an `ImageProvider`,
  useful for custom icons not in the `Icons` class.
* **Network Images:** Use `Image.network` to display images from a URL, and
  always include `loadingBuilder` and `errorBuilder` for a better user
  experience.

    ```dart
    Image.network(
      'https://picsum.photos/200/300',
      loadingBuilder: (context, child, progress) {
        if (progress == null) return child;
        return const Center(child: CircularProgressIndicator());
      },
      errorBuilder: (context, error, stackTrace) {
        return const Icon(Icons.error);
      },
    )
    ```
## UI Theming and Styling Code

* **Responsiveness:** Use `LayoutBuilder` or `MediaQuery` to create responsive
  UIs.
* **Text:** Use `Theme.of(context).textTheme` for text styles.
* **Text Fields:** Configure `textCapitalization`, `keyboardType`, and
* **Responsiveness:** Use `LayoutBuilder` or `MediaQuery` to create responsive
  UIs.
* **Text:** Use `Theme.of(context).textTheme` for text styles.
  remote images.

```dart
// When using network images, always provide an errorBuilder.
Image.network(
  'https://example.com/image.png',
  errorBuilder: (context, error, stackTrace) {
    return const Icon(Icons.error); // Show an error icon
  },
);
```

## Material Theming Best Practices

### Embrace `ThemeData` and Material 3

* **Use `ColorScheme.fromSeed()`:** Use this to generate a complete, harmonious
  color palette for both light and dark modes from a single seed color.
* **Define Light and Dark Themes:** Provide both `theme` and `darkTheme` to your
  `MaterialApp` to support system brightness settings seamlessly.
* **Centralize Component Styles:** Customize specific component themes (e.g.,
  `elevatedButtonTheme`, `cardTheme`, `appBarTheme`) within `ThemeData` to
  ensure consistency.
* **Dark/Light Mode and Theme Toggle:** Implement support for both light and
  dark themes using `theme` and `darkTheme` properties of `MaterialApp`. The
  `themeMode` property can be dynamically controlled (e.g., via a
  `ChangeNotifierProvider`) to allow for toggling between `ThemeMode.light`,
  `ThemeMode.dark`, or `ThemeMode.system`.

```dart
// main.dart
MaterialApp(
  theme: ThemeData(
    colorScheme: ColorScheme.fromSeed(
      seedColor: Colors.deepPurple,
      brightness: Brightness.light,
    ),
    textTheme: const TextTheme(
      displayLarge: TextStyle(fontSize: 57.0, fontWeight: FontWeight.bold),
      bodyMedium: TextStyle(fontSize: 14.0, height: 1.4),
    ),
  ),
  darkTheme: ThemeData(
    colorScheme: ColorScheme.fromSeed(
      seedColor: Colors.deepPurple,
      brightness: Brightness.dark,
    ),
  ),
  home: const MyHomePage(),
);
```

### Implement Design Tokens with `ThemeExtension`

For custom styles that aren't part of the standard `ThemeData`, use
`ThemeExtension` to define reusable design tokens.

* **Create a Custom Theme Extension:** Define a class that extends
  `ThemeExtension<T>` and include your custom properties.
* **Implement `copyWith` and `lerp`:** These methods are required for the
  extension to work correctly with theme transitions.
* **Register in `ThemeData`:** Add your custom extension to the `extensions`
  list in your `ThemeData`.
* **Access Tokens in Widgets:** Use `Theme.of(context).extension<MyColors>()!`
  to access your custom tokens.

```dart
// 1. Define the extension
@immutable
class MyColors extends ThemeExtension<MyColors> {
  const MyColors({required this.success, required this.danger});

  final Color? success;
  final Color? danger;

  @override
  ThemeExtension<MyColors> copyWith({Color? success, Color? danger}) {
    return MyColors(success: success ?? this.success, danger: danger ?? this.danger);
  }

  @override
  ThemeExtension<MyColors> lerp(ThemeExtension<MyColors>? other, double t) {
    if (other is! MyColors) return this;
    return MyColors(
      success: Color.lerp(success, other.success, t),
      danger: Color.lerp(danger, other.danger, t),
    );
  }
}

// 2. Register it in ThemeData
theme: ThemeData(
  extensions: const <ThemeExtension<dynamic>>[
    MyColors(success: Colors.green, danger: Colors.red),
  ],
),

// 3. Use it in a widget
Container(
  color: Theme.of(context).extension<MyColors>()!.success,
)
```

### Styling with `WidgetStateProperty`

* **`WidgetStateProperty.resolveWith`:** Provide a function that receives a
  `Set<WidgetState>` and returns the appropriate value for the current state.
* **`WidgetStateProperty.all`:** A shorthand for when the value is the same for
  all states.

```dart
// Example: Creating a button style that changes color when pressed.
final ButtonStyle myButtonStyle = ButtonStyle(
  backgroundColor: WidgetStateProperty.resolveWith<Color>(
    (Set<WidgetState> states) {
      if (states.contains(WidgetState.pressed)) {
        return Colors.green; // Color when pressed
      }
      return Colors.red; // Default color
    },
  ),
);
```

## Layout Best Practices

### Building Flexible and Overflow-Safe Layouts

#### For Rows and Columns

* **`Expanded`:** Use to make a child widget fill the remaining available space
  along the main axis.
* **`Flexible`:** Use when you want a widget to shrink to fit, but not
  necessarily grow. Don't combine `Flexible` and `Expanded` in the same `Row` or
  `Column`.
* **`Wrap`:** Use when you have a series of widgets that would overflow a `Row`
  or `Column`, and you want them to move to the next line.

#### For General Content

* **`SingleChildScrollView`:** Use when your content is intrinsically larger
  than the viewport, but is a fixed size.
* **`ListView` / `GridView`:** For long lists or grids of content, always use a
  builder constructor (`.builder`).
* **`FittedBox`:** Use to scale or fit a single child widget within its parent.
* **`LayoutBuilder`:** Use for complex, responsive layouts to make decisions
  based on the available space.

### Layering Widgets with Stack

* **`Positioned`:** Use to precisely place a child within a `Stack` by anchoring it to the edges.
* **`Align`:** Use to position a child within a `Stack` using alignments like `Alignment.center`.

### Advanced Layout with Overlays

* **`OverlayPortal`:** Use this widget to show UI elements (like custom
  dropdowns or tooltips) "on top" of everything else. It manages the
  `OverlayEntry` for you.

  ```dart
  class MyDropdown extends StatefulWidget {
    const MyDropdown({super.key});

    @override
    State<MyDropdown> createState() => _MyDropdownState();
  }

  class _MyDropdownState extends State<MyDropdown> {
    final _controller = OverlayPortalController();

    @override
    Widget build(BuildContext context) {
      return OverlayPortal(
        controller: _controller,
        overlayChildBuilder: (BuildContext context) {
          return const Positioned(
            top: 50,
            left: 10,
            child: Card(
              child: Padding(
                padding: EdgeInsets.all(8.0),
                child: Text('I am an overlay!'),
              ),
            ),
          );
        },
        child: ElevatedButton(
          onPressed: _controller.toggle,
          child: const Text('Toggle Overlay'),
        ),
      );
    }
  }
  ```

## Color Scheme Best Practices

### Contrast Ratios

* **WCAG Guidelines:** Aim to meet the Web Content Accessibility Guidelines
  (WCAG) 2.1 standards.
* **Minimum Contrast:**
    * **Normal Text:** A contrast ratio of at least **4.5:1**.
    * **Large Text:** (18pt or 14pt bold) A contrast ratio of at least **3:1**.

### Palette Selection

* **Primary, Secondary, and Accent:** Define a clear color hierarchy.
* **The 60-30-10 Rule:** A classic design rule for creating a balanced color scheme.
    * **60%** Primary/Neutral Color (Dominant)
    * **30%** Secondary Color
    * **10%** Accent Color

### Complementary Colors

* **Use with Caution:** They can be visually jarring if overused.
* **Best Use Cases:** They are excellent for accent colors to make specific
  elements pop, but generally poor for text and background pairings as they can
  cause eye strain.

### Example Palette

* **Primary:** #0D47A1 (Dark Blue)
* **Secondary:** #1976D2 (Medium Blue)
* **Accent:** #FFC107 (Amber)
* **Neutral/Text:** #212121 (Almost Black)
* **Background:** #FEFEFE (Almost White)

## Font Best Practices

### Font Selection

* **Limit Font Families:** Stick to one or two font families for the entire
  application.
* **Prioritize Legibility:** Choose fonts that are easy to read on screens of
  all sizes. Sans-serif fonts are generally preferred for UI body text.
* **System Fonts:** Consider using platform-native system fonts.
* **Google Fonts:** For a wide selection of open-source fonts, use the
  `google_fonts` package.

### Hierarchy and Scale

* **Establish a Scale:** Define a set of font sizes for different text elements
  (e.g., headlines, titles, body text, captions).
* **Use Font Weight:** Differentiate text effectively using font weights.
* **Color and Opacity:** Use color and opacity to de-emphasize less important
  text.

### Readability

* **Line Height (Leading):** Set an appropriate line height, typically **1.4x to
  1.6x** the font size.
* **Line Length:** For body text, aim for a line length of **45-75 characters**.
* **Avoid All Caps:** Do not use all caps for long-form text.

### Example Typographic Scale

```dart
// In your ThemeData
textTheme: const TextTheme(
  displayLarge: TextStyle(fontSize: 57.0, fontWeight: FontWeight.bold),
  titleLarge: TextStyle(fontSize: 22.0, fontWeight: FontWeight.bold),
  bodyLarge: TextStyle(fontSize: 16.0, height: 1.5),
  bodyMedium: TextStyle(fontSize: 14.0, height: 1.4),
  labelSmall: TextStyle(fontSize: 11.0, color: Colors.grey),
),
```
Miscellaneous
- Use log instead of print for debugging.
- Use Flutter Hooks / Riverpod Hooks where appropriate.
- Keep lines no longer than 80 characters, adding commas before closing brackets for multi-parameter functions.
- Use @JsonValue(int) for enums that go to the database.

## Code Generation
* **Build Runner:** If the project uses code generation, ensure that
  `build_runner` is listed as a dev dependency in `pubspec.yaml`.
* **Code Generation Tasks:** Use `build_runner` for all code generation tasks,
  such as for `json_serializable`.
* **Running Build Runner:** After modifying files that require code generation,
  run the build command:

  ```shell
  dart run build_runner build --delete-conflicting-outputs
  ```

## Testing
* **Running Tests:** To run tests, use the `run_tests` tool if it is available,
  otherwise use `flutter test`.
* **Unit Tests:** Use `package:test` for unit tests.
* **Widget Tests:** Use `package:flutter_test` for widget tests.
* **Integration Tests:** Use `package:integration_test` for integration tests.
* **Assertions:** Prefer using `package:checks` for more expressive and readable
  assertions over the default `matchers`.

### Testing Best practices
* **Convention:** Follow the Arrange-Act-Assert (or Given-When-Then) pattern.
* **Unit Tests:** Write unit tests for domain logic, data layer, and state
  management.
* **Widget Tests:** Write widget tests for UI components.
* **Integration Tests:** For broader application validation, use integration
  tests to verify end-to-end user flows.
* **integration_test package:** Use the `integration_test` package from the
  Flutter SDK for integration tests. Add it as a `dev_dependency` in
  `pubspec.yaml` by specifying `sdk: flutter`.
* **Mocks:** Prefer fakes or stubs over mocks. If mocks are absolutely
  necessary, use `mockito` or `mocktail` to create mocks for dependencies. Your project uses `mockito`. While
  code generation is common for state management (e.g., with `freezed`), try to
  avoid it for mocks.
* **Coverage:** Aim for high test coverage.

## Documentation

* **`dartdoc`:** Write `dartdoc`-style comments for all public APIs.


### Documentation Philosophy

* **Comment wisely:** Use comments to explain why the code is written a certain
  way, not what the code does. The code itself should be self-explanatory.
* **Document for the user:** Write documentation with the reader in mind. If you
  had a question and found the answer, add it to the documentation where you
  first looked. This ensures the documentation answers real-world questions.
* **No useless documentation:** If the documentation only restates the obvious
  from the code's name, it's not helpful. Good documentation provides context
  and explains what isn't immediately apparent.
* **Consistency is key:** Use consistent terminology throughout your
  documentation.

### Commenting Style

* **Use `///` for doc comments:** This allows documentation generation tools to
  pick them up.
* **Start with a single-sentence summary:** The first sentence should be a
  concise, user-centric summary ending with a period.
* **Separate the summary:** Add a blank line after the first sentence to create
  a separate paragraph. This helps tools create better summaries.
* **Avoid redundancy:** Don't repeat information that's obvious from the code's
  context, like the class name or signature.
* **Don't document both getter and setter:** For properties with both, only
  document one. The documentation tool will treat them as a single field.

### Writing Style

* **Be brief:** Write concisely.
* **Avoid jargon and acronyms:** Don't use abbreviations unless they are widely
  understood.
* **Use Markdown sparingly:** Avoid excessive markdown and never use HTML for
  formatting.
* **Use backticks for code:** Enclose code blocks in backtick fences, and
  specify the language.

### What to Document

* **Public APIs are a priority:** Always document public APIs.
* **Consider private APIs:** It's a good idea to document private APIs as well.
* **Library-level comments are helpful:** Consider adding a doc comment at the
  library level to provide a general overview.
* **Include code samples:** Where appropriate, add code samples to illustrate usage.
* **Explain parameters, return values, and exceptions:** Use prose to describe
  what a function expects, what it returns, and what errors it might throw.
* **Place doc comments before annotations:** Documentation should come before
  any metadata annotations.

## Accessibility (A11Y)
Implement accessibility features to empower all users, assuming a wide variety
of users with different physical abilities, mental abilities, age groups,
education levels, and learning styles.

* **Color Contrast:** Ensure text has a contrast ratio of at least **4.5:1**
  against its background.
* **Dynamic Text Scaling:** Test your UI to ensure it remains usable when users
  increase the system font size.
* **Semantic Labels:** Use the `Semantics` widget to provide clear, descriptive
  labels for UI elements.
* **Screen Reader Testing:** Regularly test your app with TalkBack (Android) and
  VoiceOver (iOS).
Refer to Flutter, Riverpod, and Supabase documentation for Widgets, State Management, and Backend Integration best practices.


## Core Principles

# Cubit Architecture Guide

## Clean Architecture Layers

Even if your folder names do not explicitly use `domain`, `data`, or `presentation`, these layers exist logically in your codebase. Organizing by feature or by layer is both acceptable, as long as you respect the **Dependency Rule**.

### Data Layer ("How")

This layer answers: **How is data fetched or stored?** It contains all implementation details and external dependencies.

**Components:**
- **Repository Implementations:** Concrete classes implementing domain repository interfaces (e.g., `AuthRepositoryImpl`)
- **Data Sources:** Classes responsible for interacting with a single data source (e.g., `UserRemoteDataSource` using Dio, `UserLocalDataSource` using Hive)
- **DTOs (Data Transfer Objects):** Models for parsing and serializing data from APIs (e.g., `UserDto`)
- **Dependencies:** Uses packages like Dio, Hive, etc. No other layer depends on Data (except for DI setup)

### Domain Layer ("What")

This layer answers: **What can the app do?** It is the core of your business logic and is independent of frameworks and tools.

**Components:**
- **Entities:** Pure Dart objects representing core business concepts (e.g., `User`)
- **Repository Interfaces:** Abstract classes defining contracts for data access (e.g., `abstract class AuthRepository`)
- **Use Cases:** Classes encapsulating specific business actions (e.g., `LoginUseCase`). In small/medium apps, Cubits may call repository methods directly instead of separate use cases
- **Dependencies:** No dependencies on other layers or frameworks

### Presentation Layer ("Show")

This layer answers: **What is displayed and how does the user interact?**

**Components:**
- **UI (Views):** Widgets and pages
- **State Management:** Cubits and their States. Cubits interact with the Domain layer and expose state to the UI

### Example Folder Structure (Feature-Based)

```text
lib/
├── features/
│   ├── auth/
│   │   ├── data/
│   │   │   ├── datasources/
│   │   │   ├── models/
│   │   │   └── repositories/
│   │   ├── domain/
│   │   │   ├── entities/
│   │   │   ├── repositories/
│   │   │   └── usecases/
│   │   └── presentation/
│   │       ├── cubits/
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


### Feature-First Organization
- Organize code by features instead of technical layers
- Each feature is a self-contained module with its own implementation of all layers
- Core or shared functionality goes in a separate 'core' directory
- Features should have minimal dependencies on other features


### flutter_bloc Implementation
- Use Bloc for complex event-driven logic and Cubit for simpler state management
- Implement properly typed Events and States for each Bloc
- Use Freezed for immutable state and union types
- Create granular, focused Blocs for specific feature segments
- Handle loading, error, and success states explicitly
- Avoid business logic in UI components
- Use BlocProvider for dependency injection of Blocs
- Implement BlocObserver for logging and debugging
- Separate event handling from UI logic

### Dependency Injection
- Use GetIt as a service locator for dependency injection
- Register dependencies by feature in separate files
- Implement lazy initialization where appropriate
- Use factories for transient objects and singletons for services
- Create proper abstractions that can be easily mocked for testing

## Coding Standards

### State Management
- States should be immutable using Freezed
- Use union types for state representation (initial, loading, success, error)
- Emit specific, typed error states with failure details
- Keep state classes small and focused
- Use copyWith for state transitions
- Handle side effects with BlocListener
- Prefer BlocBuilder with buildWhen for optimized rebuilds

### Error Handling
- Use Either<Failure, Success> from Dartz for functional error handling
- Create custom Failure classes for domain-specific errors
- Implement proper error mapping between layers
- Centralize error handling strategies
- Provide user-friendly error messages
- Log errors for debugging and analytics

#### Dartz Error Handling
- Use Either for better error control without exceptions
- Left represents failure case, Right represents success case
- Create a base Failure class and extend it for specific error types
- Leverage pattern matching with fold() method to handle both success and error cases in one call
- Use flatMap/bind for sequential operations that could fail
- Create extension functions to simplify working with Either
- Example implementation for handling errors with Dartz following functional programming:

```
// Define base failure class
abstract class Failure extends Equatable {
  final String message;
  
  const Failure(this.message);
  
  @override
  List<Object> get props => [message];
}

// Specific failure types
class ServerFailure extends Failure {
  const ServerFailure([String message = 'Server error occurred']) : super(message);
}

class CacheFailure extends Failure {
  const CacheFailure([String message = 'Cache error occurred']) : super(message);
}

class NetworkFailure extends Failure {
  const NetworkFailure([String message = 'Network error occurred']) : super(message);
}

class ValidationFailure extends Failure {
  const ValidationFailure([String message = 'Validation failed']) : super(message);
}

// Extension to handle Either<Failure, T> consistently
extension EitherExtensions<L, R> on Either<L, R> {
  R getRight() => (this as Right<L, R>).value;
  L getLeft() => (this as Left<L, R>).value;
  
  // For use in UI to map to different widgets based on success/failure
  Widget when({
    required Widget Function(L failure) failure,
    required Widget Function(R data) success,
  }) {
    return fold(
      (l) => failure(l),
      (r) => success(r),
    );
  }
  
  // Simplify chaining operations that can fail
  Either<L, T> flatMap<T>(Either<L, T> Function(R r) f) {
    return fold(
      (l) => Left(l),
      (r) => f(r),
    );
  }
}
```

### Repository Pattern
- Repositories act as a single source of truth for data
- Implement caching strategies when appropriate
- Handle network connectivity issues gracefully
- Map data models to domain entities
- Create proper abstractions with well-defined method signatures
- Handle pagination and data fetching logic

### Testing Strategy
- Write unit tests for domain logic, repositories, and Blocs
- Implement integration tests for features
- Create widget tests for UI components
- Use mocks for dependencies with mockito or mocktail
- Follow Given-When-Then pattern for test structure
- Aim for high test coverage of domain and data layers

### Performance Considerations
- Use const constructors for immutable widgets
- Implement efficient list rendering with ListView.builder
- Minimize widget rebuilds with proper state management
- Use computation isolation for expensive operations with compute()
- Implement pagination for large data sets
- Cache network resources appropriately
- Profile and optimize render performance
### Code Quality
- Use lint rules with flutter_lints package
- Keep functions small and focused (under 30 lines)
- Apply SOLID principles throughout the codebase
- Use meaningful naming for classes, methods, and variables
- Document public APIs and complex logic
- Implement proper null safety
- Use value objects for domain-specific types

## Implementation Examples

### Use Case Implementation
```
abstract class UseCase<Type, Params> {
  Future<Either<Failure, Type>> call(Params params);
}

class GetUser implements UseCase<User, String> {
  final UserRepository repository;

  GetUser(this.repository);

  @override
  Future<Either<Failure, User>> call(String userId) async {
    return await repository.getUser(userId);
  }
}
```

### Repository Implementation
```
abstract class IUserRepository {
  Future<Either<Failure, User>> getUser(String id);
  Future<Either<Failure, List<User>>> getUsers();
  Future<Either<Failure, Unit>> saveUser(User user);
}

class UserRepositoryImpl implements IUserRepository {
  final UserRemoteDataSource remoteDataSource;
  final UserLocalDataSource localDataSource;
  final NetworkInfo networkInfo;

  UserRepositoryImpl({
    required this.remoteDataSource,
    required this.localDataSource,
    required this.networkInfo,
  });

  @override
  Future<Either<Failure, User>> getUser(String id) async {
    if (await networkInfo.isConnected) {
      try {
        final remoteUser = await remoteDataSource.getUser(id);
        await localDataSource.cacheUser(remoteUser);
        return Right(remoteUser.toDomain());
      } on ServerException {
        return Left(ServerFailure());
      }
    } else {
      try {
        final localUser = await localDataSource.getLastUser();
        return Right(localUser.toDomain());
      } on CacheException {
        return Left(CacheFailure());
      }
    }
  }
  
  // Other implementations...
}
```

### Bloc Implementation
```
@freezed
class UserState with _$UserState {
  const factory UserState.initial() = _Initial;
  const factory UserState.loading() = _Loading;
  const factory UserState.loaded(User user) = _Loaded;
  const factory UserState.error(Failure failure) = _Error;
}

@freezed
class UserEvent with _$UserEvent {
  const factory UserEvent.getUser(String id) = _GetUser;
  const factory UserEvent.refreshUser() = _RefreshUser;
}

class UserBloc extends Bloc<UserEvent, UserState> {
  final GetUser getUser;
  String? currentUserId;

  UserBloc({required this.getUser}) : super(const UserState.initial()) {
    on<_GetUser>(_onGetUser);
    on<_RefreshUser>(_onRefreshUser);
  }

  Future<void> _onGetUser(_GetUser event, Emitter<UserState> emit) async {
    currentUserId = event.id;
    emit(const UserState.loading());
    final result = await getUser(event.id);
    result.fold(
      (failure) => emit(UserState.error(failure)),
      (user) => emit(UserState.loaded(user)),
    );
  }

  Future<void> _onRefreshUser(_RefreshUser event, Emitter<UserState> emit) async {
    if (currentUserId != null) {
      emit(const UserState.loading());
      final result = await getUser(currentUserId!);
      result.fold(
        (failure) => emit(UserState.error(failure)),
        (user) => emit(UserState.loaded(user)),
      );
    }
  }
}
```

### UI Implementation
```
class UserPage extends StatelessWidget {
  final String userId;

  const UserPage({Key? key, required this.userId}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return BlocProvider(
      create: (context) => getIt<UserBloc>()
        ..add(UserEvent.getUser(userId)),
      child: Scaffold(
        appBar: AppBar(
          title: const Text('User Details'),
          actions: [
            BlocBuilder<UserBloc, UserState>(
              builder: (context, state) {
                return IconButton(
                  icon: const Icon(Icons.refresh),
                  onPressed: () {
                    context.read<UserBloc>().add(const UserEvent.refreshUser());
                  },
                );
              },
            ),
          ],
        ),
        body: BlocBuilder<UserBloc, UserState>(
          builder: (context, state) {
            return state.maybeWhen(
              initial: () => const SizedBox(),
              loading: () => const Center(child: CircularProgressIndicator()),
              loaded: (user) => UserDetailsWidget(user: user),
              error: (failure) => ErrorWidget(failure: failure),
              orElse: () => const SizedBox(),
            );
          },
        ),
      ),
    );
  }
}
```

### Dependency Registration
```
final getIt = GetIt.instance;

void initDependencies() {
  // Core
  getIt.registerLazySingleton<NetworkInfo>(() => NetworkInfoImpl(getIt()));
  
  // Features - User
  // Data sources
  getIt.registerLazySingleton<UserRemoteDataSource>(
    () => UserRemoteDataSourceImpl(client: getIt()),
  );
  getIt.registerLazySingleton<UserLocalDataSource>(
    () => UserLocalDataSourceImpl(sharedPreferences: getIt()),
  );
  
  // Repository
  getIt.registerLazySingleton<UserRepository>(() => UserRepositoryImpl(
    remoteDataSource: getIt(),
    localDataSource: getIt(),
    networkInfo: getIt(),
  ));
  
  // Use cases
  getIt.registerLazySingleton(() => GetUser(getIt()));
  
  // Bloc
  getIt.registerFactory(() => UserBloc(getUser: getIt()));
}
```
# Cubit Conventions & Organization

## Naming Conventions

### Classes
- **Cubit classes**: PascalCase, suffix with `Cubit` (e.g., `LoginCubit`, `UserProfileCubit`)
- **State classes**: PascalCase, suffix with `State` (e.g., `LoginState`, `UserProfileState`)
- **Repository classes**: PascalCase, suffix with `Repository` (e.g., `AuthRepository`, `UserRepository`)
- **Use case classes**: PascalCase, suffix with `UseCase` (e.g., `LoginUseCase`, `GetUserUseCase`)

### Files
- **Files**: snake_case (e.g., `login_cubit.dart`, `login_state.dart`)
- **Test files**: Add `_test` suffix (e.g., `login_cubit_test.dart`)
- **Mock files**: Add `_mock` suffix (e.g., `auth_repository_mock.dart`)

### Folders
- **Features**: snake_case (e.g., `user_profile`, `shopping_cart`)
- **Layers**: lowercase (e.g., `data`, `domain`, `presentation`)
- **Components**: lowercase plural (e.g., `cubits`, `widgets`, `pages`)

### Examples

```dart
// ✅ Good naming
class LoginCubit extends Cubit<LoginState> { }
class LoginState extends Equatable { }
class AuthRepository { }
class LoginUseCase { }

// ❌ Bad naming
class Login extends Cubit<LoginData> { }
class LoginData { }
class AuthRepo { }
class Login_UseCase { }
```

---

## File & Directory Organization

**Feature-First (Recommended for most projects):**
```
lib/
├── features/
│   ├── auth/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   └── dashboard/
│       ├── data/
│       ├── domain/
│       └── presentation/
└── shared/
    ├── data/
    ├── domain/
    └── presentation/
```

### File Organization Best Practices

1. **Separate files**: Each Cubit and State in separate files
2. **Logical grouping**: Group related files in folders
3. **Test placement**: Mirror production structure in `test/` folder
4. **Barrel exports**: Use `index.dart` files for easier imports

```dart
// lib/features/auth/auth.dart (barrel file)
export 'cubit/auth_cubit.dart';
export 'cubit/auth_state.dart';
export 'data/auth_repository_impl.dart';
export 'domain/auth_repository.dart';
export 'presentation/login_page.dart';
```

---

## Dependency Injection

### DI Library Recommendations

**For small projects:**
- Manual DI with factory functions
- Simple service locator pattern

**For medium projects:**
- `get_it` - Service locator
- `provider` - Widget-based DI

**For large projects:**
- `injectable` + `get_it` - Code generation
- `riverpod` - Compile-safe DI

### Get_it Service Locator

```dart
// lib/core/service_locator.dart
import 'package:get_it/get_it.dart';

final getIt = GetIt.instance;

void setupServiceLocator() {
  // External dependencies
  getIt.registerLazySingleton<Dio>(() => Dio());
  getIt.registerLazySingleton<FlutterSecureStorage>(
    () => const FlutterSecureStorage(),
  );
  
  // Data sources
  getIt.registerLazySingleton<AuthRemoteDataSource>(
    () => AuthRemoteDataSourceImpl(getIt()),
  );
  
  // Repositories
  getIt.registerLazySingleton<AuthRepository>(
    () => AuthRepositoryImpl(getIt()),
  );
  
  // Use cases
  getIt.registerLazySingleton<LoginUseCase>(
    () => LoginUseCase(getIt()),
  );
  
  // Cubits
  getIt.registerFactory<AuthCubit>(
    () => AuthCubit(getIt()),
  );
}
```

### Injectable (Code Generation)

```dart
// lib/core/injection.dart
import 'package:injectable/injectable.dart';
import 'package:get_it/get_it.dart';

import 'injection.config.dart';

final getIt = GetIt.instance;

@InjectableInit()
void configureDependencies() => getIt.init();

// lib/core/injection.config.dart will be generated
```

```dart
// Data source registration
@Injectable(as: AuthRemoteDataSource)
class AuthRemoteDataSourceImpl implements AuthRemoteDataSource {
  AuthRemoteDataSourceImpl(@Named('authDio') this._dio);
  final Dio _dio;
}

// Repository registration
@Injectable(as: AuthRepository)
class AuthRepositoryImpl implements AuthRepository {
  AuthRepositoryImpl(this._remoteDataSource);
  final AuthRemoteDataSource _remoteDataSource;
}

// Cubit registration
@injectable
class AuthCubit extends Cubit<AuthState> {
  AuthCubit(this._authRepository) : super(AuthState.initial());
  final AuthRepository _authRepository;
}
```

### DI Module Pattern (with injectable)

```dart
@module
abstract class AppModule {
  @singleton
  @Named('authDio')
  Dio provideAuthDio() => Dio()..options.baseUrl = 'https://api.example.com';
  
  @singleton
  @Named('userDio')
  Dio provideUserDio() => Dio()..options.baseUrl = 'https://user-api.example.com';
  
  @singleton
  FlutterSecureStorage provideSecureStorage() => const FlutterSecureStorage();
}

@module
abstract class DatabaseModule {
  @singleton
  @preResolve
  Future<Database> provideDatabase() => $FloorAppDatabase
      .databaseBuilder('app_database.db')
      .build();
}
```

### Injecting Cubits in Widget Tree

```dart
// Single Cubit
BlocProvider(
  create: (context) => getIt<AuthCubit>(),
  child: LoginPage(),
)

// Multiple Cubits
MultiBlocProvider(
  providers: [
    BlocProvider(create: (context) => getIt<AuthCubit>()),
    BlocProvider(create: (context) => getIt<UserCubit>()),
  ],
  child: DashboardPage(),
)

// With lazy creation
BlocProvider.value(
  value: getIt<AuthCubit>(),
  child: LoginPage(),
)
```

### DI Best Practices

1. **Register early**: Set up DI in `main()` before running the app
2. **Use interfaces**: Register abstract classes, not implementations
3. **Lazy registration**: Use lazy singletons for expensive objects
4. **Scope properly**: Factory for Cubits, Singleton for repositories
5. **Test overrides**: Allow DI overrides for testing

```dart
// ✅ Good: Register interface
getIt.registerLazySingleton<AuthRepository>(
  () => AuthRepositoryImpl(getIt()),
);

// ❌ Bad: Register implementation
getIt.registerLazySingleton<AuthRepositoryImpl>(
  () => AuthRepositoryImpl(getIt()),
);

# Cubit Development Practices

## Networking & Error Handling

### Dio Configuration with Interceptors

```dart
class ApiService {
  late final Dio _dio;

  ApiService() {
    _dio = Dio(BaseOptions(
      baseUrl: 'https://api.example.com',
      connectTimeout: const Duration(seconds: 30),
      receiveTimeout: const Duration(seconds: 30),
      headers: {
        'Content-Type': 'application/json',
        'Accept': 'application/json',
      },
    ));

    _dio.interceptors.addAll([
      _AuthInterceptor(),
      _LoggingInterceptor(),
      _ErrorInterceptor(),
    ]);
  }

  Dio get dio => _dio;
}
```

### Authentication Interceptor

```dart
class _AuthInterceptor extends Interceptor {
  @override
  void onRequest(RequestOptions options, RequestInterceptorHandler handler) {
    final accessToken = getIt<AuthService>().accessToken;
    if (accessToken != null) {
      options.headers['Authorization'] = 'Bearer $accessToken';
    }
    handler.next(options);
  }

  @override
  void onError(DioException err, ErrorInterceptorHandler handler) {
    if (err.response?.statusCode == 401) {
      // Handle accessToken refresh or logout
      getIt<AuthService>().logout();
    }
    handler.next(err);
  }
}
```

### Error Handling Best Practices

```dart
// Custom exception classes
abstract class AppException implements Exception {
  final String message;
  final String? code;
  final Map<String, dynamic>? details;

  const AppException(this.message, {this.code, this.details});
}

class NetworkException extends AppException {
  const NetworkException(super.message, {super.code, super.details});
}

class ValidationException extends AppException {
  const ValidationException(super.message, {super.code, super.details});
}

class AuthenticationException extends AppException {
  const AuthenticationException(super.message, {super.code, super.details});
}

// Repository error handling
class UserRepository {
  final ApiService _apiService;

  UserRepository(this._apiService);

  Future<Result<User>> getUser(String id) async {
    try {
      final response = await _apiService.dio.get('/users/$id');
      final user = User.fromJson(response.data);
      return Result.success(data: user);
    } on DioException catch (e) {
      return Result.failure(error: _handleDioError(e));
    } catch (e) {
      return Result.failure(error: AppException('Unexpected error: $e'));
    }
  }

  AppException _handleDioError(DioException e) {
    switch (e.type) {
      case DioExceptionType.connectionTimeout:
      case DioExceptionType.receiveTimeout:
        return const NetworkException('Connection timeout');
      case DioExceptionType.badResponse:
        final statusCode = e.response?.statusCode;
        switch (statusCode) {
          case 400:
            return ValidationException('Invalid request', 
              details: e.response?.data);
          case 401:
            return const AuthenticationException('Unauthorized');
          case 404:
            return const NetworkException('Resource not found');
          default:
            return NetworkException('Server error: $statusCode');
        }
      default:
        return NetworkException('Network error: ${e.message}');
    }
  }
}
```

### Retry Logic

```dart
class RetryService {
  static Future<T> withRetry<T>(
    Future<T> Function() operation, {
    int maxRetries = 3,
    Duration delay = const Duration(seconds: 1),
  }) async {
    int attempts = 0;
    
    while (attempts < maxRetries) {
      try {
        return await operation();
      } catch (e) {
        attempts++;
        if (attempts >= maxRetries) rethrow;
        
        await Future.delayed(delay * attempts); // Exponential backoff
      }
    }
    
    throw Exception('Max retries exceeded');
  }
}

// Usage in repository
Future<Result<List<Product>>> getProducts() async {
  return await RetryService.withRetry(() async {
    final response = await _apiService.dio.get('/products');
    final products = (response.data as List)
        .map((json) => Product.fromJson(json))
        .toList();
    return Result.success(data: products);
  });
}
```

---

## Testing

### Unit Testing Cubits

```dart
// test/cubits/login_cubit_test.dart
import 'package:bloc_test/bloc_test.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:mockito/mockito.dart';

import '../mocks/mocks.dart';

void main() {
  group('LoginCubit', () {
    late MockAuthRepository mockAuthRepository;
    late LoginCubit loginCubit;

    setUp(() {
      mockAuthRepository = MockAuthRepository();
      loginCubit = LoginCubit(mockAuthRepository);
    });

    tearDown(() {
      loginCubit.close();
    });

    test('initial state is LoginState.initial', () {
      expect(loginCubit.state, equals(LoginState.initial()));
    });

    blocTest<LoginCubit, LoginState>(
      'emits [loading, success] when login succeeds',
      build: () {
        when(mockAuthRepository.login(any, any))
            .thenAnswer((_) async => User(id: '1', email: 'test@example.com'));
        return loginCubit;
      },
      act: (cubit) => cubit.login('test@example.com', 'password'),
      expect: () => [
        LoginState.loading(),
        LoginState.success(user: User(id: '1', email: 'test@example.com')),
      ],
      verify: (cubit) {
        verify(mockAuthRepository.login('test@example.com', 'password'))
            .called(1);
      },
    );

    blocTest<LoginCubit, LoginState>(
      'emits [loading, failure] when login fails',
      build: () {
        when(mockAuthRepository.login(any, any))
            .thenThrow(Exception('Invalid credentials'));
        return loginCubit;
      },
      act: (cubit) => cubit.login('test@example.com', 'wrong_password'),
      expect: () => [
        LoginState.loading(),
        LoginState.failure(error: 'Exception: Invalid credentials'),
      ],
    );

    blocTest<LoginCubit, LoginState>(
      'emits failure when email is empty',
      build: () => loginCubit,
      act: (cubit) => cubit.login('', 'password'),
      expect: () => [
        LoginState.failure(error: 'Email and password cannot be empty'),
      ],
      verify: (cubit) {
        verifyNever(mockAuthRepository.login(any, any));
      },
    );
  });
}
```

### Widget Testing with Cubit

```dart
// test/widgets/login_page_test.dart
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:mockito/mockito.dart';

void main() {
  group('LoginPage', () {
    late MockLoginCubit mockLoginCubit;

    setUp(() {
      mockLoginCubit = MockLoginCubit();
    });

    Widget createWidgetUnderTest() {
      return MaterialApp(
        home: BlocProvider<LoginCubit>.value(
          value: mockLoginCubit,
          child: const LoginPage(),
        ),
      );
    }

    testWidgets('renders email and password fields', (tester) async {
      when(() => mockLoginCubit.state).thenReturn(LoginState.initial());

      await tester.pumpWidget(createWidgetUnderTest());

      expect(find.byType(TextFormField), findsNWidgets(2));
      expect(find.text('Email'), findsOneWidget);
      expect(find.text('Password'), findsOneWidget);
    });

    testWidgets('calls login when form is submitted', (tester) async {
      when(() => mockLoginCubit.state).thenReturn(LoginState.initial());

      await tester.pumpWidget(createWidgetUnderTest());

      await tester.enterText(find.byKey(const Key('email_field')), 'test@example.com');
      await tester.enterText(find.byKey(const Key('password_field')), 'password');
      await tester.tap(find.byKey(const Key('login_button')));

      verify(() => mockLoginCubit.login('test@example.com', 'password')).called(1);
    });

    testWidgets('shows loading indicator when state is loading', (tester) async {
      when(() => mockLoginCubit.state).thenReturn(LoginState.loading());

      await tester.pumpWidget(createWidgetUnderTest());

      expect(find.byType(CircularProgressIndicator), findsOneWidget);
    });

    testWidgets('shows error message when state is failure', (tester) async {
      when(() => mockLoginCubit.state).thenReturn(
        LoginState.failure(error: 'Invalid credentials'),
      );

      await tester.pumpWidget(createWidgetUnderTest());

      expect(find.text('Invalid credentials'), findsOneWidget);
    });
  });
}
```

### Integration Testing

```dart
// integration_test/login_flow_test.dart
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:integration_test/integration_test.dart';
import 'package:my_app/main.dart' as app;

void main() {
  IntegrationTestWidgetsFlutterBinding.ensureInitialized();

  group('Login Flow Integration Tests', () {
    testWidgets('complete login flow', (tester) async {
      app.main();
      await tester.pumpAndSettle();

      // Navigate to login page
      await tester.tap(find.text('Login'));
      await tester.pumpAndSettle();

      // Enter credentials
      await tester.enterText(find.byKey(const Key('email_field')), 'test@example.com');
      await tester.enterText(find.byKey(const Key('password_field')), 'password123');
      
      // Submit form
      await tester.tap(find.byKey(const Key('login_button')));
      await tester.pumpAndSettle();

      // Verify successful login
      expect(find.text('Welcome'), findsOneWidget);
      expect(find.byKey(const Key('dashboard')), findsOneWidget);
    });

    testWidgets('login with invalid credentials shows error', (tester) async {
      app.main();
      await tester.pumpAndSettle();

      await tester.tap(find.text('Login'));
      await tester.pumpAndSettle();

      await tester.enterText(find.byKey(const Key('email_field')), 'invalid@example.com');
      await tester.enterText(find.byKey(const Key('password_field')), 'wrongpassword');
      
      await tester.tap(find.byKey(const Key('login_button')));
      await tester.pumpAndSettle();

      expect(find.text('Invalid credentials'), findsOneWidget);
    });
  });
}
```

---

## Performance Optimization

### State Optimization

```dart
// Use equatable or freezed for efficient state comparisons
@freezed
class ProductListState with _$ProductListState {
  const factory ProductListState({
    @Default([]) List<Product> products,
    @Default(false) bool isLoading,
    @Default(null) String? error,
    @Default(null) String? searchQuery,
    @Default(null) Category? selectedCategory,
  }) = _ProductListState;
}

// Selective state updates
class ProductListCubit extends Cubit<ProductListState> {
  ProductListCubit() : super(const ProductListState());

  void updateSearchQuery(String query) {
    // Only emit if query actually changed
    if (state.searchQuery != query) {
      emit(state.copyWith(searchQuery: query));
    }
  }

  void selectCategory(Category category) {
    // Only emit if category changed
    if (state.selectedCategory != category) {
      emit(state.copyWith(selectedCategory: category));
    }
  }
}
```

### BlocBuilder Optimization

```dart
// ❌ Bad: Rebuilds entire list when search query changes
BlocBuilder<ProductListCubit, ProductListState>(
  builder: (context, state) {
    return Column(
      children: [
        SearchBar(query: state.searchQuery),
        ProductList(products: state.products),
        LoadingIndicator(isVisible: state.isLoading),
      ],
    );
  },
)

// ✅ Good: Separate builders for different parts of state
Column(
  children: [
    BlocBuilder<ProductListCubit, ProductListState>(
      buildWhen: (previous, current) => previous.searchQuery != current.searchQuery,
      builder: (context, state) => SearchBar(query: state.searchQuery),
    ),
    BlocBuilder<ProductListCubit, ProductListState>(
      buildWhen: (previous, current) => previous.products != current.products,
      builder: (context, state) => ProductList(products: state.products),
    ),
    BlocBuilder<ProductListCubit, ProductListState>(
      buildWhen: (previous, current) => previous.isLoading != current.isLoading,
      builder: (context, state) => LoadingIndicator(isVisible: state.isLoading),
    ),
  ],
)
```

### Memory Management

```dart
class ProductListCubit extends Cubit<ProductListState> {
  ProductListCubit(this._repository) : super(const ProductListState());

  final ProductRepository _repository;
  Timer? _debounceTimer;
  StreamSubscription? _subscription;

  void searchProducts(String query) {
    // Debounce search requests
    _debounceTimer?.cancel();
    _debounceTimer = Timer(const Duration(milliseconds: 500), () {
      _performSearch(query);
    });
  }

  Future<void> _performSearch(String query) async {
    emit(state.copyWith(isLoading: true, searchQuery: query));
    
    try {
      final products = await _repository.searchProducts(query);
      emit(state.copyWith(products: products, isLoading: false));
    } catch (e) {
      emit(state.copyWith(error: e.toString(), isLoading: false));
    }
  }

  @override
  Future<void> close() {
    _debounceTimer?.cancel();
    _subscription?.cancel();
    return super.close();
  }
}
```

### Lazy Loading and Pagination

```dart
class ProductListCubit extends Cubit<PaginationState<Product>> {
  ProductListCubit(this._repository) : super(const PaginationState());

  final ProductRepository _repository;
  static const int _pageSize = 20;

  Future<void> loadProducts({bool refresh = false}) async {
    if (refresh) {
      emit(const PaginationState()); // Reset state
    }

    if (state.isLoading || state.hasReachedMax) return;

    final isFirstPage = state.items.isEmpty;
    emit(state.copyWith(
      isLoading: isFirstPage,
      isLoadingMore: !isFirstPage,
    ));

    try {
      final newProducts = await _repository.getProducts(
        page: state.currentPage + 1,
        limit: _pageSize,
      );

      final hasReachedMax = newProducts.length < _pageSize;

      emit(state.copyWith(
        items: refresh ? newProducts : [...state.items, ...newProducts],
        isLoading: false,
        isLoadingMore: false,
        currentPage: state.currentPage + 1,
        hasReachedMax: hasReachedMax,
      ));
    } catch (e) {
      emit(state.copyWith(
        isLoading: false,
        isLoadingMore: false,
        error: e.toString(),
      ));
    }
  }
}
```

---

## Best Practices

### Cubit Lifecycle Management

```dart
class UserProfileCubit extends Cubit<UserProfileState> {
  UserProfileCubit(this._userRepository, this._analyticsService)
      : super(UserProfileState.initial()) {
    _initialize();
  }

  final UserRepository _userRepository;
  final AnalyticsService _analyticsService;
  StreamSubscription? _userSubscription;

  void _initialize() {
    // Track cubit creation
    _analyticsService.track('user_profile_cubit_created');
    
    // Listen to user changes
    _userSubscription = _userRepository.userStream.listen(
      (user) => emit(state.copyWith(user: user)),
      onError: (error) => emit(state.copyWith(error: error.toString())),
    );
  }

  @override
  Future<void> close() {
    _userSubscription?.cancel();
    _analyticsService.track('user_profile_cubit_closed');
    return super.close();
  }
}
```

### Error Recovery

```dart
class DataSyncCubit extends Cubit<DataSyncState> {
  DataSyncCubit(this._syncService) : super(DataSyncState.initial());

  final SyncService _syncService;
  int _retryCount = 0;
  static const int _maxRetries = 3;

  Future<void> syncData() async {
    emit(state.copyWith(isSyncing: true, error: null));

    try {
      await _syncService.syncAllData();
      emit(state.copyWith(
        isSyncing: false,
        lastSyncTime: DateTime.now(),
      ));
      _retryCount = 0; // Reset retry count on success
    } catch (e) {
      if (_retryCount < _maxRetries) {
        _retryCount++;
        await Future.delayed(Duration(seconds: _retryCount * 2));
        await syncData(); // Retry with exponential backoff
      } else {
        emit(state.copyWith(
          isSyncing: false,
          error: 'Sync failed after $_maxRetries attempts: $e',
        ));
        _retryCount = 0; // Reset for next manual sync
      }
    }
  }

  void retrySync() {
    _retryCount = 0;
    syncData();
  }
}
```

### State Composition

```dart
// Compose complex state from multiple simpler states
@freezed
class AppState with _$AppState {
  const factory AppState({
    required AuthState auth,
    required UserState user,
    required SettingsState settings,
    required ConnectionState connection,
  }) = _AppState;
}

class AppCubit extends Cubit<AppState> {
  AppCubit(
    this._authCubit,
    this._userCubit,
    this._settingsCubit,
    this._connectionCubit,
  ) : super(AppState(
    auth: _authCubit.state,
    user: _userCubit.state,
    settings: _settingsCubit.state,
    connection: _connectionCubit.state,
  )) {
    // Listen to all child cubits
    _authSubscription = _authCubit.stream.listen(_onAuthChanged);
    _userSubscription = _userCubit.stream.listen(_onUserChanged);
    _settingsSubscription = _settingsCubit.stream.listen(_onSettingsChanged);
    _connectionSubscription = _connectionCubit.stream.listen(_onConnectionChanged);
  }

  final AuthCubit _authCubit;
  final UserCubit _userCubit;
  final SettingsCubit _settingsCubit;
  final ConnectionCubit _connectionCubit;

  late final StreamSubscription _authSubscription;
  late final StreamSubscription _userSubscription;
  late final StreamSubscription _settingsSubscription;
  late final StreamSubscription _connectionSubscription;

  void _onAuthChanged(AuthState authState) {
    emit(state.copyWith(auth: authState));
    
    // Handle side effects
    if (!authState.isAuthenticated) {
      _userCubit.clearUser();
    }
  }

  void _onUserChanged(UserState userState) {
    emit(state.copyWith(user: userState));
  }

  void _onSettingsChanged(SettingsState settingsState) {
    emit(state.copyWith(settings: settingsState));
  }

  void _onConnectionChanged(ConnectionState connectionState) {
    emit(state.copyWith(connection: connectionState));
  }

  @override
  Future<void> close() {
    _authSubscription.cancel();
    _userSubscription.cancel();
    _settingsSubscription.cancel();
    _connectionSubscription.cancel();
    return super.close();
  }
}
```

### Testing Best Practices

1. **Test business logic, not implementation details**
2. **Use meaningful test descriptions**
3. **Test edge cases and error conditions**
4. **Mock external dependencies**
5. **Use blocTest for complex state transitions**

```dart
// ✅ Good: Tests business logic
blocTest<LoginCubit, LoginState>(
  'should emit success state when login succeeds with valid credentials',
  build: () {
    when(() => mockAuthRepository.login(any(), any()))
        .thenAnswer((_) async => mockUser);
    return LoginCubit(mockAuthRepository);
  },
  act: (cubit) => cubit.login('valid@email.com', 'validPassword'),
  expect: () => [
    const LoginState.loading(),
    LoginState.success(user: mockUser),
  ],
);

// ❌ Bad: Tests implementation details
blocTest<LoginCubit, LoginState>(
  'should call repository login method',
  build: () => LoginCubit(mockAuthRepository),
  act: (cubit) => cubit.login('email', 'password'),
  verify: (cubit) {
    verify(() => mockAuthRepository.login('email', 'password')).called(1);
  },
);
``` 

# Cubit State Management Guide

## State Management with Cubit & Freezed

For complex state objects, use Freezed for code generation:

```dart
// login_state.dart
import 'package:freezed_annotation/freezed_annotation.dart';

part 'login_state.freezed.dart';

@freezed
class LoginState with _$LoginState {
  const factory LoginState({
    @Default(LoginStatus.initial) LoginStatus status,
    @Default(null) String? error,
    @Default(null) User? user,
    @Default(false) bool isLoading,
    @Default(false) bool obscurePassword,
  }) = _LoginState;

  // Factory for initial state
  factory LoginState.initial() => const LoginState();
  
  // Convenience getters
  const LoginState._();
  bool get isAuthenticated => user != null;
  bool get hasError => error != null;
}

enum LoginStatus { initial, loading, success, failure }
```

### Basic Cubit Implementation

```dart
// login_cubit.dart
import 'package:flutter_bloc/flutter_bloc.dart';

class LoginCubit extends Cubit<LoginState> {
  LoginCubit(this._authRepository) : super(LoginState.initial());

  final AuthRepository _authRepository;

  Future<void> login(String email, String password) async {
    if (email.isEmpty || password.isEmpty) {
      emit(state.copyWith(
        status: LoginStatus.failure,
        error: 'Email and password cannot be empty',
      ));
      return;
    }

    emit(state.copyWith(status: LoginStatus.loading));

    try {
      final user = await _authRepository.login(email, password);
      emit(state.copyWith(
        status: LoginStatus.success,
        user: user,
        error: null,
      ));
    } catch (e) {
      emit(state.copyWith(
        status: LoginStatus.failure,
        error: e.toString(),
      ));
    }
  }

  void togglePasswordVisibility() {
    emit(state.copyWith(obscurePassword: !state.obscurePassword));
  }

  void clearError() {
    emit(state.copyWith(error: null));
  }

  @override
  Future<void> close() {
    // Clean up resources if needed
    return super.close();
  }
}
```

### Advanced Cubit with Stream Subscriptions

```dart
class UserCubit extends Cubit<UserState> {
  UserCubit(this._userRepository, this._authCubit) : super(UserState.initial()) {
    // Listen to auth changes
    _authSubscription = _authCubit.stream.listen((authState) {
      if (authState.isAuthenticated) {
        loadUserProfile();
      } else {
        emit(UserState.initial());
      }
    });
  }

  final UserRepository _userRepository;
  final AuthCubit _authCubit;
  StreamSubscription<AuthState>? _authSubscription;

  Future<void> loadUserProfile() async {
    emit(state.copyWith(isLoading: true));
    
    try {
      final user = await _userRepository.getCurrentUser();
      emit(state.copyWith(
        user: user,
        isLoading: false,
        error: null,
      ));
    } catch (e) {
      emit(state.copyWith(
        isLoading: false,
        error: e.toString(),
      ));
    }
  }

  @override
  Future<void> close() {
    _authSubscription?.cancel();
    return super.close();
  }
}
```

---

## Hook Usage Guidelines(If needed)

### Hook Organization in build() Method

When using Flutter Hooks with Cubit, organize all hook calls at the beginning:

```dart
class LoginPage extends HookWidget {
  const LoginPage({super.key});

  @override
  Widget build(BuildContext context) {
    // 1. Form hooks
    final emailController = useTextEditingController();
    final passwordController = useTextEditingController();
    final formKey = useMemoized(() => GlobalKey<FormState>());
    
    // 2. State hooks
    final isLoading = useState(false);
    final autoValidate = useState(false);
    
    // 3. Effect hooks
    useEffect(() {
      // Clear controllers on dispose
      return () {
        emailController.dispose();
        passwordController.dispose();
      };
    }, []);
    
    // 4. Computed values
    final isFormValid = useMemoized(() {
      return emailController.text.isNotEmpty && 
             passwordController.text.isNotEmpty;
    }, [emailController.text, passwordController.text]);
    
    // 5. Return widget tree
    return Scaffold(
      body: _buildBody(
        emailController,
        passwordController,
        formKey,
        isFormValid,
      ),
    );
  }
}
```

### Custom Hooks for Cubit(if needed)

Create reusable hooks for common Cubit patterns:

```dart
// Custom hook for form validation
FormValidationHook useFormValidation(List<TextEditingController> controllers) {
  final isValid = useState(false);
  final errors = useState<Map<String, String>>({});

  useEffect(() {
    void validateForm() {
      final newErrors = <String, String>{};
      bool valid = true;

      for (int i = 0; i < controllers.length; i++) {
        if (controllers[i].text.isEmpty) {
          newErrors['field_$i'] = 'This field is required';
          valid = false;
        }
      }

      isValid.value = valid;
      errors.value = newErrors;
    }

    // Add listeners to all controllers
    for (final controller in controllers) {
      controller.addListener(validateForm);
    }

    return () {
      // Remove listeners
      for (final controller in controllers) {
        controller.removeListener(validateForm);
      }
    };
  }, controllers);

  return FormValidationHook(
    isValid: isValid.value,
    errors: errors.value,
  );
}

class FormValidationHook {
  const FormValidationHook({
    required this.isValid,
    required this.errors,
  });

  final bool isValid;
  final Map<String, String> errors;
}
```

### Hook Best Practices

1. **Organize by purpose**: Group related hooks together
2. **Use meaningful names**: Hook variables should be descriptive
3. **Handle cleanup**: Always dispose of resources in useEffect cleanup
4. **Avoid deep dependencies**: Keep dependency arrays simple
5. **Memoize expensive calculations**: Use useMemoized for heavy computations

```dart
// ✅ Good: Well-organized hooks
class ProductListPage extends HookWidget {
  @override
  Widget build(BuildContext context) {
    // Search and filtering
    final searchController = useTextEditingController();
    final selectedCategory = useState<String?>(null);
    
    // Pagination
    final scrollController = useScrollController();
    final isLoadingMore = useState(false);
    
    // Data fetching
    useEffect(() {
      context.read<ProductCubit>().loadProducts();
      return null;
    }, []);
    
    // Infinite scroll
    useEffect(() {
      void onScroll() {
        if (scrollController.position.pixels == 
            scrollController.position.maxScrollExtent) {
          context.read<ProductCubit>().loadMoreProducts();
        }
      }
      
      scrollController.addListener(onScroll);
      return () => scrollController.removeListener(onScroll);
    }, [scrollController]);
    
    return Scaffold(/* ... */);
  }
}
```

---

## State Patterns

### Loading State Pattern

```dart
@freezed
class DataState<T> with _$DataState<T> {
  const factory DataState.initial() = DataInitial<T>;
  const factory DataState.loading() = DataLoading<T>;
  const factory DataState.success(T data) = DataSuccess<T>;
  const factory DataState.failure(String error) = DataFailure<T>;
}

// Usage in UI
BlocBuilder<ProductCubit, DataState<List<Product>>>(
  builder: (context, state) {
    return state.when(
      initial: () => const Center(child: Text('Ready to load')),
      loading: () => const Center(child: CircularProgressIndicator()),
      success: (products) => ProductList(products: products),
      failure: (error) => ErrorWidget(error: error),
    );
  },
)
```

### Pagination State Pattern

```dart
@freezed
class PaginationState<T> with _$PaginationState<T> {
  const factory PaginationState({
    @Default([]) List<T> items,
    @Default(false) bool isLoading,
    @Default(false) bool isLoadingMore,
    @Default(false) bool hasReachedMax,
    @Default(1) int currentPage,
    String? error,
  }) = _PaginationState<T>;
}

class ProductCubit extends Cubit<PaginationState<Product>> {
  ProductCubit(this._repository) : super(const PaginationState());

  final ProductRepository _repository;

  Future<void> loadProducts() async {
    emit(state.copyWith(isLoading: true, error: null));
    
    try {
      final products = await _repository.getProducts(page: 1);
      emit(state.copyWith(
        items: products,
        isLoading: false,
        currentPage: 1,
        hasReachedMax: products.length < 20, // Assuming 20 per page
      ));
    } catch (e) {
      emit(state.copyWith(isLoading: false, error: e.toString()));
    }
  }

  Future<void> loadMoreProducts() async {
    if (state.isLoadingMore || state.hasReachedMax) return;
    
    emit(state.copyWith(isLoadingMore: true));
    
    try {
      final newProducts = await _repository.getProducts(
        page: state.currentPage + 1,
      );
      
      emit(state.copyWith(
        items: [...state.items, ...newProducts],
        isLoadingMore: false,
        currentPage: state.currentPage + 1,
        hasReachedMax: newProducts.length < 20,
      ));
    } catch (e) {
      emit(state.copyWith(isLoadingMore: false, error: e.toString()));
    }
  }
}
```

### Form State Pattern

```dart
@freezed
class FormState with _$FormState {
  const factory FormState({
    @Default({}) Map<String, String> values,
    @Default({}) Map<String, String> errors,
    @Default(false) bool isSubmitting,
    @Default(false) bool isValid,
    @Default(false) bool isDirty,
  }) = _FormState;
}

class ContactFormCubit extends Cubit<FormState> {
  ContactFormCubit() : super(const FormState());

  void updateField(String field, String value) {
    final newValues = Map<String, String>.from(state.values);
    newValues[field] = value;
    
    final newErrors = Map<String, String>.from(state.errors);
    newErrors.remove(field); // Clear error when typing
    
    emit(state.copyWith(
      values: newValues,
      errors: newErrors,
      isDirty: true,
      isValid: _validateForm(newValues),
    ));
  }

  bool _validateForm(Map<String, String> values) {
    return values['email']?.isNotEmpty == true &&
           values['name']?.isNotEmpty == true &&
           values['message']?.isNotEmpty == true;
  }

  Future<void> submitForm() async {
    if (!state.isValid) {
      emit(state.copyWith(errors: _getValidationErrors()));
      return;
    }

    emit(state.copyWith(isSubmitting: true));
    
    try {
      await _submitToServer(state.values);
      emit(const FormState()); // Reset form
    } catch (e) {
      emit(state.copyWith(
        isSubmitting: false,
        errors: {'general': e.toString()},
      ));
    }
  }
}
```

---

## Error Handling in State

### Error State Types

```dart
@freezed
class AppError with _$AppError {
  const factory AppError.network(String message) = NetworkError;
  const factory AppError.validation(Map<String, String> errors) = ValidationError;
  const factory AppError.authentication(String message) = AuthError;
  const factory AppError.unknown(String message) = UnknownError;
}

@freezed
class UserState with _$UserState {
  const factory UserState({
    @Default(false) bool isLoading,
    @Default(null) User? user,
    @Default(null) AppError? error,
  }) = _UserState;
}
```

### Error Handling in UI

```dart
BlocListener<UserCubit, UserState>(
  listener: (context, state) {
    if (state.error != null) {
      state.error!.when(
        network: (message) => _showNetworkError(context, message),
        validation: (errors) => _showValidationErrors(context, errors),
        authentication: (message) => _redirectToLogin(context),
        unknown: (message) => _showGenericError(context, message),
      );
    }
  },
  child: BlocBuilder<UserCubit, UserState>(
    builder: (context, state) {
      if (state.isLoading) {
        return const LoadingIndicator();
      }
      
      return UserProfile(user: state.user);
    },
  ),
)
```

### Global Error Handling

```dart
class AppCubit extends Cubit<AppState> {
  AppCubit() : super(AppState.initial()) {
    // Listen to all Cubit errors globally
    _errorController.stream.listen(_handleGlobalError);
  }

  final StreamController<AppError> _errorController = StreamController();
  
  void reportError(AppError error) {
    _errorController.add(error);
  }

  void _handleGlobalError(AppError error) {
    error.when(
      network: (message) => emit(state.copyWith(
        connectionStatus: ConnectionStatus.disconnected,
        lastError: error,
      )),
      authentication: (message) => emit(state.copyWith(
        isAuthenticated: false,
        lastError: error,
      )),
      validation: (errors) => {}, // Handle locally
      unknown: (message) => emit(state.copyWith(lastError: error)),
    );
  }
} 
Refer to official Flutter and flutter_bloc documentation for more detailed implementation guidelines.