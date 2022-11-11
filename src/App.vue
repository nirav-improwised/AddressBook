<script setup>

import { ref, reactive } from 'vue';
import list from './components/list.vue';
import add from './components/add.vue';

let addresses = ref([{name: "Nirav", address: "Bansari Society", contactNo: "6353492281", email: "niravgaglani6268@gmail.com", country: "India", state: "Gujarat"}, {name: "Suryakant", address: "Kuvadwa Road", contactNo: "9377151135", email: "suri@gmail.com", country: "India", state: "Gujarat"}, {name: "Vishwajeet", address: "Aalap Heritage", contactNo: "9913429071", email: "vishu@gmail.com", country: "India", state: "Gujarat"}]);

// let addresses = ref([{name: "Nirav", address: "Bansari Society", contactNo: "6353492281", email: "niravgaglani6268@gmail.com", country: "India", state: "Gujarat"}, {name: "Suryakant", address: "Kuvadwa Road", contactNo: "9377151135", email: "suri@gmail.com", country: "India", state: "Gujarat"}, {name: "Vishwajeet", address: "Aalap Heritage", contactNo: "9913429071", email: "vishu@gmail.com", country: "India", state: "Gujarat"}]);

let fields = ['name', 'address', 'contactNo', 'email', 'country', 'state'];

let addObj = reactive({
    name: '',
    address: '',
    contactNo: '',
    email: '',
    country: '',
    state: ''
});

function addAddress(newObj){
  console.log("addAdd called");
  addresses.value.push(newObj);
}

function removeAddress(obj){
  addresses.value = addresses.value.filter(item=>item!==obj);
  return addresses.value
}

function updateAddress(obj){
  addresses.value.forEach(function(item, index){
    if (item===obj){
      console.log(item.address);
    }
  })
}

</script>

<template>
  <div>
    <add :data="addresses" :dataFields="fields" @response="newObj=>addAddress(newObj)" />
  </div>

  <div>
    <list :data="addresses" :dataFields="fields" @deleteResponse="obj=>removeAddress(obj)" @updateResponse="obj=>updateAddress(obj)"/>
  </div>
</template>
