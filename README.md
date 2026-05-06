# TunisiaHeritageQuest-mohamed-nidhal-el-moulaa-

# Tunisia Heritage Quest

## Project Overview
Tunisia Heritage Quest is an interactive Android quiz game designed to educate players about the rich historical monuments and cities of Tunisia. The app targets students, tourists, and history enthusiasts (ages 12+), offering a modern visual style with a Mediterranean blue and warm earth-tone palette. The current version fully implements the "Roman Heritage" category, featuring an interactive timer, multiple difficulty levels, and an adaptive UI.

## Architecture Explanation
The application is built using modern Android development practices and the **MVVM (Model-View-ViewModel)** architecture:
- **Model**: Data structures (`Question`, `Category`, `Difficulty`, `GameState`) handle the state of the game, while `GameRepository` acts as the single source of truth for the historical facts and images.
- **View**: The UI is entirely constructed with declarative **Jetpack Compose**. It utilizes `Scaffold`, `LazyColumn`, and `Box` layouts to ensure an adaptive design across different screen sizes.
- **ViewModel**: `GameViewModel` acts as the state holder. It manages game logic such as score calculation and timer countdowns using Coroutines, exposing the state to the UI via `StateFlow`.
- **Navigation**: Jetpack Navigation Compose handles routing seamlessly between the 6 core screens (Splash, Menu, Category, Difficulty, Gameplay, Results) using a `NavHost`.

## Setup Instructions
1. Ensure you have **Android Studio** (Ladybug or newer recommended) installed.
2. Clone this repository and open the `mohamednidhalelmoulaa` folder in Android Studio.
3. Allow Gradle to sync and download all necessary dependencies (Jetpack Compose, Navigation, UI Tooling, etc.).
4. Run the application on an Android emulator or a physical device running Android 7.0 (API level 24) or higher.

## Known Issues
- **Unit Testing Coroutines**: Running standard JUnit tests (`testDebugUnitTest`) against the `GameViewModel` may throw a `RuntimeException` or `IllegalStateException` due to the lack of an Android Main Looper in the standard test environment. 
- **Image Scaling**: Depending on the resolution of the uploaded images, some images may be cropped due to the `ContentScale.Crop` attribute in the `GameplayScreen`. This ensures a uniform UI but might cut off edges of very tall/wide images.

## Test Report
The project includes the three required testing layers:
1. **Unit Tests (`GameViewModelTest.kt`)**: Tests were written to verify score calculation, correct/incorrect answer processing, and state transitions.
2. **UI Component Tests (`GameplayScreenTest.kt`)**: Verifies that Jetpack Compose nodes exist and react correctly. Tests successfully confirm that answering a question reveals the historical fact card and the "Next Question" button.
3. **Integration/Navigation Tests (`NavigationTest.kt`)**: A `TestNavHostController` is used to simulate routing. The test verifies that clicking "Play Game" on the Main Menu correctly pushes the `Category` route onto the backstack.

*Manual testing was also performed across an emulated device to verify UI responsiveness, color theming, and timer accuracy during the Gameplay state.*
