# Capital App – Flutter Project

> **Note**: The name **Capital App** is used here as an example. You can replace it with your real project name or any custom naming as required.

## Table of Contents

1. [Introduction](#introduction)
2. [Work Breakdown Structure (WBS)](#work-breakdown-structure)
3. [Design Phase](#design-phase)
4. [Development Phase](#development-phase)
5. [Delivery Phase](#delivery-phase)
6. [Project Timeline & Estimations](#project-timeline--estimations)
7. [Project Setup](#project-setup)
    - [Creating a New Flutter Project](#creating-a-new-flutter-project)
    - [Installing and Using Hygen Generator](#installing-and-using-hygen-generator)
    - [Remote Repository & Jira Board](#remote-repository--jira-board)
    - [Recommended `.gitignore` Settings](#recommended-gitignore-settings)
    - [Pubspec/YAML Configuration](#pubspecyaml-configuration)
8. [Folder Structure](#folder-structure)
9. [Module Structure](#module-structure)
10. [References](#references)
11. [Conclusion](#conclusion)

---

## Introduction

This **Capital App** README outlines how to set up a base Flutter application from design to development through testing and deployment. The goal is to help teams get a quick start on implementing a standardized structure, tooling, and project flow. While your specific resources and assets may differ, the general framework and recommended practices remain consistent.

---

## Work Breakdown Structure

Below is an example work breakdown structure typically used in project management:

![WBS](https://blog.flutter.wtf/content/images/size/w1600/2023/10/WBS-2.png)

1. **Design**
   - Wireframe
   - Final UI/UX
2. **Develop**
   - Frontend (Flutter)
   - Backend (API / Database)
3. **Deliver**
   - Testing
   - Deployment

We will discuss each of these phases in detail.

---

## Design Phase

Our design phase covers:

1. **Wireframe**  
   Designers or product managers provide basic wireframes indicating user flows and screen transitions.

2. **Design**  
   - High-fidelity designs (main).
   - Localized designs (translations, RTL, etc.) if needed.

   **Important**: Always confirm you have all design assets from the design team.
   - Main app design (Figma/Sketch/Adobe XD).
   - Any translated screens (if the app is multilingual).

   **Examples:**

   ![Example Design 1](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-23%20at%205.20.32%20PM.png)
   ![Example Design 2](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-23%20at%205.23.13%20PM.png)

3. **Prototype**  
   Sometimes, you may receive a prototype link or file to better understand user navigation and interactions.

   **Example:**

   ![Prototype](https://raw.githubusercontent.com/saqib2st/Flutter_Base/refs/heads/main/ss/Screenshot%202024-12-23%20at%205.31.44%20PM.png)

At this stage, ensure you have:
- **Project Documentation** (requirement docs, user stories, acceptance criteria).
- **All assets** (icons, fonts, images, animations, translations).
- **Design prototypes** or wireframes.

---

## Development Phase

### Frontend

Implemented using **Flutter**. We structure our code in modules/features, using a recommended architecture:
- **Data** (Data sources, repositories)
- **Domain** (Entities, repositories, use-cases)
- **Presentation** (Providers/Controllers, Views, Widgets)

### Backend

Can be developed in parallel (Node.js, Firebase, or any RESTful API). However, from the Flutter perspective:
- We integrate with the backend via packages such as `dio` or `http`.
- We handle data caching with packages like `hive` if local storage is required.

---

## Delivery Phase

### Testing

Quality assurance is critical. Common steps:
1. **Unit Tests** – for core logic.
2. **Widget Tests** – for UI components.
3. **Integration Tests** – for complete flows.

### Deployment

1. **Staging/QA** – Release internal builds (TestFlight, Firebase App Distribution, etc.).
2. **Production** – Deploy to App Store / Google Play, or distribute internally.

---

## Project Timeline & Estimations

Before writing a line of code, estimate your tasks carefully:

1. **Simple Modules**
   - 1 week for Design per module
   - 1 week for State Management per module
   - 1 week for API integration

2. **Complex Modules**
   - Split tasks in your preferred task manager (like Jira)
   - Use the “Task by Task” approach
   - Refer to this article on best practices: [How to Estimate Time for a Project](https://blog.flutter.wtf/how-to-estimate-time-for-a-project/)

> **Pro Tip**: Always consult your project manager or product owner for final timelines.

---

## Project Setup

Below are step-by-step instructions on how to get started:

### Creating a New Flutter Project

1. Open your terminal and run:

    ```bash
    flutter create my_project_name
    ```

2. Navigate into the newly created project folder:

    ```bash
    cd my_project_name
    ```

### Installing and Using Hygen Generator

1. Install [Hygen](https://www.hygen.io/docs/quick-start/):

    ```bash
    npm install -g hygen
    ```

2. Download the **`_templates`** directory from this [GitHub link](https://github.com/saqib2st/Flutter_Base/tree/main/_templates).

3. Place the **`_templates`** directory in the **root** of your newly created Flutter project.

    Your project root should look like:

    ```
    my_project_name/
    ├── .git/
    ├── _templates/
    ├── lib/
    ├── pubspec.yaml
    └── ...
    ```

    ![Templates Folder](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-23%20at%206.02.47%20PM.png?raw=true)

### Generating Modules

After placing the templates, you can create new modules easily. For example:

```bash
hygen generator mobile Splash
hygen generator mobile Auth
hygen generator mobile Profile
```

Each command will generate a corresponding module in your `lib/features/modules` directory (or your chosen folder structure).

### Remote Repository & Jira Board

- **Repository**: Request your DevOps team or authorities to create a new remote repository (GitHub, GitLab, Bitbucket, etc.) for this project.
- **Jira Board**: If it doesn’t exist, request a new Jira board or similar PM tool. Add all tasks/features with estimates.

### Recommended `.gitignore` Settings

Use Toptal’s [GitIgnore Generator](https://www.toptal.com/developers/gitignore/) or a similar tool to create a tailored `.gitignore` for Flutter/Dart.

Merge it with your existing `.gitignore`.

Exclude unnecessary build artifacts, user-specific files, and generated code from your repository.

**Example:**

![.gitignore Example](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-23%20at%206.12.15%20PM.png?raw=true)

### Pubspec/YAML Configuration

Below is a sample of a cleaned-up `pubspec.yaml` for the Capital App:

```yaml
name: capital_app
description: "A new Flutter project."
publish_to: 'none'

version: 1.0.0+1

environment:
  sdk: '>=3.4.3 <4.0.0'

dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^1.0.6
  google_fonts: ^6.2.1
  provider: ^6.1.2
  cached_network_image: ^3.4.1
  flutter_svg: ^2.0.10+1
  pinput: ^5.0.0
  dio: ^5.7.0
  go_router: ^14.2.8
  pull_to_refresh: ^2.0.0
  flutter_localizations:
    sdk: flutter
  intl: ^0.19.0
  flutter_form_builder: ^9.3.0
  qr_code_scanner: ^1.0.1
  lottie: ^3.1.3
  flutter_launcher_icons: ^0.14.1
  share_plus: ^10.1.1
  form_builder_validators: ^11.0.0
  hive: ^2.2.3
  google_sign_in: ^6.2.2
  url_launcher: ^6.3.1

flutter_icons:
  android: true
  ios: true
  image_path: "assets/images/app_icon.png"
  image_path_android: "assets/images/app_icon.png"
  min_sdk_android: 21
  adaptive_icon_foreground: "assets/images/app_icon.png"
  adaptive_icon_background: '#01387B'

flutter_native_splash:
  android: true
  ios: true
  web: false
  color: "#01387B"
  android_12:
    color: "#01387B"

dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_lints: ^3.0.0
  flutter_native_splash: ^2.4.1

flutter:
  generate: true
  uses-material-design: true

  assets:
    - assets/images/
    - assets/icons/

  fonts:
    - family: Roboto
      fonts:
        - asset: assets/fonts/Roboto/Roboto-Black.ttf
        - asset: assets/fonts/Roboto/Roboto-BlackItalic.ttf
        - asset: assets/fonts/Roboto/Roboto-Bold.ttf
        - asset: assets/fonts/Roboto/Roboto-BoldItalic.ttf
        - asset: assets/fonts/Roboto/Roboto-Italic.ttf
        - asset: assets/fonts/Roboto/Roboto-Light.ttf
        - asset: assets/fonts/Roboto/Roboto-LightItalic.ttf
        - asset: assets/fonts/Roboto/Roboto-Medium.ttf
        - asset: assets/fonts/Roboto/Roboto-MediumItalic.ttf
        - asset: assets/fonts/Roboto/Roboto-Regular.ttf
        - asset: assets/fonts/Roboto/Roboto-Thin.ttf
        - asset: assets/fonts/Roboto/Roboto-ThinItalic.ttf

    - family: GtAmerica
      fonts:
        - asset: assets/fonts/GT-America/GT-America-Standard-Bold-Trial.otf
          weight: 700
        - asset: assets/fonts/GT-America/GT-America-Standard-Regular-Trial.otf
          weight: 700
        - asset: assets/fonts/GT-America/GT-America-Standard-Medium-Trial.otf
          weight: 700
```

*Reminder: Remove all unnecessary comments to keep it clean.*

---

## Folder Structure

Below is a recommended folder structure. Your actual structure may vary based on project needs.

```
├── assets
│   ├── icons         // SVG and icon files
│   ├── images        // PNG, JPG, and other image assets
│   ├── fonts         // Custom fonts
│   └── animation     // Lottie / Adobe JSON files
│
├── lib
│   ├── config
│   │   ├── common_widgets
│   │   └── resources
│   │       └── util
│   │
│   ├── features
│   │   └── home
│   │       ├── data
│   │       │   ├── data_sources
│   │       │   ├── models
│   │       │   └── data_repository
│   │       ├── domain
│   │       │   ├── entities
│   │       │   ├── repository
│   │       │   └── usecases
│   │       └── presentation
│   │           ├── provider
│   │           ├── view
│   │           └── widgets
│   │
│   ├── routes
│   ├── injector.dart // For usecase, repository, or service injection
│   └── main.dart     // App entry point
│
├── pubspec.yaml
└── README.md
```

**Visual References**

- **Project Config Structure Example:**
  
  ![Project Config Structure](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-24%20at%2012.22.11%20PM.png?raw=true)

- **Feature Module Structure Example:**
  
  ![Feature Module Structure](https://github.com/saqib2st/Flutter_Base/blob/main/ss/Screenshot%202024-12-24%20at%2012.37.16%20PM.png?raw=true)

---

## Module Structure

A well-defined module structure ensures that each part of your application is organized, maintainable, and scalable. Below is the complete project structure module by module, along with each module's responsibilities:

### 1. Splash Module

**Responsibility:**
- Display the splash screen when the app launches.
- Perform initial checks such as:
  - Fetching the user's profile (`getProfile` API call).
  - Verifying if the app is active.
  - Determining if the user is already logged in to navigate to the appropriate screen.

**Structure:**
```
lib/features/splash/
├── data/
│   ├── data_sources/
│   │   └── splash_remote_data_source.dart
│   ├── models/
│   │   └── profile_model.dart
│   └── data_repository/
│       └── splash_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── profile.dart
│   ├── repository/
│   │   └── splash_repository.dart
│   └── usecases/
│       └── get_profile_usecase.dart
└── presentation/
    ├── provider/
    │   └── splash_provider.dart
    ├── view/
    │   └── splash_screen.dart
    └── widgets/
        └── splash_widget.dart
```

### 2. Auth Module

**Responsibility:**
- Handle all authentication-related functionalities such as login, registration, password reset, and social sign-ins.
- Manage authentication state and secure user sessions.

**Structure:**
```
lib/features/auth/
├── data/
│   ├── data_sources/
│   │   └── auth_remote_data_source.dart
│   ├── models/
│   │   └── user_model.dart
│   └── data_repository/
│       └── auth_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── user.dart
│   ├── repository/
│   │   └── auth_repository.dart
│   └── usecases/
│       ├── login_usecase.dart
│       ├── register_usecase.dart
│       └── logout_usecase.dart
└── presentation/
    ├── provider/
    │   └── auth_provider.dart
    ├── view/
    │   ├── login_screen.dart
    │   ├── register_screen.dart
    │   └── forgot_password_screen.dart
    └── widgets/
        ├── login_form.dart
        ├── registration_form.dart
        └── password_reset_form.dart
```

### 3. Profile Module

**Responsibility:**
- Manage user profile data including viewing and editing profile information.
- Handle profile-related API interactions and data persistence.

**Structure:**
```
lib/features/profile/
├── data/
│   ├── data_sources/
│   │   └── profile_remote_data_source.dart
│   ├── models/
│   │   └── profile_model.dart
│   └── data_repository/
│       └── profile_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── profile.dart
│   ├── repository/
│   │   └── profile_repository.dart
│   └── usecases/
│       ├── get_profile_usecase.dart
│       └── update_profile_usecase.dart
└── presentation/
    ├── provider/
    │   └── profile_provider.dart
    ├── view/
    │   └── profile_screen.dart
    └── widgets/
        ├── profile_view.dart
        └── edit_profile_form.dart
```

### 4. Home Module

**Responsibility:**
- Serve as the main dashboard or landing page after user authentication.
- Display key information, navigation options, and access to other modules.

**Structure:**
```
lib/features/home/
├── data/
│   ├── data_sources/
│   │   └── home_remote_data_source.dart
│   ├── models/
│   │   └── home_model.dart
│   └── data_repository/
│       └── home_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── home_entity.dart
│   ├── repository/
│   │   └── home_repository.dart
│   └── usecases/
│       └── fetch_home_data_usecase.dart
└── presentation/
    ├── provider/
    │   └── home_provider.dart
    ├── view/
    │   └── home_screen.dart
    └── widgets/
        ├── home_dashboard.dart
        └── home_navigation.dart
```

### 5. Settings Module

**Responsibility:**
- Allow users to configure app settings such as notifications, themes, language preferences, and account settings.
- Manage the persistence of user preferences.

**Structure:**
```
lib/features/settings/
├── data/
│   ├── data_sources/
│   │   └── settings_remote_data_source.dart
│   ├── models/
│   │   └── settings_model.dart
│   └── data_repository/
│       └── settings_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── settings.dart
│   ├── repository/
│   │   └── settings_repository.dart
│   └── usecases/
│       ├── get_settings_usecase.dart
│       └── update_settings_usecase.dart
└── presentation/
    ├── provider/
    │   └── settings_provider.dart
    ├── view/
    │   └── settings_screen.dart
    └── widgets/
        ├── notification_settings.dart
        ├── theme_selector.dart
        └── language_selector.dart
```

### 6. Notifications Module

**Responsibility:**
- Handle all aspects of in-app and push notifications.
- Manage notification settings and preferences.

**Structure:**
```
lib/features/notifications/
├── data/
│   ├── data_sources/
│   │   └── notifications_remote_data_source.dart
│   ├── models/
│   │   └── notification_model.dart
│   └── data_repository/
│       └── notifications_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── notification.dart
│   ├── repository/
│   │   └── notifications_repository.dart
│   └── usecases/
│       ├── fetch_notifications_usecase.dart
│       └── mark_as_read_usecase.dart
└── presentation/
    ├── provider/
    │   └── notifications_provider.dart
    ├── view/
    │   └── notifications_screen.dart
    └── widgets/
        ├── notification_list.dart
        └── notification_item.dart
```

### 7. Settings Module

**Responsibility:**
- Manage application settings, such as user preferences, theme selection, and other configurable options.
- Provide interfaces for users to update their settings.

**Structure:**
```
lib/features/settings/
├── data/
│   ├── data_sources/
│   │   └── settings_remote_data_source.dart
│   ├── models/
│   │   └── settings_model.dart
│   └── data_repository/
│       └── settings_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── settings.dart
│   ├── repository/
│   │   └── settings_repository.dart
│   └── usecases/
│       ├── get_settings_usecase.dart
│       └── update_settings_usecase.dart
└── presentation/
    ├── provider/
    │   └── settings_provider.dart
    ├── view/
    │   └── settings_screen.dart
    └── widgets/
        ├── theme_selector.dart
        └── language_selector.dart
```

### 8. Analytics Module

**Responsibility:**
- Track and analyze user interactions and app performance.
- Provide insights and reports based on collected data.

**Structure:**
```
lib/features/analytics/
├── data/
│   ├── data_sources/
│   │   └── analytics_remote_data_source.dart
│   ├── models/
│   │   └── analytics_model.dart
│   └── data_repository/
│       └── analytics_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── analytics.dart
│   ├── repository/
│   │   └── analytics_repository.dart
│   └── usecases/
│       └── track_event_usecase.dart
└── presentation/
    ├── provider/
    │   └── analytics_provider.dart
    ├── view/
    │   └── analytics_dashboard.dart
    └── widgets/
        └── analytics_graph.dart
```

### 9. Chat Module

**Responsibility:**
- Provide real-time messaging capabilities within the app.
- Manage chat threads, message storage, and user interactions.

**Structure:**
```
lib/features/chat/
├── data/
│   ├── data_sources/
│   │   └── chat_remote_data_source.dart
│   ├── models/
│   │   └── message_model.dart
│   └── data_repository/
│       └── chat_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── message.dart
│   ├── repository/
│   │   └── chat_repository.dart
│   └── usecases/
│       ├── send_message_usecase.dart
│       └── fetch_messages_usecase.dart
└── presentation/
    ├── provider/
    │   └── chat_provider.dart
    ├── view/
    │   └── chat_screen.dart
    └── widgets/
        ├── message_list.dart
        └── message_input.dart
```

### 10. Settings Module

**Responsibility:**
- Manage various app settings such as user preferences, theme options, and notification settings.
- Provide interfaces for users to customize their experience.

**Structure:**
```
lib/features/settings/
├── data/
│   ├── data_sources/
│   │   └── settings_remote_data_source.dart
│   ├── models/
│   │   └── settings_model.dart
│   └── data_repository/
│       └── settings_repository_impl.dart
├── domain/
│   ├── entities/
│   │   └── settings.dart
│   ├── repository/
│   │   └── settings_repository.dart
│   └── usecases/
│       ├── get_settings_usecase.dart
│       └── update_settings_usecase.dart
└── presentation/
    ├── provider/
    │   └── settings_provider.dart
    ├── view/
    │   └── settings_screen.dart
    └── widgets/
        ├── theme_selector.dart
        └── language_selector.dart
```

*Note: Ensure that each module follows the **Data**, **Domain**, and **Presentation** layers to maintain a clean architecture.*

---

## References

- **Estimating Time:** [How to Estimate Time for a Project](https://blog.flutter.wtf/how-to-estimate-time-for-a-project/)
- **Hygen Quick Start:** [Hygen Official Docs](https://www.hygen.io/docs/quick-start/)
- **Gitignore Generator:** [Toptal Gitignore](https://www.toptal.com/developers/gitignore/)
- **Base Templates:** [Flutter Base Templates](https://github.com/saqib2st/Flutter_Base/tree/main/_templates)

---

## Conclusion

This README aims to serve as a comprehensive guide to kickstart your Capital App in Flutter. By following the steps outlined here—from design, project setup, code generation with Hygen, and recommended folder structures—you’ll be well on your way to a clean, scalable, and maintainable codebase.

Feel free to adapt and extend this structure based on your team’s conventions and project requirements. Happy coding!

---

##MUST ADD YOUR APP DOCUMENTATION LIKE THIS
---

## Module Structure

The **Capital App** is composed of several modules, each responsible for specific functionalities within the application. Below is a detailed overview of each module, their responsibilities, and interactions.

### 1. Splash

**Responsibilities:**
- Display the splash screen during app launch.
- Perform mandatory API calls such as `getProfile` and `checkAppActivity`.
- Determine if the user is already logged in.
- Navigate to the appropriate screen based on the user's authentication status.
- Decide whether to show the popover screen.
- Initialize a singleton class to access global values.

**Functionality:**
- Ensures that essential data is fetched before the user interacts with the app.
- Handles initial app state checks and navigation flow.

### 2. Onboarding View

**Responsibilities:**
- Manage the onboarding process for new users.
- Facilitate app language selection.
- Display the welcome screen.
- Present three onboarding screens that describe the app's motto and key features.

**Functionality:**
- Guides new users through the app's purpose and functionalities.
- Allows users to select their preferred language for a personalized experience.

### 3. Auth

**Responsibilities:**
- Handle user authentication processes including login and signup.
- Manage login using email and password.
- Display error messages on login failures.
- Provide a forgot password feature using email.
- Show a succeeded forgot password screen upon successful request.
- Enable login via Google with appropriate screens.
- Facilitate signup using email, password, and confirm password fields.
- Verify user email addresses.
- Implement resend verification functionality with a 1-minute timer.
- On login, check for a verified and complete profile before navigating to the home screen.

**Functionality:**
- Ensures secure and user-friendly authentication mechanisms.
- Validates user credentials and manages authentication states.

### 4. Registration

**Responsibilities:**
- Gather all required user information to complete the user profile.
- Check if the app is being installed for the first time.
  - If first-time installation, navigate to the popover view.
  - Otherwise, navigate directly to the home screen.

**Functionality:**
- Completes the user's profile setup process.
- Determines the initial navigation flow based on installation status.

### 5. Root Navigation

**Responsibilities:**
- Set up the main view of the app.
- Serve as the root widget for the bottom navigation bar.
- Manage API calls based on the user's navigation taps.

**Functionality:**
- Controls the primary navigation structure of the app.
- Ensures seamless transitions between different sections of the app.

### 6. Home

**Responsibilities:**
- List opportunities available within the app.
- Display detailed information about each opportunity.
- Provide partner information related to the opportunities.
- Allow users to register for opportunities.
- Enable sharing and additional functionalities.

**Functionality:**
- Central hub for users to explore and engage with available opportunities.
- Facilitates user interactions with opportunities and partners.

### 7. My Opportunity

**Responsibilities:**
- Display past opportunities the user has engaged with.
- Show opportunities the user has registered for.
- Manage and display saved opportunities for quick access.

**Functionality:**
- Provides users with a personalized view of their engagement history and saved items.
- Enhances user experience by organizing opportunities based on user interactions.

### 8. Check In/Out

**Responsibilities:**
- Allow users to check in by scanning a valid QR code.
- Enable users to check out whenever they choose.
- Support multiple check-ins and check-outs.
- Display previous logs of user activity.
- Automatically check out users at day end.
- Show a timer for the active check-in period.

**Functionality:**
- Tracks user presence and activity within the app.
- Provides detailed logs and timing information for user check-ins.

### 9. Profile View

**Responsibilities:**
- Allow users to edit their profile information.
- Enable users to edit their interests.
- Provide options to change the app language.
- Display frequently asked questions (FAQ).
- Facilitate user logout.
- Allow users to delete their account.

**Functionality:**
- Manages user profile settings and preferences.
- Ensures users have control over their personal information and app settings.

---


Feel free to copy and use this enhanced README for your project. Let me know if you need any further assistance!
