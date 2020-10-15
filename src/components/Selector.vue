<template>
  <div class="category-selector">
    <p>{{ title }}</p>
    <select
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    >
      <option
        v-for="option in options"
        :key="option.id"
        :value="option.id"
        v-html="option.name"
      ></option>
    </select>
  </div>
</template>
<script>
export default {
  name: "Selector",
  props: ["modelValue", "title", "options"]
};
</script>
