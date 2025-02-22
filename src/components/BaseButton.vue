<script setup>
import { ref } from "vue";

function randomNumber() {
  return Math.floor(Math.random() * 80);
}

const { msg, isStatic, changeCurrentStep } = defineProps({
  msg: String,
  isStatic: Boolean,
  changeCurrentStep: Function,
});

const x = ref(isStatic ? 40 : 60);
const y = ref(isStatic ? 90 : 90);
const loading = ref(false);

const mouseenter = () => {
  if (isStatic) return;

  x.value = randomNumber();
  y.value = randomNumber();
};

const click = () => {
  if (!isStatic) return;
  loading.value = true;

  setTimeout(() => {
    changeCurrentStep();
    loading.value = false;
  }, 2000);
};
</script>

<template>
  <button
    class="baseButton"
    :style="{ left: `${x}%`, top: `${y}%` }"
    @mouseenter="mouseenter"
    @click="click"
  >
    {{ loading ? "Умница!" : msg }}
  </button>
</template>

<style scoped>
.baseButton {
  display: block;
  border: none;
  background: #fff;
  border-radius: 8px;
  cursor: pointer;
  padding: 12px 16px;
  transition: all 0.3s ease-in;
  position: absolute;
}

.baseButton:hover {
  transform: scale(1.25);
}
</style>
