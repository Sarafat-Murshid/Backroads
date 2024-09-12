# Backroads App React Conversion Guide

This guide provides a detailed walk-through of how to create a React app for the Backroads App using an existing HTML/CSS project as a foundation.

## Table of Contents

1. [Initial Setup](#initial-setup)
2. [Basic React App Structure](#basic-react-app-structure)
3. [Copying Assets & Initial Setup](#copying-assets--initial-setup)
4. [Setting Up Components](#setting-up-components)
5. [Fixing Images](#fixing-images)
6. [Smooth Scrolling](#smooth-scrolling)
7. [Refactor Repeating Code](#refactor-repeating-code)
8. [Component Breakdown](#component-breakdown)
9. [Final Touches](#final-touches)
10. [Optional Enhancements](#optional-enhancements)
11. [Deployment on Netlify](#deployment-on-netlify)

## Initial Setup

1. Clone or copy the HTML/CSS project.
2. Set up a new React project:
   ```
   npx create-react-app@latest backroads-app
   ```
3. Run the development server:
   ```
   npm start
   ```

## Basic React App Structure

1. Modify `src/index.js` to render the component.
2. Import global styles in `index.js`.
3. Refactor the `App.js` file to initially contain:
   ```jsx
   function App() {
     return <h1>Backroads App</h1>;
   }
   export default App;
   ```

## Copying Assets & Initial Setup

1. Copy images from the HTML project to `src`.
2. Move `favicon.ico` to the `public` folder.
3. Update `index.css` with the styles from the HTML project's `styles.css` file.

## Setting Up Components

1. Create a `components` folder and the following files:
   - `Navbar.js`
   - `Hero.js`
   - `About.js`
   - `Services.js`
   - `Tours.js`
   - `Footer.js`
2. Move the corresponding code from `App.js` to these components.
3. Import and render these components in `App.js`.

## Fixing Images

Use `import` to reference images properly within components:

```jsx
import logo from '../images/logo.svg';
```

## Smooth Scrolling

Add smooth scrolling by modifying the HTML and CSS:

```css
html {
  scroll-behavior: smooth;
}
.section {
  scroll-margin-top: 4rem;
}
```

## Refactor Repeating Code

1. Create a `data.js` file to store repeating data:
   ```javascript
   export const pageLinks = [
     { id: 1, href: '#home', text: 'home' },
     { id: 2, href: '#about', text: 'about' },
     // ...more links
   ];
   ```
2. Use `map` to render the data dynamically in components.

## Component Breakdown

Set up additional components such as `Title.js` for reusable section titles and `PageLinks.js` for rendering page links.

## Final Touches

1. Update Hero, About, Services, and Footer components.
2. Ensure the current year is displayed in the footer:
   ```jsx
   {new Date().getFullYear()}
   ```

## Optional Enhancements

1. Refactor code into smaller components:
   - `Tour.js`
   - `Service.js`
   - `SocialLink.js`
   - `PageLink.js`
2. Address any warnings to avoid deployment issues.

## Deployment on Netlify

### Create a GitHub Repository

1. Initialize a git repository and push the project to GitHub:
   ```
   git init
   git add .
   git commit -m "initial commit"
   git remote add origin git@github.com:your-profile/backroads-app.git
   git push -u origin main
   ```

### Deploy to Netlify

1. Connect your GitHub repository to your Netlify account for automatic builds.

### Handle Build Warnings

Update `package.json` to avoid Netlify treating warnings as errors:

```json
"scripts": {
  "start": "react-scripts start",
  "build": "CI= react-scripts build"
}
```

This guide serves as a structured roadmap for converting the Backroads HTML/CSS project into a fully functional React app.
