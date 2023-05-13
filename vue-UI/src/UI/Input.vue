<template>
  <div class="input-wrap">
		<label v-if="label" :for="name">{{ label }}:</label>
    <input 
			class="input-content" 
			:type="isSecret ? 'password' : 'text'" 
			:name="name"
			:placeholder="placeholder"
			:value="value"
			:style="{width: `${width}%`}"
			:disabled="disabled" 
			@input="updateHandler"
		/>
  </div>
</template>

<script setup lang="ts">
import "./style/index.css";

defineProps({
	isSecret: {
		type: Boolean,
    default: false,
	},
	value: {
		type: String,
    default: "",
	},
  label: {
    type: String,
		default: "",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
  width: {
    type: Number,
    default: 100,
  },
  name: {
    type: String,
    default: "input",
  },
	placeholder: {
		type: String,
    default: "",
	}
});

const emit = defineEmits(["update:value"]);
const updateHandler = (e: Event) => {
	emit('update:value', (e.target as HTMLInputElement).value)
}
</script>

<style scoped>
.input-content[disabled] {
	border-color: #afafaf;
}
</style>
