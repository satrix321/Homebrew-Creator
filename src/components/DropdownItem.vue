<template>
  <button class="dropdown-item" :class="{ 
    'dropdown-item--is-clicked': isClicked,
    }" @click="click"
  >
    <slot></slot>
  </button>
</template>

<script>

export default {
  name: 'ButtonItem',
  props: {
    isClicked: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  methods: {
    click(event) {
      event.stopPropagation();
      this.$emit('click');
      this.$parent.$emit('dropdownItemClick');
    },
  },
};
</script>

<style lang="scss" scoped>
.dropdown-item {
  height: 30px;
  border: 0;
  padding: 0 8px 0 8px;
  color: $button-color;
  background-color: $button-background-color;
  outline: none;
  font-family: $site-font;
  font-size: 10pt;
  width: 100%;
  text-align: left;
  display: flex;
  align-items: center;
  border-top: 1px solid $toolbar-separator-color;
  white-space: nowrap;

  &:hover {
    background-color: $button-background-hover-color;
    cursor: pointer;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  &:active {
    background-color: $button-background-active-color;
  }

  &:disabled {
    color: $button-disabled-color;

    &:hover {
      background-color: $button-background-color;
    }
  }

  &.dropdown-item--is-clicked {
    background-color: $button-background-clicked-color;

    &:hover {
      background-color: $button-background-hover-color;
    }
  }

  ::v-deep svg {
    vertical-align: middle;
  }
}
</style>
