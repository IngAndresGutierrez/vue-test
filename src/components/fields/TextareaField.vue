<template>
    <textarea 
        :id="field.id" 
        @change="handleChange"
        :value="modelValue"
    ></textarea>
</template>

<script setup>
import fieldMixin from '../FieldMixin';
const emit = defineEmits(['update']);
const props = defineProps({
    field: {
        type: Object,
        required: true,
    },
    modelValue: {
        type: [String, Number, Boolean, Object, Array],
        default: '',
    },
});
let { handleChange } = fieldMixin.setup(props, { emit });

</script>

<style>
textarea {
  width: 100%;
  height: 150px;
  background-color: #333;
  color: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 12px;
  font-family: Arial, sans-serif;
  font-size: 14px;
  resize: vertical;
  margin-top: 20px;
}
</style>