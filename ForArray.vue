<template>
  <div class="container">
    <ul>
        <li v-for="(item, index) in items">
            <!--{{item}}-->
            <slot :item="item" :value="item"></slot>
        </li>
    </ul>
  </div>
    <div>

    </div>
</template>

<script>
export default {
  name: 'ForArray',
  components: {},
  data() {
    return {
      items:['dog','bird']
    }
  },
  methods: {}
}
</script>
