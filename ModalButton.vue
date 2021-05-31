<template>
    <button @click="modalOpen = true">
        Open full screen modal!(with teleport!)
    </button>
    <teleport to="#app">
        <div v-if="modalOpen" class="modal">
            <div>
                I'm a teleported modal!
                (My parent is "body")
            </div>
            <button @click="modalOpen = false">Close</button>
        </div>
    </teleport>
</template>

<script>
export default {
  name: 'ModalButton',
  components: {},
  data() {
    return {
      modalOpen: false
    }
  },
  methods: {}
}
</script>

