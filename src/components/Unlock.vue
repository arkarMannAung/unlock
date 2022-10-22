<script setup>
    import { reactive } from 'vue';
    import { useStore } from 'vuex';
    const store = useStore();
    const data=reactive({
      auth: '',
      request: '',
      unlock: ''
    });
    const copy = async (text)=> {
        let unlock = document.getElementById('copy_text');
        unlock.setAttribute('value',text);
        unlock.setAttribute('type','text');
        unlock.select()
        try {
            var successful = document.execCommand('copy');
            if(successful){
                unlock.setAttribute('type', 'hidden')
                window.getSelection().removeAllRanges()
            }
        } catch (err) {
            alert('Oops, unable to copy');
        }
    }
    const unlock = ()=>{
        store.dispatch('unlock',{ 
            token: data.auth,
            request: data.request
        })
        .then(ans=>{
            data.unlock=ans;
            copy(ans);
        })
        .catch(err=>data.unlock=err);
    }
    const style = ()=> store.getters.getToken==true?'md:grid-cols-2':'md:grid-cols-3';
    const contact = [
        {
            title: 'N5N4 $',
            copy: 'n5n4 kanji app အတွက်ဆိုရင် 5000 mmk ပါ။ (Life Time) သုံးလို့ရပြီးတော့ App တစ်ခုလုံး unlock ဖြစ်သွားမှာပါ။ payment kpay/ wave နဲ့ရနိုင်ပါတယ်ခင်ဗျ။'
        },
        {
            title: 'N4 $',
            copy: 'n4 kanji app အတွက်ဆိုရင် 3000 mmk ပါ။ (Life Time) သုံးလို့ရပြီးတော့ App တစ်ခုလုံး unlock ဖြစ်သွားမှာပါ။ payment kpay/ wave နဲ့ရနိုင်ပါတယ်ခင်ဗျ။'
        },
        {
            title: 'N5 $',
            copy: 'n5 kanji app အတွက်ဆိုရင် 2000 mmk ပါ။ (Life Time) သုံးလို့ရပြီးတော့ App တစ်ခုလုံး unlock ဖြစ်သွားမှာပါ။ payment kpay/ wave နဲ့ရနိုင်ပါတယ်ခင်ဗျ။'
        },
        {
            title: 'JLPT N3 $',
            copy: 'JLPT N3 Old Q web app အတွက်ဆိုရင် 5000 mmk ပါ။ (Life Time) သုံးလို့ရပြီးတော့ မေးခွန်းဟောင်းအားလုံး unlock ဖြစ်သွားမှာပါ။ payment kpay/ wave နဲ့ရနိုင်ပါတယ်ခင်ဗျ။'
        },
        {
            title: 'JLPT N4 $',
            copy: 'JLPT N4 Old Q web app အတွက်ဆိုရင် 5000 mmk ပါ။ (Life Time) သုံးလို့ရပြီးတော့ မေးခွန်းဟောင်းအားလုံး unlock ဖြစ်သွားမှာပါ။ payment kpay/ wave နဲ့ရနိုင်ပါတယ်ခင်ဗျ။'
        },
        {
            title: 'Pay',
            copy: 'Kpay,Wave Pay Arkar Mann Aung 09780132792'
        },
        {
            title: 'cb acc',
            copy: 'CB Account: 0109600500148717 Arkar Mann Aung'
        },
        {
            title: 'thank',
            copy: 'ပို့ပေးတဲ့ ကုတ်ထည့်ပြီး unlock လုပ်ပေးပါခင်ဗျ။ Lifetime မို့လို့ App ဖျက်မိတာ ဖုန်းပြောင်းတာတို့ဆိုရင် unlock ထပ်လုပ်လို့ရပါတယ်။ တစ်ခြားသူတွေအတွက် အထောက်အကူဖြစ်စေဖို့အတွက် page မှာ review လေးတွေ ရေးပေးလို့ရပါတယ်ခင်ဗျ။ ကျေးဇူးတင်ပါတယ်ခင်ဗျ။'
        }
    ];
</script>
<template>
    <div class="grid grid-cols-1 mt-12 md:mt-20 gap-6 md:gap-12" :class="style()">
        <div v-if="store.getters.getToken!=true" class="flex flex-row items-center justify-center">
          <label for="auth" class="mr-4 w-16">Token:</label>
          <input v-model="data.auth" id="auth" type="password" class="text-black px-2 py-2 border-2 border-gray-500 dark:border-white rounded-lg"/>
        </div>
        <div class="flex flex-row items-center justify-center">
          <label for="request" class="mr-4 w-16">Request:</label>
          <input v-model="data.request" id="request" type="text" maxlength="8" class="text-black px-2 py-2 border-2 border-gray-500 dark:border-white rounded-lg"/>
        </div>
        <div class="flex flex-row items-center justify-center">
          <label for="unlock" class="mr-4 w-16">Unlock:</label>
          <input v-model="data.unlock" id="unlock" type="text" class="text-black px-2 py-2 border-2 border-gray-500 dark:border-white rounded-lg"/>
        </div>
    </div>
    <div class="flex flex-row justify-center mt-12 md:mt-18">
        <div @click="unlock" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800 select-none cursor-pointer">Unlock</div>
    </div>
    <div class="grid grid-cols-3 mt-6 md:mt-12 gap-4 md:gap-8">
        <div @click="copy(item.copy)" v-for="(item, index) in contact" :key="index" class="flex flex-row justify-center cursor-pointer select-none">
          <div class="border-2 border-gray-500 px-2 py-1 rounded-md">{{ item.title }}</div>
        </div>
      </div>

      <div class="my-20"></div>
</template>