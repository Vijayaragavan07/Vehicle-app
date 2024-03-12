<template>
  <div class="m-[5%]">
    <div>
      
      <div v-if="!selectImg" class="flex justify-center mt-[100px]"> 
        <div class="flex flex-row space-x-8"> 
          <img class="w-237 h-188" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0-FVVaYSFbTMXiC6bUW2O_Vzx0OyauBu_RwRlfQ7iIU5aMvWJ86dpdfvGL7eYThBSkQ0&usqp=CAU" alt="person-1" @click="handleImgSelection"/>
          <img class="w-237 h-188" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0-FVVaYSFbTMXiC6bUW2O_Vzx0OyauBu_RwRlfQ7iIU5aMvWJ86dpdfvGL7eYThBSkQ0&usqp=CAU" alt="person-2" @click="handleImgSelection"/>
          <img class="w-237 h-188" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0-FVVaYSFbTMXiC6bUW2O_Vzx0OyauBu_RwRlfQ7iIU5aMvWJ86dpdfvGL7eYThBSkQ0&usqp=CAU" alt="person-3" @click="handleImgSelection"/>
          <img class="w-237 h-188" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0-FVVaYSFbTMXiC6bUW2O_Vzx0OyauBu_RwRlfQ7iIU5aMvWJ86dpdfvGL7eYThBSkQ0&usqp=CAU" alt="person-4" @click="handleImgSelection"/>
        </div>
      </div>
      <div v-if="selectImg && !Auth" class="flex flex-col space-y-3 justify-center mt-[300px] items-center "> 
        <div v-if="incorrect" class="flex items-center p-4 mb-4 text-lg text-red-800 border border-red-300 rounded-lg bg-red-50 dark:bg-white-800 dark:text-red-800 dark:border-red-900" role="alert">
          <svg class="flex-shrink-0 inline w-5 h-5 me-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
            <path d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5ZM9.5 4a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM12 15H8a1 1 0 0 1 0-2h1v-3H8a1 1 0 0 1 0-2h2a1 1 0 0 1 1 1v4h1a1 1 0 0 1 0 2Z"/>
          </svg>
          <span class="sr-only">Info</span>&nbsp;
          <div>
            <span class="font-medium">Danger alert!</span> Change a few things up and try submitting again.
          </div>
        </div>
        <div> 
          <FeatherIcon name="arrow-left" class="w-10 h-10 absolute top-[8%] right-[93%] cursor-pointer" @click="selectImg=false"/>
        </div>
        <div class="flex flex-col item-center"> 
          <img class="w-[237.48px] h-[227.17px]" :src="data.selectedImgSrc" :alt="data.selectedAlt"/>
          <h1 class="text-center text-[25px]">User-1</h1>
        </div>
        <div> 
          <h1 class="text-[25px] text-black-500">Enter your 4 Digit Pin</h1>
        </div>
        <div class="flex flex-row space-x-8 mb-4"> 
          <input class="w-16 h-16 text-center border-2 border-black-500 bg-gray-200" type="password" v-model="pin1" maxlength="1" @input="focusNext($event, 1)">
          <input class="w-16 h-16 text-center border-2 border-black-500 bg-gray-200" type="password" v-model="pin2" maxlength="1" @input="focusNext($event, 2)">
          <input class="w-16 h-16 text-center border-2 border-black-500 bg-gray-200" type="password" v-model="pin3" maxlength="1" @input="focusNext($event, 3)">
          <input class="w-16 h-16 text-center border-2 border-black-500 bg-gray-200" type="password" v-model="pin4" maxlength="1" @input="focusNext($event, 4)">
        </div>
      </div>
      <!-- vj anna -->
    </div>
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';
  import {FeatherIcon} from 'frappe-ui'

  const selectImg = ref(false);
  const Auth = ref(false)
  const incorrect =ref(false);
  const currentstep = ref(0);

  const data = reactive({
    selectedImgSrc: '',
    selectedAlt: ''
  });

  const pin1 = ref('');
  const pin2 = ref('');
  const pin3 = ref('');
  const pin4 = ref('');

  function handleImgSelection(event) {
    selectImg.value = true;
    data.selectedImgSrc = event.target.src;
    data.selectedAlt = event.target.alt;
    console.log(data.selectedImgSrc, data.selectedAlt);
  }

  function focusNext(event, nextInput) {
    const target = event.target;
    if (target.value.length === 1) {
      const inputs = target.parentNode.querySelectorAll('input');
      if (nextInput < inputs.length) {
        inputs[nextInput].focus();
      }else{
        submitPin();
      }
    }
  }

  function submitPin() {
    if(pin1 && pin2 && pin3 && pin4){
      const pin = pin1.value + pin2.value + pin3.value + pin4.value;
      if(pin === "1234"){
        Auth.value=true;
      }
      else{
            incorrect.value=true;
            pin1.value = pin2.value = pin3.value = pin4.value = '';
            setTimeout(() => {
              incorrect.value = false;
            }, 3000);
        }
    }
    // Here you can add further logic to validate the pin or perform any other actions
  }
</script>

<style scoped>
/* Add your CSS styles here */
</style>
