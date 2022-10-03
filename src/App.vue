<script lang="ts">
import { defineComponent } from 'vue';
import SliderLeft from './components/shared/Sliders/SliderLeft.vue';
import SliderRight from "./components/shared/Sliders/SliderRight.vue";
import ToDo from './components/shared/ToDo/ToDo.vue';
import TextInfo from "./components/shared/TextInfo/TextInfo.vue";
import ImageBlock from "./components/shared/ImageBlock/ImageBlock.vue";

import kitty from "./assets/KITTY.jpeg";


export default defineComponent({
  name: "App",
  components: {
    ImageBlock,
    TextInfo,
    ToDo,
    SliderLeft,
    SliderRight
  },
  data() {
    return {
      image: kitty,
      shoppingData: {
        title: 'Shopping list',
        items: [
          {
            title: 'Milk',
            isDone: false
          },
          {
            title: 'Bread',
            isDone: false
          },
          {
            title: 'Ham',
            isDone: false
          },
          {
            title: 'Cheese',
            isDone: false
          },
          {
            title: 'Water',
            isDone: false
          }
        ],
        doneItems: 0
      },
      booksData: {
        title: 'Books to read',
        items: [
          {
            title: 'SAPIENS BY YUVAL NOAH HARARI',
            isDone: false
          },
          {
            title: 'THE THEORY OF EVERYTHING BY STEPHEN HAWKING',
            isDone: false
          },
          {
            title: 'A WILD SHEEP CHASE BY HARUKI MURAKAMI',
            isDone: false
          },
          {
            title: ' CLEAN CODE BY ROBERT MARTIN',
            isDone: false
          },
        ],
        doneItems: 0
      },
    }
  },
  methods: {
    updateShoppingList(data: any) {
      this.shoppingData = data;
    },
    updateBooksList(data: any) {
      this.booksData = data;
    }
  }
})
</script>

<template>
  <div class="main">
    <SliderLeft style="margin-top: 100px">
      <template v-slot:content>
        <ToDo :data="shoppingData" @update="updateShoppingList"></ToDo>
      </template>
      <template v-slot:placeholder>
        <span>SHOPPING LIST [{{ shoppingData.doneItems }}/{{shoppingData.items.length}}] </span>
      </template>
    </SliderLeft>
    <SliderLeft style="margin-top: 600px">
      <template v-slot:content>
        <TextInfo>
          <template v-slot:title>
            <span>MAMAAA OOOO</span>
          </template>
          <template v-slot:content>
            <div>THIS ONE IS NOT A LIST - JUST SOME PLAIN OL’ TEXT. <br>

              IS THIS THE REAL LIFE <br>
              IS THIS JUST FANTASY <br>
              CAUGHT IN A LANDSIDE <br>
              NO ESCAPE FROM REALITY <br>

              <br><br>

              BY THE WAY IF THERE WAS A REALLY LONG LINE, I’M PRETTY <br>
              SURE AT SOME POINT IT WOULD WRAP TO THE NEXT LINE. <br>
              JUST LIKE THE OTHER ELEMENTS ON THIS PAGE, THIS ONE <br>
              HAS A PRE-DEFINED MAX-WIDTH
            </div>
          </template>
        </TextInfo>
      </template>
      <template v-slot:placeholder>
        <span> MAMAAA OOOO </span>
      </template>
    </SliderLeft>
    <SliderRight style="margin-top: 150px">
      <template v-slot:placeholder>
        <span> Kitty </span>
      </template>
      <template v-slot:content>
        <keep-alive>
          <ImageBlock button-label="AWW :3" :image="image">
            <template v-slot:title>
              <span> KITTY </span>
            </template>
          </ImageBlock>
        </keep-alive>
      </template>
    </SliderRight>
    <SliderRight style="margin-top: 650px">
      <template v-slot:placeholder>
        <span> BOOKS TO READ [{{ booksData.doneItems }}/{{ booksData.items.length}}]</span>
      </template>
      <template v-slot:content>
        <ToDo :data="booksData" @update="updateBooksList"></ToDo>
      </template>
    </SliderRight>
  </div>
</template>

<style scoped lang="scss">
.main {
  background: $dark;
  width: 100%;
  height: 100vh;
  font-size: 20px;
  font-family: sans-serif;
  text-transform: uppercase;
}
</style>
