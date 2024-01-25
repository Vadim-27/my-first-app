<template>
    <div>
<!-- <input v-bind="$attrs" v-model="inputValue"  v-on="listeners" class="custom-input" /> -->
 <input
 v-bind="$attrs"
    :value="price"
    @input="$emit('update:price', $event.target.value)"
    class="custom-input"
  />
    </div>
</template>

<script>


export default {
  name: 'CustomInput',
  // model: {
  //   prop: 'value',
  //   event: 'input',
  // },
  //  props: {
  //   value: {
  //     type: String,
  //     default: '',
  //   },
  // },
  // computed: {
  //   inputValue: {
  //     get() {
  //       return this.value;
  //     },
  //     set(newValue) {
  //       this.$emit('input', newValue);
  //     },
  //   },
  // },
  props: ['price'],
  emits: ['update:price']
  // props: ['price'],
 
  // computed: {
  //   listeners() {
  //     return {
  //       ...this.$attrs,
        
  //       input: event => {
  //         console.log('Input value:', event.target.value);
  //         this.$emit('update:modelValue', event.target.value);
  //       }
  //     };
  //   }
  // }
};
</script>

<style lang="scss" scoped>
@import '../../assets/scss/variables.scss';
.custom-input {
  height: 40px;
  max-width: 220px;
  width: 100%;
  border: 2px solid $main-color;
  font-size: 18px;
  outline: none;
  line-height: inherit;
  padding: 8px 15px;
  box-sizing: border-box;

  &::placeholder {
    color: inherit;
  }
}
</style>