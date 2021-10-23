<template>
  <button class="e-button">Зарегистрироваться</button>
</template>

<script>
export default {
  name: "e-button",
};
</script>

<style lang="scss" scoped>
.e-button {
  width: 100%;
  height: 56px;
  background: #0880ae;
  color: #ebf4f8;
  box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08),
    0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius: 6px;
  border: 2px solid #0880ae;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 21px;
  transition: all 0.3s ease-in-out;
  &:active {
    border-color: #2c273886;
    box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.0001), 0px 4px 8px rgba(44, 39, 56, 0.08);
  }
  &:disabled {
    background: #dbe2ea;
    color: #2c2738;
    border-color: #dbe2ea;
  }
  &:hover {
    box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.08),
      0px 24px 48px rgba(44, 39, 56, 0.16);
  }
}
</style>