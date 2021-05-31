<template>
    <!--<ul>-->
    <!--    <li>CHAIR</li>-->
    <!--    <li>DESK</li>-->
    <!--    <li>BLACKBOARD</li>-->
    <!--    <li>FAN</li>-->
    <!--</ul>-->
    <h1>CHAIR</h1>
    <h1>DESK</h1>
</template>

<script>
export default {
  name: 'CssMarker',
  components: {},
  data() {
    return {}
  },
  methods: {}
}
</script>

<style scoped>
    li {
        padding-left: 12px;
        cursor: pointer;
        color: green;
    }

    li::marker {
        content: ">";
    }

    h1{
        display: list-item;
        padding-left:8px;
        font-size:14px;
    }
    h1::marker{
        content: '▍';
    }
    h1:nth-child(2)::marker{
        content: '😅';
    }
</style>
