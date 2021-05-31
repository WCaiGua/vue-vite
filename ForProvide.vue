<template>
    <for-inject />
</template>

<script>
import { provide, reactive, ref } from 'vue'
import ForInject from './ForInject.vue'

export default {
  name: 'ForProvide',
  components: { ForInject },
  setup(){
    let location = ref('North Pole')
    const geolocation = reactive({
      longitude:120,
      latitude: 135
    })
    location = 'Eastern'
    provide('location',location)
    provide('geolocation',geolocation)
  }
}
</script>
