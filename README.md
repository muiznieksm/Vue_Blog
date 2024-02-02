
# Vue.js Tech Blog Application

## Description

This Vue.js blog application offers a platform for users to read, post, and manage blog posts. It leverages Vue 3, Vue Router for navigation, and `json-server` as a mock backend for development purposes.

## Technologies Used

- **Vue.js 3**: The progressive JavaScript framework used for building user interfaces. [Vue.js Documentation](https://vuejs.org/)
- **Vue Router**: The official router for Vue.js. [Vue Router Documentation](https://router.vuejs.org/)
- **JSON Server**: Full fake REST API for testing and prototyping. [JSON Server Documentation](https://github.com/typicode/json-server)

## Project Setup

1. Clone the repository.
2. Install dependencies:
   ```
   npm install
   ```
3. Start the JSON server:
   ```
   npx json-server --watch -p 3000 db.json
   ```
4. Serve the application:
   ```
   npm run serve
   ```

## Features

- Create, read, update, and delete blog posts.
- Tag cloud for categorizing and filtering posts.
- Dynamic loading indicators.

## Project Structure

- `App.vue`: Main application component.
- `main.js`: Application entry point.
- `src/components/`: Vue components for different parts of the application.
- `src/composables/`: Reusable composition API functions.
- `src/assets/`: Static assets like images and styles.

## Building for Production

To create a production build, use:
```
npm run build
```

## Preview
<img src="preview.gif" alt="Preview GIF" style="max-width: 100%; height: auto; border: 2px solid #333;">
