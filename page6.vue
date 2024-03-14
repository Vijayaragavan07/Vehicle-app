<template>
    <div class="m-[5%]">
        <h1 class="text-[20px] font-bold mb-6">Greetings User 1</h1>
        <h1 class="text-[20px] font-bold mb-1">Required Services</h1>
        <hr class="mt-2" :style="{ borderWidth: '1px', borderColor: 'gray' }">
        <div class="ml-7 flex flex-row space-x-[250px]"> 
            <!-- col-1 -->
            <div class="flex flex-col space-y-4 mt-4"> 
                <div class="flex flex-row items-center space-x-3"> 
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="alignment" @change="handleShow('alignment')">
                    <label class="text-[18px]" for="alignment">Alignment</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="rotation" @change="handleShow('rotation')">
                    <label class="text-[18px]" for="rotation">Rotation</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="oil_change" @change="handleShow('oil_change')">
                    <label class="text-[18px]" for="oil_change">Oil Change</label>
                </div>  
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="balancing" @change="handleShow('balancing')">
                    <label class="text-[18px]" for="balancing">Balancing</label>
                </div>  
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="inflation" @change="handleShow('inflation')">
                    <label class="text-[18px]" for="inflation">Inflation</label>
                </div>    
            </div>            
            <!-- col-2 -->
            <div class="flex flex-col space-y-4 mt-4"> 
                <div class="flex flex-row items-center space-x-3"> 
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="puncture">
                    <label class="text-[18px]" for="puncture">Puncture</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="tyre_edge">
                    <label class="text-[18px]" for="tyre_edge">Tyre Edge</label>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="tyre_batch">
                    <label class="text-[18px]" for="tyre_batch">Tyre Batch</label>
                </div>  
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="mushroom_batch">
                    <label class="text-[18px]" for="mashroom_batch">Mushroom Batch</label>
                </div>
            </div>
            <!-- col-3 -->
            <div class="flex flex-col space-y-4 mt-4"> 
                <div class="flex flex-row items-center space-x-3"> 
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="ac_service" @change="handleShow('ac_service')">
                    <label class="text-[18px]" for="ac_service">AC Service</label>&emsp;
                    <select v-if="show.Ac" class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;">
                        <option value="" selected disabled hidden>Please select...</option>
                        <option value="good">Good</option>
                        <option value="better">Better</option>
                        <option value="not_good">Not Good</option>
                    </select>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="battery" @change="handleShow('battery')">
                    <label class="text-[18px]" for="battery">Battery</label>&emsp;&emsp;&emsp;
                    <select v-if="show.battery" class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;">
                        <option value="" selected disabled hidden>Please select...</option>
                        <option value="good">Good</option>
                        <option value="better">Better</option>
                        <option value="not_good">Not Good</option>
                    </select>
                </div>
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="wiper" @change="handleShow('wiper')">
                    <label class="text-[18px]" for="wiper">Wiper</label>&emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;
                    <select v-if="show.wiper" class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;">
                        <option value="" selected disabled hidden>Please select...</option>
                        <option value="good">Good</option>
                        <option value="better">Better</option>
                        <option value="not_good">Not Good</option>
                    </select>
                </div>  
                <div class="flex flex-row items-center space-x-3">
                    <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="car_wash" @change="handleShow('car_wash')">
                    <label class="text-[18px]" for="car_wash">Car Wash</label>&emsp;&emsp;
                    <select v-if="show.car_wash" class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;">
                        <option value="" selected disabled hidden>Please select...</option>
                        <option value="good">Good</option>
                        <option value="better">Better</option>
                        <option value="not_good">Not Good</option>
                    </select>
                </div>
            </div>                        
        </div>
        <hr class="mt-4" :style="{ borderWidth: '1px', borderColor: 'gray' }">
        <div class="flex flex-col space-y-1 ">
            <div v-if="show.alignment"> 
                <h1 class="text-[20px] mt-2 mb-2">Alignment Details</h1>
                <div class="flex flex-row space-x-[130px] ml-[55px]"> 
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="LA">Last Alignment (kms)</label>
                        <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="LA">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="NA">Next Alignment (kms)</label>
                        <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="NA">
                    </div>
                </div>
                <hr class="mt-6" :style="{ borderWidth: '1px', borderColor: 'gray' }">
            </div>
            <div v-if="show.rotation"> 
                <h1 class="text-[20px] mt-2 mb-2">Tyre Rotation Details</h1>
                <div class="flex flex-row space-x-[130px] ml-[55px]"> 
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="rim">Rim</label>
                        <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="rim">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="wheel">Wheel</label>
                        <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="wheel">
                    </div>
                </div>
                <hr class="mt-6" :style="{ borderWidth: '1px', borderColor: 'gray' }">
            </div>
            <div v-if="show.oil_change"> 
                <h1 class="text-[20px] mt-2 mb-2">Oil Service</h1>
                <div class="flex flex-row space-x-[130px] ml-[55px]"> 
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="oil_quality">Oil Quality</label>
                        <div> 
                            <select class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;" id="oil_quality">
                                <option value="" selected disabled hidden>Please select...</option>
                                <option value="good">Good</option>
                                <option value="ok">Ok</option>
                                <option value="change">Change</option>
                            </select>
                        </div>
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="oil_quantity">Oil Quantity</label>
                        <div> 
                            <select class="w-[338px] h-[52px] rounded-sm" style="border: 1px solid black;" id="oil_quantity">
                                <option value="" selected disabled hidden>Please select...</option>
                                <option value="max">Max</option>
                                <option value="normal">Normal</option>
                                <option value="min">Min</option>
                            </select>
                        </div>
                    </div>
                </div>
                <hr class="mt-6" :style="{ borderWidth: '1px', borderColor: 'gray' }">
            </div>
            <div v-if="show.balancing"> 
                <h1 class="text-[20px] mt-2 mb-2">Balancing Details</h1>
                <div class="flex flex-row space-x-[30px] ml-[55px]"> 
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="FL">Front-Left (gm)</label>
                        <input class="w-[300px] h-[52px] rounded-sm border-solid border border-black" type="text" id="FL">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="FR">Front-Right (gm)</label>
                        <input class="w-[300px] h-[52px] rounded-sm border-solid border border-black" type="text" id="FR">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="BL">Back-Left (gm)</label>
                        <input class="w-[300px] h-[52px] rounded-sm border-solid border border-black" type="text" id="BL">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="BR">Back-Right (gm)</label>
                        <input class="w-[300px] h-[52px] rounded-sm border-solid border border-black" type="text" id="BR">
                    </div>
                    <div class="flex flex-col space-y-1"> 
                        <label class="text-[16px]" for="ST">Spare Tyre (gm)</label>
                        <input class="w-[300px] h-[52px] rounded-sm border-solid border border-black" type="text" id="ST">
                    </div>
                </div>
                <hr class="mt-6" :style="{ borderWidth: '1px', borderColor: 'gray' }">
            </div>
            <div v-if="show.inflation"> 
                <h1 class="text-[20px] mt-2 mb-2">Inflation Details</h1>
                    <div class="flex flex-row space-x-[100px] ml-[55px]"> 
                        <div class="flex flex-col space-y-5">
                            <div class="flex flex-row space-x-3 mt-3"> 
                                <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="air" :checked="selectedCheckbox === 'air'" @change="handleCheckboxChange('air')">
                                <label class="text-[18px]" for="air">Air</label>
                            </div>
                            <div class="flex flex-row space-x-3"> 
                                <input class="w-5 h-5 rounded-sm border border-black bg-gray-200" type="checkbox" id="nitrogen" :checked="selectedCheckbox === 'nitrogen'" @change="handleCheckboxChange('nitrogen')">
                                <label class="text-[18px]" for="nitrogen">Nitrogen</label>
                            </div>
                        </div>
                        <div class="flex flex-row space-x-[100px]"> 
                            <div class="flex flex-col space-y-1"> 
                                <label class="text-[16px]" for="FTS">Front Tyres (psi)</label>
                                <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="FTS">
                            </div>
                            <div class="flex flex-col space-y-1"> 
                                <label class="text-[16px]" for="RTS">Rear Tyres (psi)</label>
                                <input class="w-[338px] h-[52px] rounded-sm border-solid border border-black" type="text" id="RTS">
                            </div>
                        </div>
                    </div>
                    <hr class="mt-6" :style="{ borderWidth: '1px', borderColor: 'gray' }">
            </div>     
        </div> 
    </div>
