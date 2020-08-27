<template lang="pug">
.container.cover-page
  modal(v-if="editEntry" @close="editEntry = false")
    h1 {{ entryToEdit }}
  .row.h-100.align-items-center
    .col-12
      .row(v-for="month in transactions")
        .col-12.mb-4
          h1 {{ month.month }}
        .col-12.mb-5
          h2 Intäkter
          .px-3
            .row.py-3.bg-primary
              .col-2
                p.mb-0
                  strong Kund
              .col-2
                p.mb-0
                  strong Datum
              .col-5
                p.mb-0
                  strong Kommentar
              .col-1
                p.mb-0
                  strong Status
              .col-2.text-right
                p.mb-0
                  strong Summa
            .row.py-3(v-for="transaction, i in month.revenue", :class="i % 2 === 0 ? 'bg-white' : 'bg-secondary'" @click="open(transaction)").mouse-pointer
              .col-2
                p.mb-0 {{ transaction.company }}
              .col-2
                p.mb-0 {{ transaction.date }}
              .col-5
                p.mb-0 {{ transaction.comment }}
              .col-1
                p.mb-0 {{ transaction.status }}
              .col-2.text-right
                p.mb-0 {{ transaction.amount }} SEK
            .row.py-3.bg-primary.justify-content-between
              .col-2
                p.mb-0
                  strong Totalt
              .col-3.text-right
                p.mb-0 {{ total(month.revenue) }} SEK
        .col-12.mb-5
          h2 Utgifter
          .px-3
            .row.py-3.bg-primary
              .col-2
                p.mb-0
                  strong Kostnad
              .col-2
                p.mb-0
                  strong Datum
              .col-5
                p.mb-0
                  strong Kommentar
              .col-1
                p.mb-0
                  strong Status
              .col-2.text-right
                p.mb-0
                  strong Summa
            .row.py-3(v-for="transaction, i in month.costs", :class="i % 2 === 0 ? 'bg-white' : 'bg-secondary'" @click="open(transaction)").mouse-pointer
              .col-2
                p.mb-0 {{ transaction.company }}
              .col-2
                p.mb-0 {{ transaction.date }}
              .col-5
                p.mb-0 {{ transaction.comment }}
              .col-1
                p.mb-0 {{ transaction.status }}
              .col-2.text-right
                p.mb-0 {{ transaction.amount }} SEK
            .row.py-3.bg-primary.justify-content-between
              .col-2
                p.mb-0
                  strong Totalt
              .col-3.text-right
                p.mb-0 {{ total(month.costs) }} SEK
</template>

<script>
import Modal from '~/components/Modal.vue'
export default {
  components: {
    Modal
  },
  mounted () {
  },
  methods: {
    total (stream) {
      let sek = 0
      for (let i = 0; i < stream.length; i++) {
        sek += stream[i].amount
      }
      return sek
    },
    open (transaction) {
      this.entryToEdit = transaction
      this.editEntry = true
    }
  },
  data () {
    return {
      editEntry: true,
      entryToEdit: null,
      transactions: [
        {
          month: 'Januari',
          revenue: [{
            company: 'Qamcom',
            date: 'Måndag, 23 Jan',
            comment: 'Vi gjorde mycket jobb, de är asnöjda och betalade därför in tidigare än väntat. Grymt!',
            status: 'GRÖN',
            amount: 138520
          }, {
            company: 'Server.pro',
            date: 'Onsdag, 18 Jan',
            comment: 'Carl och Andre är ju ta mig fan på ett skönt gäng ändå.',
            status: 'GRÖN',
            amount: 30280
          }],
          costs: [{
            company: 'Offerta',
            date: 'Fredag, 27 Jan',
            comment: 'Ska bli så jävla skönt att slippa betala de här f*****a',
            status: 'GRÖN',
            amount: 2900
          }]
        }
      ]
    }
  }
}
</script>

<style lang="stylus">
.cover-page
  height 100vh
  min-height 100vh
.bg-primary
  background-color #2ba2f1 !important
.bg-secondary
  background-color #cddae2 !important
.mouse-pointer
  cursor pointer !important
</style>
