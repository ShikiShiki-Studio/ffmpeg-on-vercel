# @lunesia/tsconfig

Shared TypeScript configurations for the Lunesia project.

## Usage

This package contains predefined TypeScript configurations for different types of projects in the Lunesia monorepo.

### Available Configurations

- `base.json`: Base configuration for all projects
- `node-library.json`: Configuration for Node.js libraries (server-side only)
- `react-library.json`: Configuration for React libraries that can be used in web
- `react-native.json`: Configuration for React Native compatible libraries
- `next.json`: Configuration for Next.js applications

### Using in Packages

For a Node.js only package (like firebase-admin):

```json
{
  "extends": "@lunesia/tsconfig/node-library.json",
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist"
  },
  "include": ["src/**/*"]
}
```

For a shared package that works on both web and React Native:

```json
{
  "extends": "@lunesia/tsconfig/react-library.json",
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist"
  },
  "include": ["src/**/*"]
}
```

For a React Native specific package:

```json
{
  "extends": "@lunesia/tsconfig/react-native.json",
  "compilerOptions": {
    "rootDir": "./src",
    "outDir": "./dist"
  },
  "include": ["src/**/*"]
}
```

## Package Compatibility

When developing packages within the monorepo, consider which environment they'll be used in:

- **Server-only packages**: Use `node-library.json` (Example: firebase-admin, tts-client)
- **Shared packages**: Use `react-library.json` with careful attention to available APIs (Example: types, firebase-config)
- **React Native specific**: Use `react-native.json` (Example: mobile app specific components)
