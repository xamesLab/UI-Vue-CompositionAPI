<template>
  <input 
		:class="['btn', `btn_${size}`]" 
		:type="buttonType" 
		:value="label" 
		:disabled="disabled" 
		@click="clickHandler" 
	/>
</template>

<script setup lang="ts">
import "./style/index.css";

const props = defineProps({
  label: {
    type: String,
    default: "Button",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  size: {
    type: String,
    default: "md",
  },
  buttonType: {
    type: String,
    default: "button",
  },
});

const emit = defineEmits(["click"]);
const clickHandler = () => {
  if (props.buttonType === "button") emit("click");
};
</script>

<style scoped>
.btn_md {
  padding: 0.5rem 1.5rem;
}

.btn_sm {
  font-size: 0.7rem;
  padding: 0.2rem 0.5rem;
}

.btn_lg {
  text-transform: uppercase;
  padding: 0.8rem 2.5rem;
}
</style>
