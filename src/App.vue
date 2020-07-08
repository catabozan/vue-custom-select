<template>
  <div id="app">
    <CustomSelect :options="options" label="Label test"></CustomSelect>
  </div>
</template>

<script>
import CustomSelect from "@/components/CustomSelect";

export default {
  name: 'App',
  components: {
    CustomSelect
  },
  data(){
    return {
      options: [
        {
          label: 'Sibiu',
          value: 'sb'
        },
        {
          label: 'Selimbar',
          value: 'sl'
        },
        {
          label: 'This is a label',
          value: 'label_value'
        },
      ]
    }
  }
}
</script>

<style>
  body{
    background-color: gray;
  }
</style>
