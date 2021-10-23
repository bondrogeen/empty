<template>
  <div :class="['e-select', { 'e-select--active': show }]">
    <i class="icon" @click="click"></i>
    <input
      class="e-select__input"
      v-model="search"
      readonly
      :name="name"
      :placeholder="placeholder || ''"
      :autocomplete="'off'"
      @click="click"
      @blur="select(false)"
      @focus="$emit('focus', $event)"
    />
    <div class="e-select__content" v-show="show">
      <div
        class="e-select__content--item"
        v-for="(item, i) in filterList"
        :key="i"
        @mousedown="select(item)"
      >
        {{ item.label }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "e-select",
  props: {
    type: String,
    placeholder: String,
    value: {
      type: [String, Number],
      default: "",
    },
    name: String,
    list: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      selected: {},
      show: false,
      input: "",
    };
  },
  computed: {
    filterList() {
      return this.list ?? [];
    },
    search: {
      set(value) {
        this.input = value;
      },
      get() {
        const list = this.list ?? [];
        const label =
          list.find(
            (item) =>
              item.value === this.selected?.value || item.value === this.value
          )?.label || "";
        return label || "";
      },
    },
  },
  methods: {
    send(value) {
      this.$emit("input", value);
    },
    select(item) {
      if (item) {
        this.selected = item;
        this.send(item.value);
        this.input = item.value;
      } else {
        this.search = this.selected.label || this.value || "";
      }
      this.show = false;
    },
    click(e) {
      this.show = !this.show;
      this.$emit("click", e);
    },
  },
};
</script>

<style lang="scss" scoped>
.e-select {
  position: relative;
  height: 52px;
  .icon {
    position: absolute;
    top: 22px;
    right: 15px;
    cursor: pointer;
    display: block;
    height: 10px;
    width: 20px;
    background-repeat: no-repeat;
    background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAJCAYAAAA7KqwyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAB3SURBVHgBjZKxDYAwDASdlFRsQMkU1IzBSqzAFlAzCRtQ0YZ8JEuR4yT+xpblu8hS3LyfgWKubaFpHMiS5/1oPe7U+3yAaoV51/PLFkm+Awas56Yn0WDUdEJPUoMRF2Jai0gNLgSahGcarAqkRJ4oowpyCdL6Iz81i4ZsRxcbjgAAAABJRU5ErkJggg==");
  }

  &__input {
    height: 52px;
    width: 100%;
    padding: 0 16px;
    font-size: 14px;
    font-weight: 400;
    padding: 0 20px 0 10px;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 21px;
    color: #2c2738;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    cursor: pointer;
    outline: none;
    &:focus {
      border: 2px solid #0880ae;
    }
    &:disabled {
      border-color: #6c7883;
      cursor: default;
      opacity: 0.35;
    }
  }
  &__content {
    position: absolute;
    top: 56px;
    width: 100%;
    z-index: 3;
    color: #756f86;
    max-height: 200px;
    overflow: auto;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04),
      0px 20px 20px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    padding: 12px 0;
    overflow: hidden;
    &--item {
      height: 44px;
      color: inherit;
      text-align: left;
      cursor: pointer;
      padding: 12px 15px;
      &:hover {
        background-color: #ebf4f8;
      }
    }
  }
}
</style>
