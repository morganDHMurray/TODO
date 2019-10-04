<template>
  <li>
    <label :for="`checkbox-${id}`">
      <input
        :id="`checkbox-${id}`"
        type="checkbox"
        v-bind:value="value"
        v-on:input="$emit('input', $event.target.checked)"
      />
    </label>
    - {{ description }}
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    id: Number,
    value: Boolean,
    description: String
  }
};
</script>
