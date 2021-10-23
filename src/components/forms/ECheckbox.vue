<template>
  <div class="e-checkbox">
    <input
      v-model="checked"
      class="e-checkbox__input"
      :checked="checked ? 'checked' : ''"
      type="checkbox"
      :name="name"
    />
    <span class="e-checkbox__switch"></span>
  </div>
</template>

<script>
export default {
  name: "e-checkbox",
  props: {
    value: Boolean,
    name: String,
  },
  computed: {
    checked: {
      set(value) {
        this.$emit('input', value)
      },
      get() {
        return this.value
      }
    }
  },
};
</script>

<style lang="scss" scoped>
.e-checkbox {
  position: relative;
  &__input {
    height: 100%;
    width: 100%;
    position: absolute;
    left: 0;
    top: 0;
    z-index: 1;
    opacity: 0;
    cursor: pointer;
    &:checked {
      & + span:before {
        border-color: #1390e5;
      }
      & + span {
        border: 2px solid #1390e5;
      }
    }
  }
  &__switch {
    display: block;
    height: 28px;
    width: 28px;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 4px;
    &:before {
      content: "";
      position: absolute;
      height: 8px;
      width: 14px;
      border-left: 2px solid white;
      border-bottom: 2px solid white;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%) rotate(-45deg);
    }
  }
}
</style>