</template>

<script setup>
import {ref} from 'vue';

let selectedCheckbox = null;

const show=ref({
    Ac:false,
    battery:false,
    wiper:false,
    car_wash:false,
    alignment:false,
    rotation:false,  
    oil_change:false,
    balancing:false,
    inflation:false
})

function handleCheckboxChange(checkboxId) {
      if (this.selectedCheckbox === checkboxId) {
        selectedCheckbox = null;
      } else {
        selectedCheckbox = checkboxId;
        const otherCheckboxId =checkboxId === 'air' ? 'nitrogen' : 'air';
        const otherCheckbox = document.getElementById(otherCheckboxId);
        if (otherCheckbox) {
          otherCheckbox.checked = false;
        }
      }
    }
function handleShow(item){
    switch(item) {
        case 'ac_service':
            show.value.Ac = !show.value.Ac;
            break;
        case 'battery':
            show.value.battery = !show.value.battery;
            break;
        case 'wiper':
            show.value.wiper = !show.value.wiper;
            break;
        case 'car_wash':
            show.value.car_wash = !show.value.car_wash;
            break;
        case 'alignment':
            show.value.alignment = !show.value.alignment;
            break;
        case 'rotation':
            show.value.rotation = !show.value.rotation;
            break; 
        case 'oil_change':
            show.value.oil_change = !show.value.oil_change;
            break; 
        case 'balancing':
            show.value.balancing = !show.value.balancing;
            break; 
        case 'inflation':
            show.value.inflation = !show.value.inflation;
            break;                 
    }
}
</script>

<style lang="scss" scoped>

</style>