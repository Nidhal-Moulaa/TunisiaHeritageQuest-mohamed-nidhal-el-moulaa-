# Tunisia Heritage Quest - Project Report

**Student Name:** [Your Name]
**Project Name:** Tunisia Heritage Quest

## Overview
This report details the implementation of the Tunisia Heritage Quest application, an image identification game built with Android Studio, Kotlin, and Jetpack Compose.

## 1. Architecture & Technologies
The application uses the **MVVM (Model-View-ViewModel)** architecture:
- **Model**: Data classes (`Question`, `Category`, `Difficulty`, `GameState`) define the application data. `GameRepository` acts as the data source.
- **View**: Built entirely with Jetpack Compose using modern UI principles and a custom color palette (Mediterranean Blue and Warm Earth Tones).
- **ViewModel**: `GameViewModel` manages the game state using `StateFlow`, handling the timer, scoring, and question progression.
- **Navigation**: Jetpack Navigation Compose is used for routing between the 6 distinct screens.

## 2. Activity Lifecycle & State Management
The game uses `ViewModel` to survive configuration changes. `StateFlow` ensures the UI reactively updates when the timer ticks or the score changes. A `LaunchedEffect` is used in the `SplashScreen` to handle the initial delay without blocking the main thread, and another in the `GameplayScreen` to observe when the game ends and trigger navigation.

## 3. Testing
Three types of tests were implemented:
1. **Unit Tests**: `GameViewModelTest` verifies the core logic (score calculation, difficulty settings, and question advancement).
2. **UI Component Tests**: `GameplayScreenTest` uses `createComposeRule` to verify that question text appears and interacting with buttons updates the UI state (showing the fact and next button).
3. **Integration/Navigation Tests**: `NavigationTest` verifies the NavHost setup, testing the transition from the Main Menu to the Category Selection screen.

## 4. Adaptive UI
The Jetpack Compose layout uses flexible modifiers (`fillMaxSize`, `fillMaxWidth`, `weight`, `padding`) to ensure the application adapts to different screen sizes, whether on a phone or tablet. Box and Column layouts ensure the content remains centered and readable.

## 5. Screenshots

*(Please replace the placeholders below with actual screenshots from your device or emulator)*

### Splash Screen
![Splash Screen](path/to/your/splash_screen_screenshot.png)

### Main Menu
![Main Menu](path/to/your/main_menu_screenshot.png)

### Category Selection
![Category Selection](path/to/your/category_selection_screenshot.png)

### Difficulty Settings
![Difficulty Settings](path/to/your/difficulty_settings_screenshot.png)

### Gameplay Screen
![Gameplay Screen](path/to/your/gameplay_screen_screenshot.png)

### Results Screen
![Results Screen](path/to/your/results_screen_screenshot.png)
