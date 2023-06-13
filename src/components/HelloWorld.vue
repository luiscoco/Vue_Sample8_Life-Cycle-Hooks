<template>
  <div>
    <p>{{ message }}</p>
    <button @click="incrementCounter">Increment Counter</button>
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted, onUpdated, onUnmounted, watchEffect } from "vue";

const useLifecycleHooks = () => {
  const message = ref("Hello, Vue 3!");
  const counter = ref(0);

  // Mounted hook
  onMounted(() => {
    console.log("Component mounted");
  });

  // Updated hook
  onUpdated(() => {
    console.log("Component updated");
  });

  // Unmounted hook
  onUnmounted(() => {
    console.log("Component unmounted");
  });

  // Watch effect hook
  watchEffect(() => {
    console.log("Counter changed:", counter.value);
  });

  // Custom method
  const incrementCounter = () => {
    counter.value++;
  };

  return {
    message,
    counter,
    incrementCounter,
  };
};

// Component setup function
const { message, counter, incrementCounter } = useLifecycleHooks();
</script>
