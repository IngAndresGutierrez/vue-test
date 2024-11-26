<template>
    <input
        :type="field.type || 'text'"
        :name="field.id"
        :disabled="field.disabled ?? null"
        :value="modelValue"
        @keyup="updateData"
    />
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
let { handleChange, debounce } = fieldMixin.setup(props, { emit });
const updateData = (event) => {
    debounce(handleChange, 50)(event);
};

</script>
<style lang="css">
input[type="text"] {
  background-color: #333;
  border: 1px solid #ccc;
  color: white;
  padding: 12px 20px;
  font-size: 16px;
  border-radius: 5px;
  width: 100%;
  box-sizing: border-box;
  margin-bottom: 20px;
}

input[type="text"]:focus {
  outline: none;
  border-color: #444;
}
</style>
