<script setup>
import BaseButton from "./components/BaseButton.vue";
import { ref } from "vue";
import img1 from "./assets/img1.jpg";
import img2 from "./assets/img2.jpg";
import img3 from "./assets/img3.jpg";
import img4 from "./assets/img4.jpg";
import img5 from "./assets/img5.jpg";
import img6 from "./assets/img5.jpg";

const step = ref(0);

const stepData = [
  {
    src: img1,
    text: "Вашему вниманию представляется очень важный для меня чечик  💟",
  },

  {
    src: img2,
    text: "Благодаря ей я пересмотрел взгляд на многие вещи, например присмотреть за этим красавщиком",
  },

  {
    src: img3,
    text: "Посетил кучу новых мест, слушал много классной музыки",
  },

  {
    src: img4,
    text: "Вкусно кушали, каждый раз когда она фоткает еду я кайфую  💕",
  },

  {
    src: img5,
    text: "Открывались друг другжке. С ней я могу быть настоящим!",
  },

  {
    src: img6,
    text: "Это были лучшие 3 месяца в моей жизни, и дальше у нас будет только лучше. I love u, te amo, вельми кахаю! 💏",
  },
];

const changeCurrentStep = () => {
  step.value = step.value + 1;
};
</script>

<template>
  <div class="root">
    <div class="content" v-if="step <= 5">
      <img :src="stepData[step].src" />
      <p>{{ stepData[step].text }}</p>
    </div>
    <div v-else class="end">Спасибо за внимание!</div>
    <div v-if="step <= 5">
      <BaseButton
        :msg="step < 5 ? 'Согласна' : 'И я тебя люблю'"
        :isStatic="true"
        :changeCurrentStep="changeCurrentStep"
      />

      <BaseButton msg="Ой всё!" :isStatic="false" />
    </div>
  </div>
</template>

<style scoped>
.root {
  background-color: #a40afc;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
}

.content {
  max-width: 500px;
  width: 100%;
  display: flex;
  gap: 16px;
  align-items: center;
}

.content img {
  object-fit: cover;
  width: 70%;
}

.content p {
  font-size: 18px;
  color: #fff;
}

.end {
  font-size: 24px;
  color: #fff;
  text-transform: uppercase;
}
</style>
