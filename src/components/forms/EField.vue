<template>
  <div :class="['e-field', { 'e-field--inline': inline }]">
    <div class="e-field__label">
      <slot name="label">{{ label }}</slot>
    </div>
    <div class="e-field__input">
      <slot></slot>
    </div>
    <div class="e-field__hint">{{ error }}</div>
  </div>
</template>

<script>
export default {
  name: "e-field",
  props: {
    label: String,
    error: String,
    inline: Boolean,
  },
};
</script>

<style lang="scss" scoped>
.e-field {
  position: relative;
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
  transition: all 0.2s ease-in-out;
  &--inline {
    flex-direction: row-reverse;
    align-items: center;
    .e-field__label {
      padding: 0 0 0 8px;
    }
  }
  &__label {
    flex: 1 1 auto;
    color: #756f86;
    padding: 0 0 7px 0;
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
    cursor: default;
    user-select: none;
    text-overflow: ellipsis;
  }
  &__hint {
    height: 18px;
    margin: 8px 0;
    color: #ff7171;
    max-width: 100%;
    word-wrap: break-word;
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 18px;
  }
  &:hover &__hint {
    display: block;
  }
}
</style>
