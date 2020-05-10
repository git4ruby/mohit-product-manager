<template>
  <div>
     <b-button @click="modalShow = !modalShow"><i class="fas fa-edit"></i></b-button>
     <b-modal 
      v-model="modalShow"
      title="UpdateProduct"
      @show="showModal"
      @hidden="resetModal"
      @ok="handleSubmit"
      >

     </b-modal>
  </div>
</template>

<script>
export default {
  name: 'UpdateProduct',
  data() {
    return {
      modalShow: false
    }
  },
  methods: {
    showModal(){
      console.log('Model Opened')
    },
    resetModal(){
      console.log('Model Closed')
    },
    handleSubmit(bvModalEvt){
      // Prevent modal from closing
      bvModalEvt.preventDefault()
      console.log('Model Submitted')
    }
  }
}
</script>

<style>

</style>

