<template>
  <div class="slider">
      <transition name="slider" mode="out-in">
        <div class="slider-open" v-if="isOpen" >
          <div class="slider-content">
            <slot name="content"></slot>
          </div>
          <div class="slider-arrow slider-arrow-container" @click="handleSlider">
            <img src="@/assets/arrow.svg" alt="">
          </div>
        </div>
        <div class="slider-hidden" v-else>
          <div class="slider-arrow slider-arrow-reverse" @click="handleSlider">
            <img src="@/assets/arrow.svg" alt="">
          </div>
          <div class="slider-placeholder">
              <div class="slider-placeholder-text">
                <slot name="placeholder">Placeholder</slot>
              </div>
          </div>
        </div>
      </transition>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Index.vue",
  data() {
    return {
      isOpen: false
    }
  },
  methods: {
    handleSlider() {
      this.isOpen = !this.isOpen;
    }
  }
})
</script>

<style lang="scss" scoped>
.slider {
  position: fixed;
  &-hidden {
    width: 45px;
    height: auto;
    background: #1E1E1E;
    border-width: 1px 1px 1px 0;
    border-style: solid;
    border-color: #929292;

    padding-bottom: 26px;
  }

  &-open {
    display: flex;
  }

  &-placeholder {
    width: 100%;
    height: 100%;
    margin-top: 15px;

    &-text {
      font-family: 'Average Sans', sans-serif;
      font-style: normal;
      font-weight: 400;
      font-size: 20px;
      line-height: 26px;

      color: #D9D9D9;

      writing-mode: tb-rl;
      transform: rotate(-180deg);
      text-align: center;

      width: 100%;
      display: flex;
      align-items: center;
    }
  }

  &-arrow {
    width: 45px;
    height: 45px;

    display: flex;
    justify-content: center;
    align-items: center;

    cursor: pointer;

    &-reverse {
      transform: rotate(180deg);
    }

    &-container {
      background: #1E1E1E;
      border-width: 1px 1px 1px 0;
      border-style: solid;
      border-color: #929292;
    }
  }

  &-content {
    min-width: 250px;
    min-height: 277px;
    clip-path: polygon(0% 0%, 100% 0%, 100% 80%, 80% 100%, 0 100%);
    background: #929292;
  }

  &-enter-active, &-leave-active {
    transition: all 1s;
  }

  &-enter-from,
  &-leave-to {
    transform: translateX(-102%)
  }

  &-leave-from,
  &-enter-to {
    transform: translateX(0)
  }

}
</style>