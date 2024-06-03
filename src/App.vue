<template>
  <div id="app">
    <button @click="showModalA">Show Modal A</button>
    <button @click="showModalB">Show Modal B</button>
    <button @click="showModalC">Show Modal C</button>

    <div class="modal-display">
      <ModalA 
      :is-show="isShowModalA"
      :title="modalATitle" 
      @confirm="onConfirmModalA" 
      @cancel="onCancelModalA">
        {{ modalAContent }}
      </ModalA> 

      <ModalB
        :is-show="isShowModalB"
        :title="modalBTitle" 
        @confirm="onConfirmModalB" 
        @cancel="onCancelModalB">
          {{ modalBContent }}
      </ModalB> 


      <ModalC
        :is-show="isShowModalC"
        :title="modalCTitle" 
        @confirm="onConfirmModalC" 
        @cancel="onCancelModalC">
          {{ modalCContent }}
      </ModalC> 
    </div>


    <!-- 實際上想寫的做法 -->
    <!--
      <ModalA 
        :is-show="modalA.isShow"
        :title="modalA.title" 
        @confirm="modalA.onConfirm" 
        @cancel="modalA.onCancel">
          {{ modalA.content }}
      </ModalA> 

      以此類推
    -->
  </div>
</template>

<script>
import ModalA from './components/ModalA.vue'
import ModalB from './components/ModalB.vue'
import ModalC from './components/ModalC.vue'


export default {
  name: 'App',
  components: {
    ModalA,
    ModalB,
    ModalC
  },

  data() {
    return {
      isShowModalA: false,
      isShowModalB: false,
      isShowModalC: false,
      modalATitle: 'Modal A',
      modalAContent: 'This is Modal A',
      modalBTitle: 'Modal B',
      modalBContent: 'This is Modal B',
      modalCTitle: 'Modal C',
      modalCContent: 'This is Modal C'
    }
  },

  methods: {
    showModalA() {
      this.isShowModalB = false
      this.isShowModalC = false
      this.isShowModalA = true
    },

    showModalB() {
      this.isShowModalA = false
      this.isShowModalC = false
      this.isShowModalB = true
    },

    showModalC() {
      this.isShowModalA = false
      this.isShowModalB = false
      this.isShowModalC = true
    },

    onConfirmModalA() {
      console.log('Modal A confirmed')
    },

    onCancelModalA() {
      console.log('Modal A canceled')
    },

    onConfirmModalB() {
      console.log('Modal B confirmed')
    },

    onCancelModalB() {
      console.log('Modal B canceled')
    },

    onConfirmModalC() {
      console.log('Modal C confirmed')
    },

    onCancelModalC() {
      console.log('Modal C canceled')
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.modal-display {
  display: flex;
  justify-content: center;
  margin-top: 24px;
}
</style>
