<script setup>
  import DarkMode from '@/components/DarkIcon.vue';
  import Logo from '@/components/Logo.vue';
  import Unlock from '../components/Unlock.vue';  
  // const auth=reactive('');
</script>
<template>
    <div class="container mx-auto">
      <DarkMode/>
      <Logo/>
      <Unlock/>
    </div>
    <input type="hidden" id="copy_text"/>
</template>

