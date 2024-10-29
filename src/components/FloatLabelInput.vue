<template>
  <div class="float-label-container">
    <input
      :type="type"
      v-model="inputValue"
      @focus="isFocused = true"
      @blur="handleBlur"
      required
    />
    <label :class="{ active: isFocused || inputValue }">
      {{ label }}
    </label>
  </div>
</template>

<script setup>
import { ref } from "vue";

// Props
defineProps({
  label: String,
  type: {
    type: String,
    default: "text",
  },
});

// Variables reactivas
const inputValue = ref("");
const isFocused = ref(false);

// Manejadores de eventos
const handleBlur = () => {
  if (!inputValue.value) isFocused.value = false;
};
</script>

<style scoped>
.float-label-container {
  position: relative;
  margin: 16px 0;
  width: 100%;
}

input {
  width: 100%;
  padding: 8px 12px;
  font-size: 16px;
  border: 1px solid var(--bg-aonibi);
  border-radius: var(--radius-24);
  background-color: var(--bg-white-alpha-10);
  color: var(--text-white);
  outline: none;
  transition: border var(--transition-1);
}

input:focus {
  border-color: var(--border-kin);
}

label {
  position: absolute;
  top: 10px;
  left: 14px;
  color: var(--text-white-alpha-60);
  font-size: 16px;
  transition: 0.3s ease-in-out;
  pointer-events: none;
}

label.active {
  top: -20px;
  left: 20px;
  font-size: 12px;
  color: var(--bg-kin);
}
</style>
