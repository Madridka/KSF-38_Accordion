<template>
  <div class="accordion">
    <div
      class="accordion__item"
      v-for="item in items"
      :key="item.id"
      :class="{ 'accordion__item-active': activeItem === item.id }"
    >
      <div class="accordion-header" @click.prevent="toggleItem(item.id)">
        <span>{{ item.title }}</span>
        <span>{{ activeItem === item.id ? "-" : "+" }}</span>
      </div>
      <div v-if="activeItem === item.id">
        <div
          class="accordion-content"
          :class="{ 'accordion__item-active': activeItem === item.id }"
        >
          {{ item.content }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const items = ref([
  {
    id: 1,
    title: "Секция 1",
    content:
      "Содержимое первой секции. Здесь может быть любой текст или элементы.",
  },
  {
    id: 2,
    title: "Секция 2",
    content: "Содержимое второй секции. Это пример текста для демонстрации.",
  },
  {
    id: 3,
    title: "Секция 3",
    content:
      "Содержимое третьей секции. Аккордеон поддерживает динамическое раскрытие.",
  },
]);

const activeItem = ref(null);

const toggleItem = (id) => {
  if (activeItem.value === id) {
    activeItem.value = null;
  } else {
    activeItem.value = id;
  }
};
</script>


<style lang="scss" scoped>
.accordion {
  margin: 20px auto;
  width: 800px;
  background-color: bisque;

  &__item {
    margin: 10px;
    padding: 5px;
    height: 30px;
    border: 2px solid ghostwhite;

    &-active {
      border-color: blue;
    }
  }
}
</style>
