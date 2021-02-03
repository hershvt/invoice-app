<template>
  <div>
   <b-button v-b-modal.modal-lg variant="primary">Create Invoice</b-button>

     <b-modal ref="modal" id="modal-lg" size="lg" title="Invoice" hide-footer="false">
       <div>
    <b-form action="mailto:info@gmail.com" method="post" @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Hours of Work:"
        label-for="input-1"
        description="Rate of work : 20$ / hour.s"
      >
        <b-form-input
          id="input-1"
          v-model="form.hours"
          type="text"
          placeholder="Enter hours. "
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Equipment Expenses:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.expense"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Invoice Number:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.Invoice_Number"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Payment Status:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.Payment_Status"
          :options="payment"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-2" label="Balance Amount :" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.Balance"
          placeholder="Enter balance amount (if any)"
          required
        ></b-form-input>
      </b-form-group>
      
      <b-form-group id="input-group-3" label="Department:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.department"
          :options="department"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-4" label="Payment Type:" v-slot="{ ariaDescribedby }">
        <b-form-checkbox-group
          v-model="form.checked"
          id="checkboxes-4"
          :aria-describedby="ariaDescribedby"
        >
          <b-form-checkbox v-b-popover.hover.top="'Please pay the exact amount'" value="Cash">Cash</b-form-checkbox>
          <b-form-checkbox  v-b-popover.hover.top="'Please send the cheque to the following add...'" value="Cheque">Cheque</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button class="button-reset" type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Invoice Data :">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>

     </b-modal>
    

  </div> 


</template>

<script>
  export default {
    name : 'HelloWorld',
    data() {
      return {
        form: {
          hours: '',
          expense: '',
          Invoice_Number: '',
          Payment_Status : '',
          Balance : '',
          payment: null,
          checked: []
        },
        department: [{ text: 'Select One', value: null }, 'IT', 'Electrical', 'Business Development', 'Logistics'],
        payment: [{ text: 'Select One', value: null }, 'Pending', 'Paid'],
        show: true
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        const newForm = {
          hours : this.hours,
          expense : this.expense,
          number : this.number,
          status : this.status,
          balance : this.balance,
          payment : this.payment,
          checked : this.checked

        }
       this.$emit('onSubmit',newForm)
       this.$refs['modal'].hide()
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.hours = ''
        this.form.expense = ''
        this.form.payment= null
        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.button-reset{
  left: 100px;
}
</style>
