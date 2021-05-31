<template>
    <div>
        {{userLocation}}
        {{userGeolocation}}
    </div>
</template>

<script>
import {inject} from 'vue'
export default {
  name: 'ForInject',
  setup(){
    const userLocation = inject('location','The Universe')
    const userGeolocation = inject('geolocation')
    return {
      userLocation,
      userGeolocation,
    }
  }
}
</script>
