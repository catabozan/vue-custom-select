<template>
    <div class="bg-white">
        <div @click="showOptions = !showOptions"
             class="p-2"
             ref="defaultoption"
        >
            <span class="default capitalize">{{ selectedOption.label }}</span>
        </div>
        <div class="options overflow-y-scroll" :style="{ maxHeight: showOptions ? calculateHeight + 'px' : '0px' }">
            <div class="option p-2"
                 v-for="opt in options"
                 :key="opt.label"
                 :class="{ 'bg-orange-500 text-white' : opt === selectedOption }"
                 @click="onOptionClick(opt)"
            >
                <span class="capitalize">
                    {{ opt.label }}
                </span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CustomSelect",
        props: {
            options: {
                type: Array,
                required: true
            },
            maxHeight: {
                type:  Number,
                default: 150
            }
        },
        data() {
          return {
              showOptions: false,
              selectedOption: {}
          }
        },
        computed: {
            getDefaultOption(){
                return this.options.filter(opt => {
                    return opt.default === true
                })[0]
            },
            calculateHeight() {
                const optionHeight = this.$refs.defaultoption.getBoundingClientRect().height;
                const totalHeight = optionHeight * this.options.length;
                return totalHeight < this.maxHeight ? totalHeight : this.maxHeight
            }
        },
        methods: {
            onOptionClick(option){
                this.selectedOption = option;
                this.showOptions = false;
            }
        },
        created() {
            this.selectedOption = this.getDefaultOption;
        }
    }
</script>

<style scoped>
    .options {
        transition: max-height 0.25s ease-out;
    }
    .option:hover {
        @apply bg-orange-500 text-white;
    }
</style>