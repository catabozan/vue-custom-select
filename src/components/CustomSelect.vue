<template>
    <div class="bg-white relative">
        <div @click="showOptions = !showOptions"
             class="p-2"
             ref="defaultoption"
        >
            <span class="default capitalize">{{ selectedOption }}</span>
        </div>
        <div class="bg-white w-full options absolute overflow-y-scroll" :style="{ maxHeight: showOptions ? calculateHeight + 'px' : '0px' }">
            <div class="option p-2"
                 v-for="opt in [label, ...options]"
                 :key="opt"
                 :class="{ 'bg-orange-500 text-white' : opt === selectedOption }"
                 @click="onOptionClick(opt)"
            >
                <span class="capitalize">
                    {{ opt }}
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
            label: {
                type: String,
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
            this.selectedOption = this.label
        }
    }
</script>

<style scoped>
    .options {
        transition: max-height .4s ease-out;
    }
    .option:hover {
        @apply bg-orange-500 text-white;
    }
</style>