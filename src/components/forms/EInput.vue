<template>
  <div class="e-input">
    <input
      v-model="input"
      class="e-input__input"
      :type="type || 'text'"
      :name="name"
      :placeholder="placeholder"
      @blur="change"
      @focus="$emit('focus', $event)"
    />
  </div>
</template>

<script>
export default {
  name: "e-input",
  props: {
    type: String,
    value: String,
    name: String,
    placeholder: String,
    disabled: Boolean,
  },
  computed: {
    input: {
      set(value) {
        this.$emit("input", value);
        this.isChange = true;
      },
      get() {
        return this.value;
      },
    },
  },
  methods: {
    change() {},
  },
};
</script>

<style lang="scss" scoped>
.e-input {
  position: relative;
  &__input {
    width: 100%;
    height: 52px;
    color: #2c2738;
    background: #ffffff;
    padding: 16px 57px 15px 16px;
    border: 1px solid #dbe2ea;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 21px;
    transition: all 0.2s ease-in-out;
    &::placeholder {
      color: #7C9CBF;
    }
    &:focus {
      border: 2px solid #0880AE;
      outline: none;
    }
  }
}
</style>
