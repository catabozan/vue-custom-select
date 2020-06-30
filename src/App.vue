<template>
  <div id="app">
    <CustomSelect :options="options"></CustomSelect>
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
          label: 'Localitate',
          default: true
        },
        {
          label: 'Selimbar'
        },
        {
          label: 'sibiu'
        }
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
