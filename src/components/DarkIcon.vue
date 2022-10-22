<script setup>
  import { mdiLightbulbOnOutline, mdiLightbulbOffOutline } from '@mdi/js';
  import Icon from '@/components/Svg.vue';
  import { useStore } from 'vuex';
  const store = useStore();

</script>
<template>
    <div class="h-20 flex flex-row justify-end items-center">
        <!-- onDark -->
        <div @click="store.dispatch('toggleDark')" v-if="store.getters.getDark" class="border-2 border-gray-200 text-gray-200 w-10 h-10 flex flex-row justify-center items-center rounded-full cursor-pointer hover:opacity-50">
            <Icon :path="mdiLightbulbOnOutline"/>
        </div>
        <!-- onlight -->
        <div v-else @click="store.dispatch('toggleDark')" class="border-2 border-gray-500 text-gray-500 w-10 h-10 flex flex-row justify-center items-center rounded-full cursor-pointer hover:opacity-50">
            <Icon :path="mdiLightbulbOffOutline"/>
        </div>
    </div>
</template>