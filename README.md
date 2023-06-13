# vue-life-cycle-hooks

In Vue 3, lifecycle hooks are functions that allow you to perform actions at different stages of a component's lifecycle. These hooks are called automatically by Vue at specific points during the component's creation, update, and destruction.

Here are the lifecycle hooks in Vue 3:

## beforeCreate: 
This hook is called synchronously immediately after the component instance is created but before data observation and event/watcher setup. At this stage, data and methods are not available.

## created: 
This hook is called synchronously after the component instance has been created. Data observation, computed properties, methods, and watchers have been set up. However, the DOM is not yet available.

## beforeMount: 
This hook is called right before the component is mounted to the DOM. The template has been compiled, and the component is about to be rendered. You can access the DOM and modify it in this hook.

## mounted: 
This hook is called after the component has been mounted to the DOM. At this stage, the component's template is rendered, and you can interact with the rendered DOM and access component references.

## beforeUpdate: 
This hook is called when a reactive property used by the component has changed, and the component is about to re-render. You can perform pre-update actions in this hook. Note that you cannot modify data properties in this hook, as it is intended for observing changes.

## updated: 
This hook is called after the component has been re-rendered due to a reactive property change. You can access and interact with the updated DOM in this hook. Similar to mounted, you should be cautious about modifying data properties within this hook.

## beforeUnmount: 
This hook is called right before the component is unmounted from the DOM. You can perform cleanup tasks, such as canceling timers or removing event listeners, in this hook.

## unmounted: 
This hook is called after the component has been unmounted from the DOM. At this stage, the component is no longer part of the active component tree.

In addition to these hooks, Vue 3 also introduces the errorCaptured hook, which allows you to capture and handle errors that occur during rendering or in child components.

It's worth noting that in Vue 3, the beforeDestroy and destroyed hooks from Vue 2 have been replaced with beforeUnmount and unmounted, respectively, to align with the terminology used in the Composition API.

These lifecycle hooks provide you with the ability to perform specific actions at different stages of a component's lifecycle, making it easier to handle initialization, updates, and cleanup in your Vue 3 applications.

Here's an example of a complex code sample showcasing the capabilities of lifecycle hooks in Vue 3:

```vue
<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="updateMessage">Update Message</button>
    <button @click="destroyComponent">Destroy Component</button>
  </div>
</template>

<script>
import { ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, onUnmounted } from 'vue';

export default {
  name: 'MyComponent',
  setup() {
    const message = ref('Hello, Vue 3!');
  
    // Lifecycle hooks
    onBeforeMount(() => {
      console.log('Before Mount');
    });
  
    onMounted(() => {
      console.log('Mounted');
    });
  
    onBeforeUpdate(() => {
      console.log('Before Update');
    });
  
    onUpdated(() => {
      console.log('Updated');
    });
  
    onBeforeUnmount(() => {
      console.log('Before Unmount');
    });
  
    onUnmounted(() => {
      console.log('Unmounted');
    });
  
    // Methods
    const updateMessage = () => {
      message.value = 'Updated Message';
    };
  
    const destroyComponent = () => {
      // Destroy the component manually
      // You can also use v-if in the template to conditionally render the component
      // and let Vue handle the destruction automatically
      this.$destroy();
    };
  
    return {
      message,
      updateMessage,
      destroyComponent
    };
  }
};
</script>
```

In this code sample, we have a Vue component named MyComponent that showcases the usage of different lifecycle hooks. The component has a reactive property message which is initially set to 'Hello, Vue 3!'.

Within the setup() function, we define the lifecycle hooks using the onBeforeMount, onMounted, onBeforeUpdate, onUpdated, onBeforeUnmount, and onUnmounted functions provided by the Vue 3 Composition API. Each hook logs a message to the console, indicating the corresponding lifecycle stage.

The component also defines two methods: updateMessage and destroyComponent. updateMessage updates the value of the message property when the "Update Message" button is clicked. destroyComponent manually destroys the component when the "Destroy Component" button is clicked.

You can observe the console logs and the behavior of the component as it goes through the different lifecycle stages, gets updated, and is eventually destroyed.

Remember to import the necessary functions from the vue package in order to use the lifecycle hooks and the ref function for reactive properties.

This example demonstrates the flexibility and power of Vue 3's lifecycle hooks to perform actions at specific points in a component's lifecycle, allowing you to control and customize your component's behavior accordingly.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
