<template>
  <div>
    <div class="m-5" v-if="currentstep === 0">
      <h4>Greeting User 1</h4>
      <div class="text-center m-5">
        <input type="text" class="input-color">
        <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3">Search</Button>
      </div>
      <div class="row">
        <div class="col-6">
          <h4>Vehicle Details</h4>
          <hr class="dark-hr">
          <div class="row">
            <div class="col-6">
              <p>Vehicle Brand&emsp;: Tata</p>
              <p>Vehicle Type&emsp;&nbsp;&nbsp;: Hatchback</p>
              <p>Fuel Type&emsp;&emsp;&nbsp;&nbsp;&nbsp;: Diesel</p>
              <p>Type Change (kms)&nbsp;:25,000 kms</p>
            </div>
            <div class="col-6">
              <p>Vehicle Model&emsp;: Indica Vista</p>
              <p>Chassis No&emsp;&nbsp;&nbsp;&emsp;: MAT611261APK75576</p>
              <p>Odometer Value&emsp;: Indica Vista</p>
              <p>Alignment (kms)&emsp;: 10,000 kms</p>
            </div>
          </div>
          <!-- <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3" >Add</Button> -->
          <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3" type="button" data-bs-toggle="offcanvas"
            @click="addVehicle" data-bs-target="#offcanvasWithBothOptions" aria-controls="offcanvasWithBothOptions">Add
            Vehicle</Button>
          <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3">Modify</Button>
        </div>
        <div class="col-6">
          <h4>Customer Details</h4>
          <hr class="dark-hr">
          <div class="row">
            <div class="col-6">
              <p>Owner Name&emsp;&emsp;: Arumugaraja R <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;WhatsApp
                <span class="ms-5">
                  <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Call
                </span>
              </p>
              <p>Driver Name&emsp;&emsp;: Krishna <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;WhatsApp
                <span class="ms-5">
                  <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Call
                </span>
              </p>
              <p>Contact Person&emsp;&emsp;: Harish Krishna <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;WhatsApp
                <span class="ms-5">
                  <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Call
                </span>
              </p>
            </div>
            <div class="col-6">
              <p>Customer Mobile No :9876543210 <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Email
              </p>
              <p>Driver Mobile No :9876543210 <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Email
              </p>
              <p>Contact Person No :9876543210 <br>
                <input type="checkbox" class="input-color1 rounded-1">&nbsp;&nbsp;Email
              </p>
            </div>
          </div>
          <div class="float-right">
            <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3" type="button" data-bs-toggle="offcanvas"
              @click="addCustomer" data-bs-target="#offcanvasWithBothOptionss"
              aria-controls="offcanvasWithBothOptions">Add Customer</Button>
            <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3">Modify</Button>
          </div>
        </div>
      </div>

      <div v-if="showNewVehicle">
        <div class="float-right">
          <div class="offcanvas offcanvas-end" data-bs-scroll="true" tabindex="-1" id="offcanvasWithBothOptions"
            aria-labelledby="offcanvasWithBothOptionsLabel">
            <div class="offcanvas-header border-bottom">
              <h5 class="offcanvas-title" id="offcanvasWithBothOptionsLabel">Vehicle Details</h5>
              <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
            <div class="offcanvas-body">
              <p>Vehicle Number <br>
                <input type="text" class="input-color" placeholder="Enter your Vehicle Number">
              </p>
              <p>Vehicle Brand <br>
                <input type="text" class="input-color" placeholder="Enter Vehicle Brand">
              </p>
              <p>Vehicle Model <br>
                <input type="text" class="input-color" placeholder="Enter Vehicle Model">
              </p>
              <p>Chassis No <br>
                <input type="text" class="input-color" placeholder="Enter Chassis No">
              </p>
              <p>Fuel Type <br>
                <input type="text" class="input-color" placeholder="Enter Fuel Type">
              </p>
              <p>Odometer Value <br>
                <input type="text" class="input-color" placeholder="Enter Odometer Value">
              </p>
              <p>Tyre Change (kms) <br>
                <input type="text" class="input-color" placeholder="Enter Tyre Change">
              </p>
              <p>Alignment (kms) <br>
                <input type="text" class="input-color" placeholder="Enter Alignment">
              </p>
              <div>
                <Button class="bg-green-500 me-1">Add</Button>
                <Button class="bg-red-500 ms-1">Clear</Button>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div v-if="showNewCustomer">
        <div class="float-right">
          <div class="offcanvas offcanvas-end" data-bs-scroll="true" tabindex="-1" id="offcanvasWithBothOptionss"
            aria-labelledby="offcanvasWithBothOptionsLabel">
            <div class="offcanvas-header border-bottom">
              <h5 class="offcanvas-title" id="offcanvasWithBothOptionsLabel">Customer Details</h5>
              <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
            <div class="offcanvas-body">
              <p>Owner Name <br>
                <input type="text" class="input-color" placeholder="Enter your Owner Name">
              </p>
              <p>Owner Mobile No <br>
                <input type="text" class="input-color" placeholder="Enter Owner Mobile No.">
              </p>
              <hr>
              <p>Employee Name<br>
                <input type="text" class="input-color" placeholder="Enter your Name">
              </p>
              <p>Employee Type<br>
                <select class="input-color w-75">
                  <option value="Driver">Driver</option>
                  <option value="Driver">Customer</option>
                </select>
              </p>
              <Button class="bg-blue-500" @click="moreEmployee">Add Employee</Button>
              <div v-if="showMoreCustomer">
                <p>Employee Name<br>
                  <input type="text" class="input-color" placeholder="Enter your Name">
                </p>
                <p>Employee Type<br>
                  <select class="input-color w-75">
                    <option value="Driver">Driver</option>
                    <option value="Driver">Customer</option>
                  </select>
                </p>
              </div>
              <div class="mt-2">
                <Button class="bg-green-500 me-1">Add</Button>
                <Button class="bg-red-500 ms-1">Clear</Button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div v-if="currentstep === 1">
      <h1>hi this is currentstep 1</h1>
    </div>



    <div>
      <div class="text-center">
        <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3" @click="previousPage"><font-awesome-icon
            icon="fa-solid fa-arrow-left-long" style="color: #000000;" class="me-2" />Previous</Button>
        <Button class="bg-blue-500 button-text p-3 rounded-lg ms-3" @click="nextPage">Next<font-awesome-icon
            icon="fa-solid fa-arrow-right-long" style="color: #000000;" class="ms-2" /></Button>
      </div>
      <div class="mt-5 pt-5">
        <ul class="d-flex justify-content-around text-center">
          <li>Details</li>
          <li type="disc">Service Details</li>
          <li type="disc">Tyre Replacement Details</li>
          <li type="disc">Billing Details</li>
        </ul>
      </div>
    </div>

  </div>
</template>
<script setup>
import { ref } from "vue"

const currentstep = ref(0);
const showNewVehicle = ref(false)
const showNewCustomer = ref(false)
const showMoreCustomer = ref(false)

function previousPage() {
  currentstep.value--;
}
function nextPage() {
  currentstep.value++;
}
function addVehicle() {
  showNewVehicle.value = true;
}
function addCustomer() {
  showNewCustomer.value = true;
}
function moreEmployee() {
  showMoreCustomer.value = true;
}
</script>
<style scoped>
.input-color {
  background-color: #e2e2e2;
  color: #333;
  border: 1px solid #ccc;
  padding: 5px 10px;
}

.input-color1 {
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

.button-text {
  font-size: 20px;
}
</style>
