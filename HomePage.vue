<template>
  <div class="m-10">
    <h4 class="text-2xl font-bold">Greetings User 1</h4>
    <div v-if="currentstep === 0">
      <div class="flex justify-center m-5">
        <input type="text" class="bg-gray-300 p-2 border border-gray-400" v-model="searchQuery"
          @keyup.enter="performSearch">
        <button class="bg-blue-500 text-white font-bold text-base p-3 rounded-lg ml-3"
          @click="performSearch">Search</button>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <Card>
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
              <button class="bg-blue-500 text-white font-bold  p-5 rounded-lg ml-3" @click="addVehicle">
                Add Vehicle
              </button>
              <button class="bg-blue-500 text-white font-bold  p-5 rounded-lg ml-3"
                @click="modifyVehicle">Modify</button>
            </div>
          </div>
        </Card>
        <Card>
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
              <button class="bg-blue-500 text-white font-bold  p-5 rounded-lg ml-3" @click="addCustomer">
                Add Customer
              </button>
              <button class="bg-blue-500 text-white font-bold  p-5 rounded-lg ml-3"
                @click="modifyCustomer">Modify</button>
            </div>
          </div>
        </Card>
      </div>

      <div v-if="showNewVehicle"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="addVehicle"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute to text-white font-bold p-2 right-2  px-2 py-1 rounded" @click="addVehicle">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="p-8">
            <h2 class="text-lg font-semibold mb-4">Vehicle Details</h2>
            <hr>
            <p class="m-2">Vehicle Number <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.vehicleNumber"
                placeholder="Enter your Vehicle Number">
            </p>
            <p class="m-2">Vehicle Brand <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.vehicleBrand"
                placeholder="Enter Vehicle Brand">
            </p>
            <p class="m-2">Vehicle Model <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.vehicleModel"
                placeholder="Enter Vehicle Model">
            </p>
            <p class="m-2">Chassis No <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.chassisNo"
                placeholder="Enter Chassis No">
            </p>
            <p class="m-2">Fuel Type <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.fuelType"
                placeholder="Enter Fuel Type">
            </p>
            <p class="m-2">Odometer Value <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.odometerValue"
                placeholder="Enter Odometer Value">
            </p>
            <p class="m-2">Tyre Change (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.tyreChange"
                placeholder="Enter Tyre Change">
            </p>
            <p class="m-2">Alignment (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleData.alignment"
                placeholder="Enter Alignment">
            </p>
            <div class="m-3">
              <button class="bg-green-500 text-white font-bold 0 p-2 rounded" @click="addVehicleData">Add</button>
              <button class="bg-red-500  text-white font-bold ml-3 p-2 rounded" @click="clearVehicleData">Clear</button>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showModifyVehicle"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="modifyVehicle"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute to text-white font-bold p-2 right-2 px-2 py-1 rounded" @click="modifyVehicle">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="p-8">
            <h2 class="text-lg font-semibold mb-4">Vehicle Details</h2>
            <hr>
            <p class="m-2">Vehicle Number <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.vehicleNumber"
                placeholder="Enter your Vehicle Number">
            </p>
            <p class="m-2">Vehicle Brand <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.vehicleBrand"
                placeholder="Enter Vehicle Brand">
            </p>
            <p class="m-2">Vehicle Model <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.vehicleModel"
                placeholder="Enter Vehicle Model">
            </p>
            <p class="m-2">Chassis No <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.chassisNo"
                placeholder="Enter Chassis No">
            </p>
            <p class="m-2">Fuel Type <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.fuelType"
                placeholder="Enter Fuel Type">
            </p>
            <p class="m-2">Odometer Value <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.odometerValue"
                placeholder="Enter Odometer Value">
            </p>
            <p class="m-2">Tyre Change (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.tyreChange"
                placeholder="Enter Tyre Change">
            </p>
            <p class="m-2">Alignment (kms) <br>
              <input type="text" class="bg-gray-300 border-gray-400" v-model="vehicleDetails.alignment"
                placeholder="Enter Alignment">
            </p>
            <div class="m-3">
              <button class="bg-green-500 text-white font-bold 0 p-2 rounded" @click="addModifiedData">Add</button>
              <button class="bg-red-500  text-white font-bold ml-3 p-2 rounded"
                @click="clearModifiedVehicleData">Clear</button>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showNewCustomer"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="addCustomer"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute to text-white font-bold p-2 right-2 px-2 py-1 rounded" @click="addCustomer">
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
                {{ console.log("e") }}
                <input type="text" v-model="employee.name" @input="logEmployeeName(employee.name)"
                  class="bg-gray-300 border-gray-400" placeholder="Enter your Name">
              </p>
              <p class="m-2">Employee Type<br>
                <select v-model="employee.type" class="bg-gray-300 border-gray-400 w-75">
                  <option value="Driver">Driver</option>
                  <option value="Customer">Customer</option>
                </select>
              </p>
            </div>
            <div>
              <button class="bg-blue-500 text-white font-bold  text-base p-3 rounded-lg ml-3 float-right"
                @click="moreEmployee">Add
                Employee</button><br>
            </div>
            <div class="mt-2">
              <button class="bg-green-500 text-white font-bold 0 text-base p-3 rounded-lg ml-3"
                @click="addCustomerData">Save</button>
              <button class="bg-red-500  text-white font-bold text-base p-3 rounded-lg ml-3"
                @click="removeCustomerData">Clear</button>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showModifyCustomer"
        class="fixed inset-0 overflow-hidden bg-black bg-opacity-50 flex justify-end items-center">
        <div class="fixed inset-0" @click="modifyCustomer"></div>
        <div class="max-w-sm w-full bg-white shadow-xl h-full overflow-y-auto relative">
          <button class="absolute to text-white font-bold p-2 right-2 px-2 py-1 rounded" @click="modifyCustomer">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <div class="p-8">
            <h2 class="text-lg font-semibold mb-4">Customer Details</h2>
            <hr>
            <p class="m-2">Owner Name <br>
              <input type="text" v-model="employeesDetails.ownerName" class="bg-gray-300 border-gray-400"
                placeholder="Enter your Owner Name">
            </p>
            <p class="m-2">Owner Mobile No <br>
              <input type="text" v-model="employeesDetails.ownerMobile" class="bg-gray-300 border-gray-400"
                placeholder="Enter Owner Mobile No.">
            </p>
            <hr>
            <div v-for="(employee, index) in employeesDetails.employeessss" :key="index" class="mt-2">
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
            <div>
              <button class="bg-blue-500 text-white font-bold  text-base p-3 rounded-lg ml-3 float-right"
                @click="moreEmployee">Add
                Employee</button><br>
            </div>
            <div class="mt-2">
              <button class="bg-green-500 text-white font-bold 0 text-base p-3 rounded-lg ml-3"
                @click="addModifiedCustomerData">Save</button>
              <button class="bg-red-500  text-white font-bold text-base p-3 rounded-lg ml-3"
                @click="removeModifiedCustomerData">Clear</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- <div v-if="currentstep === 1">
      <div class="pb-5">
        <h4 class="text-[20px] font-bold mt-2">Replacement Tyre Details</h4>
        <hr class="dark-hr">
        <div v-for="(position,index) in tyrePositions" :key="index"
          class="grid grid-cols-5 gap-0 mt-5 pb-5 ml-2 border-b border-gray-900">
          <div>
            <p class="font-bold mt-8">{{ position }} Tyre</p>
            <div class="mt-8">
              <label>Load Index</label><br>
              <input type="text" v-model="replacementDetails[index].loadIndex">
            </div>
          </div>
          <div>
            <div>
              <label>Brand</label><br><input type="text">
            </div>
            <div class="mt-5">
              <label>Speed Rating</label><br><input type="text">
            </div>
          </div>
          <div>
            <div>
              <label>Pattern</label><br><input type="text">
            </div>
            <div class="mt-5">
              <label>Size</label><br><input type="text">
            </div>
          </div>
          <div>
            <div>
              <label>TT/TL</label><br><input type="text">
            </div>
            <div class="mt-5">
              <label>Item</label><br><input type="text">
            </div>
          </div>
          <div class="mt-5">
            <button class="bg-blue-500 text-white font-bold  font-bold text-base p-3 rounded-lg ml-3 text-white" @click="copyData($index)">Copy</button>
            <br>
            <button class="bg-blue-500 text-white font-bold  font-bold text-base p-3 rounded-lg ml-3 mt-5 text-white">Paste</button>
          </div>
        </div>
      </div>
    </div> -->

    <div>
      <div class="flex justify-center pb-5 mt-5">
        <button class="bg-blue-500 text-white font-bold  text-base p-3 rounded-lg ml-3" @click="previousPage">
          <font-awesome-icon icon="fa-solid fa-arrow-left-long" class="mr-2" style="color: #000000;" />Previous
        </button>
        <button class="bg-blue-500 text-white font-bold  text-base p-3 rounded-lg ml-3"
          @click="nextPageAndHighlight">Next
          <font-awesome-icon icon="fa-solid fa-arrow-right-long" class="ml-2" style="color: #000000;" />
        </button>
      </div>
      <div class="bottom-div">
        <div class="m-3 p-2 mb-0">
          <ul class="flex justify-around text-center">
            <li type="disc" :class="{ 'active': currentPage === 'details' }">Details</li>
            <li type="disc" :class="{ 'active': currentPage === 'tyre-replacement-details' }">Tyre Replacement Details
            </li>
            <li type="disc" :class="{ 'active': currentPage === 'service-details' }">Service Details</li>
            <li type="disc" :class="{ 'active': currentPage === 'billing-details' }">Billing Details</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue"
import { createListResource } from 'frappe-ui'

const searchQuery = ref('');
const logEmployeeName = (name) => {
  console.log('Employee Name:', name);
};

const performSearch = () => {
  const query = searchQuery.value.trim().toLowerCase();
  console.log('Performing search with query:', query);
  const vehicleResults = vehicleData.items.value.filter(item => {
    return Object.values(item).some(val => val.toString().toLowerCase().includes(query));
  });
  const customerResults = Object.values(customerData.value).some(val => val.toString().toLowerCase().includes(query));

  console.log('Vehicle search results:', vehicleResults);
  console.log('Customer search results:', customerResults);
};

let vehicleDetailsData = createListResource({
  doctype: 'Vehicle Details',
  onSuccess(doc) {
    console.log('neew doctype data', doc);
  },
  auto: true
})
console.log('vehicledetailsdata', vehicleDetailsData);

const currentPage = ref('details');
const currentstep = ref(0);
const maxStep = 3;

function previousPage() {
  if (currentstep.value > 0) {
    currentstep.value--;
    currentPage.value = getPageName(currentstep.value);
  }
}

function nextPageAndHighlight() {
  if (currentstep.value < maxStep) {
    currentstep.value++;
    currentPage.value = getPageName(currentstep.value);
  }
}

function getPageName(step) {
  switch (step) {
    case 0:
      return 'details';
    case 1:
      return 'tyre-replacement-details';
    case 2:
      return 'service-details';
    case 3:
      return 'billing-details';
    default:
      return 'details';
  }
}
// const tyrePositions = ['Front Left', 'Front Right', 'Rear Left', 'Rear Right', 'Spare'];
// const replacementDetails = ref({
//   loadIndex:'',
//   brand:'',
//   pattern:'',
//   tubelessOrTube:'',
//   speedRating:'',
//   size:'',
//   item:'',  
// })
// function copyData(i){
// }
// const Vehicles = createListResource({
//   doctype: 'Vehicles',
//   // field:[,'vehicle_no','vehicle_brand','vehicle_model','odometer_value','fuel_type','tyre_change','alignment'],
//   onSuccess(doc) {
//     console.log("vehicle inserted");
//   },
//   auto: true,
// })


const vehicleDetails = ref({
  vehicleNumber: 'TN 47 SL 7784',
  vehicleBrand: 'Tata',
  vehicleModel: 'rtyui',
  chassisNo: 3456789,
  fuelType: "Diesel",
  odometerValue: 'qwertyui',
  tyreChange: 'wertyui',
  alignment: 'asdfghjk'
})

const employeesDetails = ref({
  ownerName: 'Vijayaragavan',
  ownerMobile: 6383436185,
  employeessss: {
    name: 'siva',
    type: 'Driver'
  }
})

const showNewVehicle = ref(false);
const showNewCustomer = ref(false)
const showModifyVehicle = ref(false);
const showModifyCustomer = ref(false);

const addVehicle = () => {
  showNewVehicle.value = !showNewVehicle.value;
};
const addCustomer = () => {
  showNewCustomer.value = !showNewCustomer.value;
}
const modifyVehicle = () => {
  showModifyVehicle.value = !showModifyVehicle.value;
}
const modifyCustomer = () => {
  showModifyCustomer.value = !showModifyCustomer.value;
}
const employees = ref([{ name: '', type: '' }]);
function moreEmployee() {
  employees.value.push({ name: '', type: '' });
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

  // Vehicles.insert.submit({
  //   vehicle_no: vehicleData.vehicleNumber,
  //   vehicle_brand: vehicleData.vehicleBrand,
  //   vehicle_model: vehicleData.vehicleModel,
  //   chassis_no: vehicleData.chassisNo,
  //   fuel_type: vehicleData.fuelType,
  //   odometer_value: vehicleData.odometerValue,
  //   tyre_change: vehicleData.tyreChange,
  //   alignment: vehicleData.alignment

  // })
  // console.log(Vehicles);
  console.log(data);
};

const addModifiedData = () => {
  vehicleDetailsData.insert.submit({
    vehicle_number: vehicleDetails.vehicleNumber
  })
  console.log('checking', vehicleDetailsData);
  console.log('saved', vehicleDetails.value);
}

const addModifiedCustomerData = () =>{
  console.log('modified data',employeesDetails);
}

const clearModifiedVehicleData = () => {
  Object.keys(vehicleDetails.value).forEach(key => {
    vehicleDetails.value[key] = '';
  });
}

const clearVehicleData = () => {
  Object.keys(vehicleData.value).forEach(key => {
    vehicleData.value[key] = '';
  });
};

const customerData = ref({
  ownerName: '',
  ownerMobile: '',
  employees: employees.value,
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
  const isAnyEmployeeDataMissing = employees.value.some(employee => {
    return !employee.name.trim() || !employee.type.trim();
  });
  if (isAnyEmployeeDataMissing) {
    alert("Please fill in all fields for all employees");
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
  employees.value = [{ name: '', type: '' }];

  console.log("Owner name:", data.ownerName);
  console.log("Owner mobile:", data.ownerMobile);

  data.employees.forEach(employee => {
    console.log("Employee Name:", employee.name);
    console.log("Employee Type:", employee.type);
  });

  console.log(data);
};


const removeCustomerData = () => {
  Object.keys(customerData.value).forEach(key => {
    customerData.value[key] = '';
  });
  employees.value = [{ name: '', type: '' }];
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
  font-size: 20px;
}

.bottom-div {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background-color: #f0f0f0;
}

.active {
  font-weight: bold;
}
</style>
