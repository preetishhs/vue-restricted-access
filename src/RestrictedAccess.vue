<template>
  <div
    v-if="restricted"
    :class="['restricted-access', { 'strict-mode': config.strict }]"
  >
    <div
      class="restricted-access__message"
      v-if="!config.customStatusBox || !config.showStatusText"
    >
      <div class="lock">&#128274;</div>
      <div class="status-text">
        {{ config.statusText }}
      </div>
    </div>
    <div
      class="custom-message-wrapper"
      :class="['custom-message', { center: config.customStatusPositionCenter }]"
    >
      <slot name="custom-message" v-if="config.customStatusBox" />
    </div>
    <div
      :class="[
        'restricted-access__item-container',
        { 'strict-mode': config.strict }
      ]"
      :style="itemStyles"
    >
      <div
        class="restricted-overlay"
        :style="{ 'background-color': config.backgroundColor }"
      ></div>
      <slot v-if="config.strict !== true" />
    </div>
  </div>
  <div v-else>
    <slot />
  </div>
</template>
<script>
export default {
  props: {
    restricted: {
      required: true,
      type: Boolean
    },
    config: {
      required: false,
      default: () => {}
    }
  },
  computed: {
    itemStyles() {
      return {
        opacity: this.config.opacity,
        filter: `blur(${this.config.blur}px)`
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.restricted-access {
  position: relative;
  &.strict-mode {
    width: 100%;
    height: 100%;
  }
}
.restricted-access__message {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 20px;
  z-index: 3;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-flow: column;
}
.restricted-access__item-container {
  position: relative;
  filter: blur(4px);
  opacity: 0.5;
  &.strict-mode {
    min-height: 100px;
    width: 100%;
    height: 100%;
  }
}
.restricted-overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.2);
}
.custom-message {
  position: absolute;
  width: 100%;
  height: 100%;
  &.center {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
