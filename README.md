# Flutter Provider Demo

A demonstration project showcasing the use of Provider pattern in Flutter with multiple providers.

## About This Project

This project serves as a teaching example for Flutter state management using the Provider package. It demonstrates how to implement and use multiple providers in a Flutter application with proper code organization.

### Features

- Counter functionality with state management
- Theme switching (light/dark mode)
- Properly structured project organization
- Demonstration of three different Provider access methods

## Provider Access Methods

This project showcases three different ways to access provider data:

1. **context.watch\<T\>()** - Listens to changes and rebuilds when the provider updates
   ```dart
   // Example: Display counter value that updates automatically
   Text('${context.watch<Counter>().count}')
   ```

2. **context.read\<T\>()** - One-time read access without rebuilding
   ```dart
   // Example: Trigger an action without setting up listeners
   onPressed: () => context.read<Counter>().increment()
   ```

3. **Consumer\<T\>** - Fine-grained rebuilds for specific widget subtrees
   ```dart
   // Example: Only rebuild this specific widget when ThemeProvider changes
   Consumer<ThemeProvider>(
     builder: (context, themeProvider, child) {
       return Text('Current theme: ${themeProvider.isDarkMode ? 'Dark' : 'Light'}');
     },
   )
   ```

## Project Structure

```
lib/
  ├── main.dart              # Entry point with MultiProvider setup
  ├── providers/
  │   ├── counter_provider.dart    # Counter state management
  │   └── theme_provider.dart      # Theme state management
  └── screens/
      └── home_page.dart           # UI implementation
```

## MultiProvider Usage

The project demonstrates how to set up multiple providers using the MultiProvider widget:

```dart
MultiProvider(
  providers: [
    ChangeNotifierProvider(create: (_) => Counter()),
    ChangeNotifierProvider(create: (_) => ThemeProvider()),
    // Add more providers as needed
  ],
  child: const MyApp(),
)
```

## Getting Started

1. Ensure you have Flutter installed on your machine
2. Clone this repository
3. Run `flutter pub get` to install dependencies
4. Run `flutter run` to start the application

## Learning Resources

For more information about Provider:
- [Provider package](https://pub.dev/packages/provider)
- [Flutter state management documentation](https://docs.flutter.dev/data-and-backend/state-mgmt/intro)
- [InheritedWidget documentation](https://api.flutter.dev/flutter/widgets/InheritedWidget-class.html)
