<script setup>
import { reactive, ref } from "@vue/reactivity";


let newObj = reactive({
    name: '',
    address: '',
    contactNo: '',
    email: '',
    country: '',
    state: ''

});

const props = defineProps({
    data: Array,
    dataFields: Array,
});

const emit = defineEmits(['response']);
function sendEmits(){
    emit('response', newObj);
}

</script>

<template>
    <form action="">
        <div>
        <label for="">Name :</label>
        <input type="text" v-model="newObj.name" placeholder="name" id="name">
        </div>
        
        <div>
        <label for="">Address :</label>
        <input type="text" v-model="newObj.address" placeholder="address" id="address">
        </div>
        
        <div>
        <label for="">Contact No. :</label>
        <input type="text" v-model="newObj.contactNo" placeholder="contactNo" id="contactNo">
        </div>
        
        <div>
        <label for="">Email ID :</label>
        <input type="email" v-model="newObj.email" placeholder="email" id="email">
        </div>
        
        <div>
        <label for="">Country :</label>
        <input type="text" v-model="newObj.country" placeholder="country" id="country">
        </div>
        
        <div>
        <label for="">State :</label>
        <input type="text" v-model="newObj.state" placeholder="state" id="state">
        </div>
        <button type="submit" @click="sendEmits" class="btn btn-primary">Submit</button>
    </form>
</template>