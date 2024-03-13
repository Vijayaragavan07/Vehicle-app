<template>
  <div>
    <div class="m-10" v-if="currentstep === 0">
      <h4 class="text-2xl font-bold">Greetings User 1</h4>
      <div class="flex justify-center m-5">
        <input type="text" class="bg-gray-300 p-2 border border-gray-400">
        <button class="bg-blue-400 text-base p-3 rounded-lg ml-3">Search</button>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <div>
          <h4 class="text-[20px] font-bold">Vehicle Details</h4>
          <hr class="dark-hr">
          <div class="grid grid-cols-2 gap-4">
            <div>
              <p class="mt-3">Vehicle Brand&emsp;: Tata</p>
              <p class="mt-3">Vehicle Type&emsp;&nbsp;&nbsp;: Hatchback</p>
              <p class="mt-3">Fuel Type&emsp;&emsp;&nbsp;&nbsp;&nbsp;: Diesel</p>
              <p class="mt-3">Type Change (kms)&nbsp;:25,000 kms</p>
            </div>
            <div>
              <p class="mt-3">Vehicle Model&emsp;: Indica Vista</p>
              <p class="mt-3">Chassis No&emsp;&nbsp;&nbsp;&emsp;: MAT611261APK75576</p>
              <p class="mt-3">Odometer Value&emsp;: Indica Vista</p>
              <p class="mt-3">Alignment (kms)&emsp;: 10,000 kms</p>
            </div>
          </div>
          <div class="mt-5">
            <Button class="bg-blue-600 text-white  p-5 rounded" @click="addVehicle">
              Add Vehicle
            </Button>
            <Button class="bg-blue-400 text-base p-5 rounded-lg ml-3">Modify</Button>
          </div>
        </div>
        <div>
          <h4 class="text-[20px] font-bold">Customer Details</h4>
          <hr class="dark-hr">
          <div class="grid grid-cols-2 gap-4">
            <div>
              <p class="mt-3">Owner Name&emsp;&emsp;: Arumugaraja R <br>
                <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;WhatsApp
                <span class="ml-5">
                  <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;Call
                </span>
              </p>
              <p class="mt-3">Driver Name&emsp;&emsp;: Krishna <br>
                <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;WhatsApp
                <span class="ml-5">
                  <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;Call
                </span>
              </p>
              <p class="mt-3">Contact Person&emsp;&emsp;: Harish Krishna <br>
                <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;WhatsApp
                <span class="ml-5">
                  <input type="checkbox" class="bg-gray-300">&nbsp;&nbsp;Call
                </span>
              </p>
            </div>
            <div>
              <p class="mt-3">Customer Mobile No: 9876543210 <br>
                <input type="checkbox" class="bg-gray-300 w-1">&nbsp;&nbsp;Email
              </p>
              <p class="mt-3">Driver Mobile No: 9876543210 <br>
                <input type="checkbox" class="bg-gray-300 w-1">&nbsp;&nbsp;Email
              </p>
              <p class="mt-3">Contact Person No: 9876543210 <br>
                <input type="checkbox" class="bg-gray-300 w-1">&nbsp;&nbsp;Email
              </p>
            </div>
          </div>
          <div class="float-right">
            <Button class="bg-blue-600 text-white p-5 rounded" @click="addCustomer">
              Add Customer
            </Button>
            <Button class="bg-blue-400 text-base p-5 rounded-lg ml-3">Modify</Button>
          </div>
        </div>
      </div>

      <div v-if="showNewVehicle"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="addVehicle"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute top-2 right-2 text-black px-2 py-1 rounded" @click="addVehicle">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="p-8">
            <h2 class="text-lg font-semibold mb-4">Vehicle Details</h2>
            <hr>
            <p class="m-2">Vehicle Number <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.vehicleNumber" placeholder="Enter your Vehicle Number">
            </p>
            <p class="m-2">Vehicle Brand <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.vehicleBrand" placeholder="Enter Vehicle Brand">
            </p>
            <p class="m-2">Vehicle Model <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.vehicleModel" placeholder="Enter Vehicle Model">
            </p>
            <p class="m-2">Chassis No <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.chassisNo" placeholder="Enter Chassis No">
            </p>
            <p class="m-2">Fuel Type <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.fuelType" placeholder="Enter Fuel Type">
            </p>
            <p class="m-2">Odometer Value <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.odometerValue" placeholder="Enter Odometer Value">
            </p>
            <p class="m-2">Tyre Change (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.tyreChange" placeholder="Enter Tyre Change">
            </p>
            <p class="m-2">Alignment (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400"
                v-model="vehicleData.alignment" placeholder="Enter Alignment">
            </p>
            <div class="m-3">
              <button class="bg-green-500 p-2 rounded" @click="addVehicleData">Add</button>
              <button class="bg-red-500 ml-3 p-2 rounded" @click="clearVehicleData">Clear</button>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showNewCustomer"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="addCustomer"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute top-2 right-2 text-black px-2 py-1 rounded" @click="addCustomer">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="p-8">
            <h2 class="text-lg font-semibold mb-4">Customer Details</h2>
            <hr>
            <p class="m-2">Owner Name <br>
              <input type="text" v-model="customerData.ownerName" class="bg-gray-300 border-gray-400"
                placeholder="Enter your Owner Name">
            </p>
            <p class="m-2">Owner Mobile No <br>
              <input type="text" v-model="customerData.ownerMobile" class="bg-gray-300 border-gray-400"
                placeholder="Enter Owner Mobile No.">
            </p>
            <hr>
            <div v-for="(employee, index) in employees" :key="index" class="mt-2">
              <p class="m-2">Employee Name<br>
                <input type="text" v-model="employee.name" class="bg-gray-300 border-gray-400"
                  placeholder="Enter your Name">
              </p>
              <p class="m-2">Employee Type<br>
                <select v-model="employee.type" class="bg-gray-300 border-gray-400 w-75">
                  <option value="Driver">Driver</option>
                  <option value="Customer">Customer</option>
                </select>
              </p>
            </div>
            <Button class="bg-blue-600 m-2 p-2" @click="moreEmployee">Add Employee</Button>
            <div class="mt-2">
              <Button class="bg-green-600 m-2 me-1 p-2 rounded" @click="addCustomerData">Add</Button>
              <Button class="bg-red-600 m-2 ms-1 p-2 rounded" @click="removeCustomerData">Clear</Button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div v-if="currentstep === 1">
      <h1>hi this is currentstep 1</h1>
    </div>

    <div>
      <div class="flex justify-center">
        <button class="bg-blue-400 text-base p-3 rounded-lg ml-3" @click="previousPage">
          <font-awesome-icon icon="fa-solid fa-arrow-left-long" class="mr-2" style="color: #000000;" />Previous
        </button>
        <button class="bg-blue-400 text-base p-3 rounded-lg ml-3" @click="nextPage">Next
          <font-awesome-icon icon="fa-solid fa-arrow-right-long" class="ml-2" style="color: #000000;" />
        </button>
      </div>
      <div class="mt-5 pt-5">
        <ul class="flex justify-around text-center">
          <li>Details</li>
          <li>Service Details</li>
          <li>Tyre Replacement Details</li>
          <li>Billing Details</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue"
import { createListResource } from 'frappe-ui'

const Vehicles = createListResource({
  doctype: 'Vehicles',
  onSuccess(doc) {
    console.log("vehicle inserted");
  },
  auto: true,
})

const showNewVehicle = ref(false);
const showNewCustomer = ref(false)

const addVehicle = () => {
  showNewVehicle.value = !showNewVehicle.value;
};
const addCustomer = () => {
  showNewCustomer.value = !showNewCustomer.value;
}
const currentstep = ref(0);
const showMoreCustomer = ref(false)

function previousPage() {
  currentstep.value--;
}
function nextPage() {
  currentstep.value++;
}

const employees = ref([{name:'',type:''}]);
function moreEmployee() {
  employees.value.push({ name: '', type: '' });
  showMoreCustomer.value = true;
}
const vehicleData = ref({
  vehicleNumber: '',
  vehicleBrand: '',
  vehicleModel: '',
  chassisNo: '',
  fuelType: '',
  odometerValue: '',
  tyreChange: '',
  alignment: ''
});
const addVehicleData = () => {
  const fieldNames = Object.keys(vehicleData.value);
  const data = {};
  
  fieldNames.forEach(fieldName => {
    const value = vehicleData.value[fieldName].trim();
    if (value == '') {
      return
    }
    data[fieldName] = value;
    vehicleData.value[fieldName] = '';
  });
  
  Vehicles.insert.submit({
    vehicle_no: vehicleData.vehicleNumber,
    vehicle_brand: vehicleData.vehicleBrand,
    vehicle_model: vehicleData.vehicleModel,
    chassis_no: vehicleData.chassisNo,
    fuel_type: vehicleData.fuelType,
    odometer_value: vehicleData.odometerValue,
    tyre_change: vehicleData.tyreChange,
    alignment: vehicleData.alignment
    
  })
  console.log(Vehicles);
  console.log(data);
};

const clearVehicleData = () => {
  Object.keys(vehicleData.value).forEach(key => {
    vehicleData.value[key] = '';
  });
};

const customerData = ref({
  ownerName:'',
  ownerMobile:'',
  employees:employees.value,
});

const addCustomerData = () => {
  const ownerName = customerData.value.ownerName.trim();
  const ownerMobile = customerData.value.ownerMobile.trim();
  if (!ownerName && !ownerMobile) {
    alert("Please fill in at least one of the fields: Owner Name or Owner Mobile");
    return;
  }
  if (employees.value.length === 0) {
    alert("Please add at least one employee");
    return;
  }
  const data = {
    ownerName: customerData.value.ownerName,
    ownerMobile: customerData.value.ownerMobile,
    employees: []
  };

  employees.value.forEach(employee => {
    data.employees.push({
      name: employee.name,
      type: employee.type
    });
  });

  Object.keys(customerData.value).forEach(key => {
    customerData.value[key] = '';
  });
  employees.value = [];

  console.log("Owner name:", data.ownerName);
  console.log("Owner mobile:", data.ownerMobile);

  data.employees.forEach(employee => {
    console.log("Employee Name:", employee.name);
    console.log("Employee Type:", employee.type);
  });

  console.log(data);
};


const removeCustomerData =()=>{
  Object.keys(customerData.value).forEach(key => {
    customerData.value[key] = '';
  });
  employees.value = [];
}
</script>

<style scoped>
.bg-gray-300 {
  background-color: #e2e2e2;
  color: #333;
  border: 1px solid #ccc;
  padding: 5px 10px;
}

.bg-gray-3001 {
  background-color: #cdcdcd;
  color: #333;
  border: 1px solid #656464;
}

.dark-hr {
  height: 2px;
  background-color: #000000 !important;
}

p {
  font-size: 16px;
}
</style>
