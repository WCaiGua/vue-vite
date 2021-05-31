<template>
    <!--<input :value="modelValue" v-focus-->
    <!--       @input="emitValue"-->
    <!--       type="text">-->
    <!--<input type="range" min="0" max="500" v-model="pinPadding">-->


    <!--<for-array>-->
    <!--    <template v-slot:default="slotProps">-->
    <!--        <span v-pin:[direction]="pinPadding">{{slotProps}}</span>-->
    <!--    </template>-->
    <!--</for-array>-->
</template>

<script>
import ForArray from './ForArray.vue'
export default {
  name: 'Test',
  components:{
    ForArray
  },
  directives:{
    focus:{
      mounted(el){
        el.focus()
      }
    },
    pin:{
      mounted(el,binding) {
        console.log(el,binding)
        el.style.position = 'fixed'
        const s = binding.arg || 'top'
        el.style[s] = binding.value + 'px'
      },
      updated(el,binding){
        const s = binding.arg || 'top'
        el.style[s] = binding.value + 'px'
      }
    }
  },
  props: {
    modelValue: String,
    modelModifiers: {
      default: () => ({})
    }
  },
  emits: ['update:modelValue'],
  data() {
    return {
      direction:'left',
      pinPadding: 0,
    }
  },
  created() {
    console.log(this.modelModifiers) // { capitalize: true }
  },
  methods: {
    emitValue(e){
      let value = e.target.value
      if(this.modelModifiers.capitalize){
        value = value.charAt(0).toUpperCase() + value.slice(1)
      }
      this.$emit('update:modelValue',value)
    }
  }
}
</script>
