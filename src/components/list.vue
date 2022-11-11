<script setup>
import { reactive } from "@vue/reactivity";

const props = defineProps({
    data: Array,
    dataFields: Array,
})

const emit = defineEmits(['deleteResponse', 'updateResponse']);
function emitDeleteObj(obj){
    emit('deleteResponse', obj);
}
function emitUpdateObj(obj){
    emit('response', obj);
}

</script>

<template>

    <table>
        <thead>
        <tr>
            <th v-for="(field, index) in props.dataFields" :key="index">
                {{ field }}
            </th>
        </tr>
        </thead>

        <tbody v-if="props.data.length>0">
        <tr v-for="(obj, index) in data" :key="index">
            <td v-for="(objField, i) in dataFields" :key="i">
                {{obj[objField]}}
            </td>
            <td>
                <button class="btn btn-outline-success" @click="emitDeleteObj(obj)">Delete</button>
            </td>
            <td>
                <button class="btn btn-outline-success" @click="emitUpdateObj(obj)">Update</button>
            </td>
        </tr>
        </tbody>

        <tbody v-else>
            <tr>
                <td colspan="6">
                    No data found
                </td>
            </tr>
        </tbody>
    </table>

</template>

<style>
table {
  border: 2px solid #42b983;
  border-radius: 3px;
  background-color: #fff;
}

th {
  background-color: #42b983;
  color: rgba(255, 255, 255, 0.66);
  cursor: pointer;
  user-select: none;
}

td {
  background-color: #f9f9f9;
}

th,
td {
  min-width: 120px;
  padding: 10px 20px;
}

th.active {
  color: #fff;
}

th.active .arrow {
  opacity: 1;
}
</style>