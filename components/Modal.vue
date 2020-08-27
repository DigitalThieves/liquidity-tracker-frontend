<template lang="pug">
.modal.d-block(@click.stop='close')
  .modal-body(@click.stop='', :class='{ transparent: isTransparent }')
    .modal-header.container-fluid
      .row.align-items-center
        .col-3.text-left.pl-0
        .col-6.text-center
          slot(name="modal-header")
        .col-3.text-right.pr-0
          //- button.ml-0(@click.stop="close", color="secondary").py-1.px-2
          //-   strong X
    .modal-content(ref='content')
      slot
    .modal-footer(v-if='!noBtn').text-right
      slot(name="modal-footer")
        button.ml-0(color='danger', btnType="pill" @click.stop='close').mb-0 Stäng
</template>
<script>
import Button from './Button.vue'

export default {
  components: { Button },
  props: ['noBtn', 'isTransparent'],
  data: () => ({
    results: {}
  }),
  methods: {
    close (e) {
      this.$emit('close');
    }
  }
}
</script>
<style lang="stylus">
.modal {
  position: fixed;
  z-index: 100;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background: rgba(0,0,0,0.75);
}
.modal-wrap {
  padding: 20px;
}
.modal-body {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  max-width: 1080px;
  width: 95%;
  min-height: 200px;
  max-height: 95%;
  background: #fff;
  border-radius: 4px;
  padding: 15px;
  overflow-y: auto;
}
.modal-content {
  flex: 1 0 90%;
}
.modal-footer {
  border-top 1px solid #aaa
}
.modal-header {
  border-bottom 1px solid #aaa
  margin-bottom 15px
  padding-bottom 10px
}
</style>