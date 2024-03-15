<template>
    <div class="m-[5%]">
        <h1 class="text-[20px] font-bold mb-6">Greetings User 1</h1>
        <h1 class="text-[20px] font-bold mb-1">5 Points Checkup</h1>
        <hr class="mt-2 " :style="{ borderWidth: '2px', borderColor: 'gray' }"> 
        <div class="flex flex-col space-y-5 mt-4  p-2 bg-gray-200 rounded-lg shadow-md transition-shadow duration-300 hover:shadow-lg" v-for="(tyreData, index) in tyreDatas" :key="index"> 
            <div class="flex flex-row space-x-[70px]"> 
                <div class="flex flex-col space-y-1 ml-4">
                    <label class="mt-2" :for="'tyre'+index">Tyre</label>
                    <select class="w-[338px] h-[52px] rounded-sm" v-model="tyreData.tyre" :id="'type'+index" style="border: 1px solid black;" @change="updateTyreData(index)">
                        <option value="" selected disabled hidden>Please select...</option>
                        <option value="Front-Left">Front-Left</option>
                        <option value="Front-Right">Front-Right</option>
                        <option value="Back-Left">Back-Left</option>
                        <option value="Back-Right">Back-Right</option>
                        <option value="Stephanie">Stephanie</option>
                    </select>
                </div>
                <div class="flex flex-col space-y-1">
                    <label class="mt-2" :for="'RTD'+index">Remaining Tread Depth</label>
                    <input v-model="tyreData.depth" class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" :id="'RTD'+index" @change="updateTyreData(index)">
                </div>
                <div class="flex flex-col space-y-1">
                    <label class="mt-2" :for="'TP'+index">Tyre Pressure (psi)</label>
                    <input v-model="tyreData.pressure" class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" :id="'TP'+index" @change="updateTyreData(index)">
                </div>
                <div class="flex flex-col space-y-1">
                    <label class="mt-2" :for="'COM'+index">Comment</label>
                    <input v-model="tyreData.comment" class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" :id="'COM'+index" @change="updateTyreData(index)">
                </div>
                <div> 
                    <FeatherIcon name="trash-2" class="mt-11 w-8 h-8 cursor-pointer text-red-500" @click="deleteTyre(index)" />
                </div>
            </div>
            <div class="flex flex-row space-x-20">
                <div class="flex flex-row items-center space-x-3 ml-4">
                    <input v-model="tyreData.wear" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="IW">
                    <label for="IW">Irregular Wear</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input v-model="tyreData.cut" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="C/D">
                    <label for="C/D">Cut/Damage</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input v-model="tyreData.mark" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="RFM">
                    <label for="RFM">Run Flat MARK</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input v-model="tyreData.damage" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="DM">
                    <label for="DM">Damage</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input v-model="tyreData.bulge" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="BL">
                    <label for="BL">Bulge</label>
                </div>                        
                <div class="flex flex-row items-center space-x-3">
                    <input v-model="tyreData.puncture" class="rounded-sm border border-black bg-gray-200" type="checkbox" id="PUN">
                    <label for="PUN">Puncture</label>
                </div>  
            </div>
            <!-- <hr class="mt-2" :style="{ borderWidth: '1px', borderColor: 'gray' }">  -->
        </div>
        <button s class="mt-3 ml-[1570px] text-[25px] w-[150px] h-[50px] bg-blue-500 rounded-lg" @click="addTyre">Add </button>
        <!-- <button @click="fetchData">Fetch Data</button> -->
    </div>
</template>

<script setup>
import { ref } from 'vue';
import {FeatherIcon} from 'frappe-ui'
// import {MdCard} from 'vue-material/dist/components'
import axios from 'axios';

// const data = ref(null);

// const fetchData = async () => {
//   try {
//     const response = await axios.get('/api/method/tyre/api/custom_test_api');
//     data.value = response.data;
//     console.log(data.value);
//   } catch (error) {
//     console.error('Error fetching data:', error);
//   }
// };

const tyreDatas = ref([{ tyre: '', depth: '', pressure: '', comment: '', wear: false, cut: false, mark: false, damage: false, bulge: false, puncture: false }]);

const addTyre = () => {
    tyreDatas.value.push({ tyre: '', depth: '', pressure: '', comment: '', wear: false, cut: false, mark: false, damage: false, bulge: false, puncture: false });
};

const updateTyreData = (index) => {
    const tyre = tyreDatas.value[index];
    console.log('Updated tyre data:', tyre);
    console.log(tyreDatas.value);
};

const deleteTyre = (index) => {
    tyreDatas.value.splice(index, 1);
};

</script>

<style lang="scss" scoped>

</style>
