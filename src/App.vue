<script setup>
  import { onMounted } from 'vue';
  import { useStore } from 'vuex';
  const store = useStore();
  onMounted(()=>{
    store.dispatch('init');
  });
</script>
<template>
  <div class="relative flex flex-col h-screen overflow-auto scrollbar-hide">
   <!-- bg-white text-base dark:bg-gray-800 dark:text-gray-100 -->
    <router-view/>
  </div>
</template>