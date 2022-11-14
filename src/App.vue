<template>
  <div>
    <h1 class="text-center my-4">Adress Book</h1>
    <add
      :defaultValues="defaultObj"
      @response="(newObj) => addAddress(newObj)"
    />
  </div>

  <div>
    <list
      :data="addresses"
      :dataFields="fields"
      @updateResponse="(obj) => updateAddress(obj)"
      @deleteResponse="(obj) => removeAddress(obj)"
    />
  </div>
</template>

  <script setup>
  import { ref } from "vue";
  import list from "./components/list.vue";
  import add from "./components/add.vue";
  
  let addresses = ref([
    {
      name: "Nirav",
      address: "Bansari Society",
      contactNo: "6353492281",
      email: "niravgaglani6268@gmail.com",
      country: "India",
      state: "Gujarat",
    },
    {
      name: "Suryakant",
      address: "Kuvadwa Road",
      contactNo: "9377151135",
      email: "suri@gmail.com",
      country: "India",
      state: "Gujarat",
    },
    {
      name: "Vishwajeet",
      address: "Aalap Heritage",
      contactNo: "9913429071",
      email: "vishu@gmail.com",
      country: "India",
      state: "Gujarat",
    },
  ]);
  
  let fields = ["name", "address", "contactNo", "email", "country", "state"];
  
  let defaultObj = ref({
    name: "",
    address: "",
    contactNo: "",
    email: "",
    country: "",
    state: "",
  });
  
  function addAddress(newObj) {
    let index = addresses.value.indexOf(newObj);
    if (index !== -1) {
      confirm("Are you sure you want to update details?");
      addresses[index].name = newObj.name;
      addresses[index].address = newObj.address;
      addresses[index].contactNo = newObj.contactNo;
      addresses[index].email = newObj.email;
      addresses[index].country = newObj.country;
      addresses[index].state = newObj.state;
    } else {
      addresses.value.push(newObj);
      alert("Details added successfully");
    }
  }
  
  function removeAddress(obj) {
    addresses.value = addresses.value.filter((item) => item !== obj);
    return addresses.value;
  }
  
  function updateAddress(obj) {
    defaultObj.value = obj;
  }
  </script>
