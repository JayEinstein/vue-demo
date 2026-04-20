# Code Wiki

## 1. Project Overview
This project is a **single-page Vue.js application** demonstrating core Vue Router concepts including nested routes, dynamic routes, and component organization.

## 2. Technology Stack
- **Frontend Framework**: Vue 2.4.2
- **Routing**: Vue Router 2.7.0
- **HTTP Client**: Vue Resource 1.3.4
- **UI Framework**: Bootstrap 3.3.7
- **Build Tool**: Webpack 2.6.1

## 3. Directory Structure
```
/workspace
├── src/
│   ├── assets/
│   │   └── logo.png
│   ├── components/
│   │   ├── OursSub/
│   │   │   ├── NewsSub/
│   │   │   │   └── NewsParame.vue
│   │   │   ├── Message.vue
│   │   │   └── News.vue
│   │   ├── About.vue
│   │   ├── Hello.vue
│   │   ├── Ours.vue
│   │   ├── Sub.vue
│   │   └── SubTwo.vue
│   ├── router/
│   │   └── index.js
│   ├── App.vue
│   └── main.js
├── build/
├── config/
├── static/
├── test/
├── index.html
└── package.json
```

## 4. Core Modules

### 4.1. Entry Point
- **File**: [main.js](file:///workspace/src/main.js)
- **Responsibilities**:
  - Initializes Vue application
  - Registers Vue Router and Vue Resource plugins
  - Configures application routes
  - Imports Bootstrap CSS/JS
  - Mounts root Vue instance

### 4.2. Root Component
- **File**: [App.vue](file:///workspace/src/App.vue)
- **Responsibilities**:
  - Main layout component
  - Provides navigation links
  - Renders active route via `<router-view>`
  - Uses `<keep-alive>` to cache components

### 4.3. Routing Configuration
There are two router configuration files:
- **Actual Router**: Configured directly in [main.js](file:///workspace/src/main.js) (lines 20‑50)
- **Template Router**: [router/index.js](file:///workspace/src/router/index.js) (unused in current setup)

**Route Hierarchy**:
```
/
├── /Hello (Hello.vue)
├── /About (About.vue)
└── /Ours (Ours.vue)
    ├── /Ours/News (News.vue)
    │   └── /Ours/News/NewsParame/:id (NewsParame.vue)
    └── /Ours/Message (Message.vue)
```

## 5. Key Components

### 5.1. Hello.vue
- **File**: [Hello.vue](file:///workspace/src/components/Hello.vue)
- **Responsibilities**:
  - Fetches geolocation data using Tencent Maps API
  - Displays address, latitude, and longitude
  - Imports and renders `Sub` and `SubTwo` components
- **Key Methods**:
  - `mounted()`: Sends POST request to fetch geolocation data

### 5.2. About.vue
- **File**: [About.vue](file:///workspace/src/components/About.vue)
- **Responsibilities**:
  - Displays a list of categories
  - Renders `Sub` and `SubTwo` child components

### 5.3. Ours.vue
- **File**: [Ours.vue](file:///workspace/src/components/Ours.vue)
- **Responsibilities**:
  - Parent component for nested routes (News/Message)
  - Provides navigation between child routes
  - Renders active child component via `<router-view>`

### 5.4. News.vue
- **File**: [News.vue](file:///workspace/src/components/OursSub/News.vue)
- **Responsibilities**:
  - Parent component for dynamic news routes
  - Provides navigation to news items (01/02)
  - Renders `NewsParame` component with dynamic `id` parameter
- **Key Methods**:
  - `fetchData()`: Logs child components

### 5.5. NewsParame.vue
- **File**: [NewsParame.vue](file:///workspace/src/components/OursSub/NewsSub/NewsParame.vue)
- **Responsibilities**:
  - Displays dynamic news content based on route parameter
  - Watches for route changes to update content
- **Key Features**:
  - Uses `$route.params.id` to get dynamic parameter
  - Watches `$route` to react to parameter changes

### 5.6. Message.vue
- **File**: [Message.vue](file:///workspace/src/components/OursSub/Message.vue)
- **Responsibilities**:
  - Simple component displaying "Message World!"

### 5.7. Sub.vue & SubTwo.vue
- **Files**: [Sub.vue](file:///workspace/src/components/Sub.vue), [SubTwo.vue](file:///workspace/src/components/SubTwo.vue)
- **Responsibilities**:
  - Simple child components used in `Hello.vue`

## 6. Dependencies
- **Production**:
  - vue@^2.4.2
  - vue-router@^2.7.0
  - vue-resource@^1.3.4
  - bootstrap@^3.3.7
  - jquery@^3.2.1
- **Development**:
  - webpack & related loaders
  - babel for transpilation
  - eslint for linting
  - karma & nightwatch for testing

## 7. How to Run
```bash
# Install dependencies
npm install

# Start development server at localhost:8080
npm run dev

# Build for production
npm run build

# Run tests
npm test
```
