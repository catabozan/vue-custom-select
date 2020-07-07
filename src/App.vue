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
      options: ['Selimbar', 'Sibiu', 'Bucuresti']
    }
  }
}
</script>

<style>
  body{
    background-color: gray;
  }
</style>
