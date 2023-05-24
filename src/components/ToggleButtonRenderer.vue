<template>
  <div>
    <label :for="id" class="flex items-center cursor-pointer">
      <div class="relative">
        <input
          type="checkbox"
          class="hidden"
          :id="id"
          :checked="value"
          @change="$emit('update:modelValue', !value)"
        >
        <div class="toggle__line w-10 h-4 bg-gray-400 rounded-full shadow-inner"></div>
        <div
          class="toggle__dot absolute w-6 h-6 bg-white rounded-full shadow inset-y-0 left-0"
          :class="{ 'translate-x-6': value }"
        ></div>
      </div>
      <div class="ml-3 text-gray-700 font-medium">
        {{ label }}
      </div>
    </label>
  </div>
</template>

<script>
export default {
  props: {
    id: String,
    value: Boolean,
    label: String,
  },
};
</script>

<style scoped>
.toggle__line {
  transition: background-color 0.2s ease;
}

.toggle__dot {
  transition: transform 0.2s ease;
}
</style>
