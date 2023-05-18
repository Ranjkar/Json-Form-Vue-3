<template>
 
  <div class="myform">
     <h1>JSON Forms Vue 3</h1>
       <JsonForms
         :data="data"
         :schema="schema"
         :uischema="uischema"
         :renderers="renderers"
         @change="onChange"
       />
       <button type="submit" class="SubmitBtn" @click.prevent="SubmitData">Submit</button>
  </div>

  <div class="myform">
    <h1>Submited Data</h1>
    <div v-for="(data, index) in submitedData" :key="index">
      <div>
        <h3>Form Data {{index + 1}}</h3>
        <pre>{{data}}</pre>
      </div>
    </div>
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
    return { // declare variables
      renderers: Object.freeze(renderers),   // freeze renderers for performance gains
      schema, // schema
      uischema, // layout
      formData: {}, // form data
      submitedData: []
    };
  },
  methods: {
    onChange(event) {
      if (event.data ===  undefined) { // if data is undefined return
        return;
      }
      this.formData = event.data; // update form data
    },
    SubmitData() {
      if (Object.keys(this.formData).length === 0) { // if form data is empty return
        return;
      }
      console.log(this.formData);
      this.submitedData.push(this.formData); // push form data to submitedData array
      this.formData = {}; // reset form data
    },
  },
});
</script>

