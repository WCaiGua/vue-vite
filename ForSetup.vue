<template>
    <div class="container" ref="root">
        {{readersNumber}}
        {{book}}
    <div v-for="(item, i) in list" :ref="el=> {if (el) divs[i] = el}">
        {{item}}
    </div>
    </div>
</template>

<script>
import {h, ref, reactive, onMounted, onBeforeUpdate, watchEffect} from 'vue'
export default {
  name: 'ForSetup',
  setup() {
    const readersNumber = ref(0)
    const book = reactive({ title: 'guide' })

    const root = ref(null)
    const list = reactive([1,2,3])
    const divs = ref([])

    watchEffect(()=>{
      // DOM更新之前运行，因此，模板引用还没有持有对元素的引用。
      console.log('watchEffect',root.value)
    },{
      flush: 'post'
    })

    onMounted(()=>{
      // DOM元素将在初始渲染后分配给ref
      console.log(root.value)
    })

    // 确保在每次更新之前重置ref
    onBeforeUpdate(()=>{
      divs.value = []
    })

    return {
      readersNumber,
      book,
      root,
      list,
      divs,
    }
    // return ()=> h('div',{ref:root})
    // return ()=> h('div',[readersNumber.value, book.title])
  }
}
</script>
