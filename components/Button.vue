<template lang="pug">
.wi-btn(:disabled='disabled', v-if="tag==='div'", @click="$emit('click', $event)", :class="'btn-type-' + btnType + ' ' + 'btn-color-' + color")
  slot
a.wi-btn(:disabled='disabled', v-else-if="tag==='a'", @click="$emit('click', $event)", :class="'btn-type-' + btnType + ' ' + 'btn-color-' + color")
  slot
button.wi-btn(:disabled='disabled', v-else='v-else', @click="$emit('click', $event)", :class="'btn-type-' + btnType + ' ' + 'btn-color-' + color")
  slot

</template>
<script>
export default {
  props: {
    color: {
      type: String,
      default: 'primary'
    },
    btnType: {
      type: String,
      default: 'square'
    },
    disabled: Boolean,
    tag: {
      type: String,
      default: 'button'
    }
  }
}
</script>
<style lang="stylus">
.wi-btn {
  position: relative;
  transition: top 0.02s ease-in-out;
  top: 0;
  padding: 10px 15px;
  margin: 12px;
  border-radius: 50px;
  /* border-shadow: none; */
  border-style: solid;
  box-shadow: 0px 4px 4px #c9c9c9, 0px -4px 4px #fff;
}

.wi-btn:disabled {
  opacity: .4;
}
.wi-btn .text-uppercase {
  text-transform: uppercase;
}
.wi-btn .text-capitalize {
  text-transform: capitalize;
}
.wi-btn:active:enabled {
  top: 2px;
  box-shadow: 0px 2px 3px #c9c9c9, 0px -2px 3px #fff;
  border-style: solid;
}
.wi-btn:focus:enabled {
  outline: none;
}
.wi-btn.btn-color-primary {
  background-color: #006cb2;
  border-color: #006cb2;
  color: #fff;
}
.selected {
  border-color: #006cb2;
  background-color: #bad1e2;
}
.wi-btn.btn-color-primary:hover {
  background-color: rgba(0,108,178,0.9);
}
.wi-btn.btn-color-success {
  background-color: #56aa3c;
  border-color: #56aa3c;
  color: #fff;
}
.wi-btn.btn-color-success:hover {
  background-color: rgba(86,170,60,0.9);
}
.wi-btn.btn-color-secondary {
  background-color: #ffd400;
  border-color: #ffd400;
  color: #fff;
}
.wi-btn.btn-color-secondary:hover {
  background-color: rgba(255,212,0,0.9);
}
.wi-btn.btn-color-danger {
  background-color: #cd1013;
  border-color: #cd1013;
  color: #fff;
}
.wi-btn.btn-color-danger:hover {
  background-color: #ab0303;
}
.wi-btn.btn-color-neutral {
  background-color: #ddd;
  border-color: #ddd;
  color: #fff;
}
.wi-btn.btn-color-neutral:hover {
  background-color: #ccc;
}
.wi-btn.btn-type-square {
  padding: 10px 25px;
  border-radius: 10px;
  font-size: 18px;
}
.wi-btn.btn-type-pill {
  font-size: 16px;
  padding: 10px 25px;
  border-radius: 30px;
}
</style>