<!-- 
    #Usage 
        add input element on parent template
            <input type="hidden" id="fb_link"/>
        inport this component
            import Copy from '@/components/Copy.vue';
        now ready to use
        <Copy :text="your_text_for_copy" id_name="#fb_link"/>
 -->
<script setup>
import { reactive } from 'vue';
import { mdiContentCopy  } from '@mdi/js';
import Icon from '@/components/Svg.vue';
import { sleep } from '@/helper';
let data = reactive({
    title:'copy',
})
let props = defineProps({
    text:{
        type: String,
        required: true
    },
    id_name:{
        type: String,
        required: true
    },
    action:{
        type: String,
        required: false
    }
});
const copy = async ()=> {
    let id = props.id_name;
    let fbLink = document.querySelector(id);
    fbLink.setAttribute('value',props.text);
    fbLink.setAttribute('type','text');
    fbLink.select()
    try {
        var successful = document.execCommand('copy');
        if(successful){
            data.title='copied';
            fbLink.setAttribute('type', 'hidden')
            window.getSelection().removeAllRanges()
            await sleep(3000);
            data.title='copy';
        }
    } catch (err) {
        alert('Oops, unable to copy');
    }
}
</script>
<template>
    <div :action="action" @click="copy" class="flex flex-row items-center border-2 px-2 py-1 rounded-md border-gray-400 select-none cursor-pointer hover:animate-pulse">
        <Icon :action="action" :path="mdiContentCopy" size="20"/>
        <span :action="action" >{{data.title}}</span>
    </div>
</template>