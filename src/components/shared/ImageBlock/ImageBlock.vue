<template>
  <div class="image-block">
    <div class="image-block-title">
      <span><slot name="title"></slot></span>
    </div>
      <div class="image-block-image">
        <div class="image-block-reaction" :style="{top: item.top,  left: item.left}" v-for="(item, index) in reactions" :key="index">
          <span >{{ item.value }}</span>
        </div>
        <img :src="image" alt="image">
      </div>
    <div class="image-block-buttons">
      <button class="image-block-button" @click="addReaction">{{ buttonLabel }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageBlock",
  data() {
    return {
      reactions: []
    }
  },
  props: {
    image: {
      type: Object,
      required: true
    },
    buttonLabel: {
      type: String,
      required: true
    },
    reaction: {
      type: String,
      default: '💖'
    }
  },
  methods: {
    addReaction() {
      const img = document.querySelector('.image-block-image img');
      const imgWidth = img.clientWidth;
      const imgHeight = img.clientHeight;
      const left = Math.floor(Math.random() * imgWidth);
      const top = Math.floor(Math.random() * imgHeight);
      const reaction = {
        left : left + 'px',
        top : top + 'px',
        value: this.reaction
      }
      this.reactions.push(reaction);
    }
  }
}
</script>

<style lang="scss">
.image-block {
  padding: 35px 35px 45px;

  &-image {
    margin-top: 38px;
    position: relative;
  }

  &-buttons{
    margin-top: 15px;
  }

  &-reaction {
    position: absolute;
    top: 10px;
    left: 0;

    animation: fade 1s ease-in-out;
    transition: all 1s ease-in-out;
  }

  &-button {
    appearance: none;
    border: none;
    font-family: 'Average Sans', sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 26px;
    /* identical to box height */


    color: #D9D9D9;

    background: #1E1E1E;
    border-radius: 5px;

    width: 100%;

    padding: 8px 0;

    cursor: pointer;

    &:active {
      background: #2E2E2E;
    }
  }
}

@keyframes fade {
  from {
    transform: translateY(30px);
    opacity: 0;
  } to {
    transform: translateY(0);
    opacity: 1;
  }
}
</style>