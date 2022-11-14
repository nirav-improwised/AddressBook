<template>
  <section class="p-4">
    <div class="container-fluid">
      <table class="table table-bordered">
        <thead>
          <tr>
            <th v-for="(field, index) in props.dataFields" :key="index" class="text-capitalize">
              {{ field }}
            </th>
            <th>Delete</th>
            <th>Update</th>
          </tr>
        </thead>
    
        <tbody v-if="props.data.length > 0">
          <tr v-for="(obj, index) in data" :key="index">
            <td v-for="(objField, i) in dataFields" :key="i">
              {{ obj[objField] }}
            </td>
            <td>
              <button class="btn btn-outline-success" @click="emitDeleteObj(obj)">
                Delete
              </button>
            </td>
            <td>
              <button class="btn btn-outline-success" @click="emitUpdateObj(obj)">
                Update
              </button>
            </td>
          </tr>
        </tbody>
    
        <tbody v-else>
          <tr>
            <td colspan="6">No data found</td>
          </tr>
        </tbody>
      </table>
  </div>
  </section>
  </template>
  
  <script setup>
  
  const props = defineProps({
    data: Array,
    dataFields: Array,
  });
  
  const emit = defineEmits(["deleteResponse", "updateResponse"]);
  
  function emitDeleteObj(obj) {
    emit("deleteResponse", obj);
  }
  function emitUpdateObj(obj) {
    emit("updateResponse", obj);
  }
  </script>
  