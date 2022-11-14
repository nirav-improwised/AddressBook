<template>
  <section class="p-4">
    <div class="container-fluid">
      <form action="">
        <div class="mb-3">
          <label for="name" class="form-label">Name :</label>
          <input
            type="text"
            class="form-control"
            v-model="defaultValues.name"
            placeholder="name"
            id="name"
          />
        </div>

        <div class="mb-3">
          <label for="address" class="form-label">Address :</label>
          <input
          class="form-control"
            type="text"
            v-model="defaultValues.address"
            placeholder="address"
            id="address"
          />
        </div>

        <div class="mb-3">
          <label for="contactNo" class="form-label">Contact No. :</label>
          <input
            type="text"
            class="form-control"
            v-model="defaultValues.contactNo"
            placeholder="contactNo"
            id="contactNo"
          />
        </div>

        <div class="mb-3">
          <label for="email" class="form-label">Email ID :</label>
          <input
            type="email"
            class="form-control"
            v-model="defaultValues.email"
            placeholder="email"
            id="email"
          />
        </div>

        <div class="mb-3">
          <label for="country" class="form-label">Country :</label>
          <input
            type="text" 
            class="form-control"
            v-model="defaultValues.country"
            placeholder="country"
            id="country"
            />
          </div>

        <div class="mb-3">
          <label for="state" class="form-label">State :</label>
          <input
          type="text" 
          class="form-control"
          v-model="defaultValues.state"
          placeholder="state"
          id="state"
          />
        </div>
        <button type="button" @click="sendEmits" class="btn btn-primary mt-4">
          Add address
        </button>
      </form>
    </div>
</section>
</template>

<script setup>
const props = defineProps({
  defaultValues: Object,
});

const emit = defineEmits(["response"]);

function sendEmits() {
  emit("response", props.defaultValues);
}
</script>
