<template>
 
  <div class="myform">
     <h1>JSON Forms Vue 3</h1>
    <json-forms
      :data="data"
      :renderers="renderers"
      :schema="schema"
      :uischema="uischema"
      @change="onChange"
    />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { JsonForms } from "@jsonforms/vue"; // import JsonForms component
import {
  vanillaRenderers, // default renderers
} from "@jsonforms/vue-vanilla";

const renderers = [
  ...vanillaRenderers,
  // here you can add custom renderers
];
import schema from "./jsonForm/schema.json"; // import schema for the form
import uischema from "./jsonForm/uischema.json" // import uischema its layout

export default defineComponent({
  name: "App",
  components: {
    JsonForms,
  },
  data() {
    return {
      // freeze renderers for performance gains
      renderers: Object.freeze(renderers),
      schema, // schema
      uischema, // layout
    };
  },
  methods: {
    onChange(event) {
      console.log(event);
    },
  },
});
</script>

