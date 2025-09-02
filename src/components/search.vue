<template>
    <el-input
    :model-value="modelValue"
    style="width: 240px"
    placeholder="Please input"
    clearable
    class="input-box"
    @input="handleInput"
  />
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'

const props = defineProps({
  modelValue: String
})

const emit = defineEmits(['update:modelValue', 'change'])
const handleInput = (val) => {
  emit('update:modelValue', val)
  emit('change', val)
}


</script>

<style scoped>
.input-box :deep(.el-input__inner) {
  height: 5vh;
  font-size: 1.2rem;
  font-family: 'openhuninn','Baloo 2';
}
</style>