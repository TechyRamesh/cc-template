# Project Name

## Project Details
This project is a Flutter application designed to [briefly describe the purpose of your project]. It aims to [mention the main goal or feature].

## Links
- **GitHub Repository**: [GitHub Repo URL](https://github.com/your-username/your-repo)
- **Figma Design**: [Figma Link](https://www.figma.com/your-design-link)
- **Jira Issue Tracker**: [Jira Link](https://your-jira-instance.atlassian.net/your-project)

## Development Setup

### Prerequisites
- Flutter SDK: `v3.32.8`
- Dart Version: `3.8.1`
- Node.js: `v16.x` or higher (for Husky Git hooks)

Make sure you have Flutter, Dart, and Node.js set up on your machine before you proceed with the setup. You can install Flutter from [flutter.dev](https://flutter.dev/docs/get-started/install) and Node.js from [nodejs.org](https://nodejs.org/).

### Run the Project

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/your-username/your-repo.git
    cd your-repo
    ```

2. **Change package name**:
   Since this is template not a project. So you may need to change the package name of this project.

   Run this command to make shell script executable:
    ```bash
    chmod +x package_name_change.sh
    ```

   To change the package name, use this command and replace package name with your new package name (write.new.package.name):
    ```bash
    ./package_name_change.sh pacakgeName
    ```

3. **Install Dependencies**:
   Run the following command to get all the dependencies required by the project:
    ```bash
    flutter pub get
    ```

4. **Setup Git Hooks (Husky)**:
   This project uses Husky for Git hooks to ensure code quality. Install Node.js dependencies and setup hooks:
    ```bash
    npm install
    ```
   This will automatically setup the following Git hooks:
   - **pre-commit**: Runs code formatting and static analysis
   - **commit-msg**: Validates commit message format (conventional commits)
   - **pre-push**: Runs tests before pushing to remote

5. **Generate Code for JSON Serialization**:
   Since this project uses JSON serialization (via `json_serializable` package), you need to run the `build_runner` command to generate code for your models.

   Run this command to generate the necessary code:
    ```bash
    dart run build_runner build
    ```

   If you are making changes to your models and want to regenerate the code, use this command:
    ```bash
    dart run build_runner watch
    ```

6. **Remove Firebase (If Applicable)**:
   Since this project uses firebase, if don't need it, you can remove it using following command.

   Run this command to make shell script executable:
    ```bash
    chmod +x remove_firebase.sh
    ```

   To remove the firebase from project, use this command:
    ```bash
    ./remove_firebase.sh
    ```

7. **Run the App**:
   To run the app on an emulator or connected device:
    ```bash
    flutter run
    ```

### Build the App

1. **Build for Android**:
   To build the app for an Android release:
    ```bash
    flutter build apk --release --no-tree-shake-icons
    ```

2. **Build for iOS**:
   To build the app for iOS:
    ```bash
    flutter build ios --release
    ```

## Git Hooks & Code Quality

This project uses **Husky** to enforce code quality through Git hooks:

### Available Git Hooks:
- **pre-commit**: 
  - Automatically formats staged Dart files and re-stages them
  - Runs static analysis (per-file if supported, otherwise full analysis)
  - Safely handles filenames with spaces and special characters
  - Provides clear error messages and exits on failures
- **commit-msg**: Validates commit messages follow conventional commits format
- **pre-push**: 
  - Runs comprehensive static analysis before pushing
  - Detects Flutter repositories automatically
  - Optional Flutter analyzer for additional safety

### NPM Scripts:
You can use these convenient npm scripts for common Flutter tasks:

```bash
# Code formatting and analysis
npm run format          # Format all Dart files
npm run analyze         # Run static analysis
npm run test           # Run tests

# Build commands
npm run build:android  # Build Android APK
npm run build:ios     # Build iOS app

# Development utilities
npm run clean          # Clean and get dependencies
npm run deps:update    # Update dependencies
npm run deps:get       # Get dependencies
npm run codegen        # Generate code (JSON serialization)
```

### Commit Message Format:
This project follows [Conventional Commits](https://www.conventionalcommits.org/) format:
```
<type>(<scope>): <description>

Examples:
feat(auth): add login functionality
fix(ui): resolve button alignment issue
docs(readme): update setup instructions
```

## Notes
- Ensure that you have the appropriate development environment set up for Android or iOS.
- For further instructions on how to configure your device or emulator, refer to [Flutter Installation Guide](https://flutter.dev/docs/get-started/install).
- If you encounter issues with code generation (e.g., errors with `build_runner`), try clearing any generated files by running the following:
    ```bash
    dart run build_runner clean
    ```
- Git hooks will automatically run when you commit or push code. Make sure your code passes all checks before committing.

### Enhanced Hook Features:
- **Smart File Detection**: Only processes staged Dart files for efficiency
- **Auto-formatting**: Automatically formats code and re-stages formatted files
- **Robust Error Handling**: Clear error messages and proper exit codes
- **Flutter Detection**: Automatically detects Flutter projects and applies appropriate checks
- **Safe Filename Handling**: Properly handles files with spaces and special characters
- **Per-file Analysis**: Uses per-file analysis when supported by Dart SDK
- **Comprehensive Logging**: Detailed output showing what's being processed
