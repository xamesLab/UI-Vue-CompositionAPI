<template>
  <main>
    <h2>Test UI</h2>
    <div>
      <Input placeholder="place" label="label" name="input11" />
      <Input :width="50" label="label2" name="input2" />
      <Input placeholder="place3" :width="50" name="input3" disabled />
    </div>
    <div>
      <Button label="My button sm" size="sm" />
    </div>
    <div>
      <Button label="My button submit" buttonType="submit" />
    </div>
    <div>
      <Button label="disabled" disabled />
    </div>
    <div>
      <Button label="My button LG" size="lg" />
    </div>
    <hr />
    <br />
    <form @submit.prevent="eventSubTest">
      <Input placeholder="name" name="input1" v-model:value="formData.name" />
      <Input placeholder="pass" name="pass" isSecret v-model:value="formData.password" />
      <Button label="My button submit" buttonType="submit" />
    </form>
  </main>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Button from "./UI/Button.vue";
import Input from "./UI/Input.vue";

const formData = ref({ name: "", password: "" });

const eventSubTest = () => {
  const { name, password } = formData.value;
  console.log("submit", name, password);
  formData.value = { name: "", password: "" };
};
</script>

<style scoped>
main {
  width: 800px;
  height: 100vh;
  margin: 0 auto;
  padding: 100px 50px;
  background-color: beige;
}
</style>
