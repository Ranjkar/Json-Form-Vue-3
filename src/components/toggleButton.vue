<template>
    <div
      class="toggle"
      :class="{ 'toggle--active': value }"
      @click="toggleValue"
    >
      <div class="toggle__track"></div>
      <div class="toggle__handle"></div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'CustomToggle',
    props: {
      value: {
        type: Boolean,
        required: true
      }
    },
    methods: {
      toggleValue() {
        this.$emit('update:value', !this.value);
      }
    }
  };
  </script>
  
  <style scoped>
  .toggle {
    position: relative;
    width: 48px;
    height: 24px;
    background-color: #e5e7eb;
    border-radius: 12px;
    cursor: pointer;
  }
  
  .toggle__track {
    position: absolute;
    top: 50%;
    left: 4px;
    transform: translateY(-50%);
    width: 16px;
    height: 16px;
    background-color: #ffffff;
    border-radius: 50%;
    transition: transform 0.3s;
  }
  
  .toggle__handle {
    position: absolute;
    top: 50%;
    left: 4px;
    transform: translateY(-50%);
    width: 16px;
    height: 16px;
    background-color: #ffffff;
    border-radius: 50%;
    transition: transform 0.3s;
  }
  
  .toggle--active .toggle__track {
    transform: translateY(-50%) translateX(20px);
  }
  
  .toggle--active .toggle__handle {
    transform: translateY(-50%) translateX(8px);
  }
  </style>
  