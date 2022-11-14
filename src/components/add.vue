<template>
  <form action="">
    <div>
      <label for="name">Name :</label>
      <input
        type="text"
        v-model="defaultValues.name"
        placeholder="name"
        id="name"
      />
    </div>

    <div>
      <label for="address">Address :</label>
      <input
        type="text"
        v-model="defaultValues.address"
        placeholder="address"
        id="address"
      />
    </div>

    <div>
      <label for="contactNo">Contact No. :</label>
      <input
        type="text"
        v-model="defaultValues.contactNo"
        placeholder="contactNo"
        id="contactNo"
      />
    </div>

    <div>
      <label for="email">Email ID :</label>
      <input
        type="email"
        v-model="defaultValues.email"
        placeholder="email"
        id="email"
      />
    </div>

    <div>
      <label for="country">Country :</label>
      <input
        type="text"
        v-model="defaultValues.country"
        placeholder="country"
        id="country"
        />
      </div>

    <div>
      <label for="state">State :</label>
      <input
      type="text"
      v-model="defaultValues.state"
      placeholder="state"
      id="state"
      />
    </div>
    <button type="button" @click="sendEmits" class="btn btn-warning">
      Add address
    </button>
  </form>
</template>

<script setup>
const props = defineProps({
  defaultValues: Object,
});

const emit = defineEmits(["response"]);

function sendEmits() {
  emit("response", props.defaultValues);
}

function consoleNewObj() {
  console.log("007", props.defaultValues);
}
</script>
