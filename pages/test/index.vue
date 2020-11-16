<template>
  <div>Component</div>
</template>

<script>
// import { useStore } from "vuex";
import { computed } from "vue";
export default {
  name: "App",
  setup(props) {
    // const store = useStore();

    return {
      // store
    };
  }
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
