<template>
    <div >
    <HelloWorld v-on:onSubmit="onSubmit"/>

    <b-table class="table" striped hover :items="items" bordered="true" outlined="true" ></b-table>
    
  </div>
</template>

<script>

import HelloWorld from './HelloWorld.vue';
export default {
     components:{
       HelloWorld
     },
     data() {
      return {
         
        items: [
          { Invoice_Number : 40, Payment_Status: 'Paid',  Balance: '0.00' },
          { Invoice_Number : 21, Payment_Status: 'Paid', Balance: '0.00' },
          { Invoice_Number : 89, Payment_Status: 'Pending',  Balance: '51,000', _cellVariants: {  Balance: 'danger' ,Payment_Status: 'danger' } },
          { Invoice_Number : 38, Payment_Status: 'Paid',  Balance: '0.00' },
          { Invoice_Number : 31, Payment_Status: 'Pending',  Balance: '4,370.00' }
        ]
      }
    },
  methods:{
   onClick(){
     this.$refs['modal'].show()
   },
   onSubmit(newForm){
     this.items = [...this.items,newForm]
    }
  }
   
}
</script>

<style scoped>
.table{
  color: #fff;
}
</style>