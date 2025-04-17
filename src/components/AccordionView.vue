<template>
  <div class="accordion">
    <div
      class="accordion__item"
      v-for="item in items"
      :key="item.id"
      :class="{ 'accordion__item-active': activeItem === item.id }"
    >
      <div class="accordion__header" @click.prevent="toggleItem(item.id)">
        <span>{{ item.title }}</span>
        <span>{{ activeItem === item.id ? "-" : "+" }}</span>
      </div>
      <div v-if="activeItem === item.id">
        <div
          class="accordion__content"
          :class="{ 'accordion__content-open': activeItem === item.id }"
        >
          <span class="accordion__text">{{ item.content }}</span>
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
  padding: 20px;
  width: 600px;

  &__item {
    margin-bottom: 10px;
    // border: 1px solid rgb(37, 37, 204);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
    border-radius: 5px;
    overflow: hidden;

    &-active {
      border: 1px solid #007bff;
    }
  }

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 25px;
    padding: 10px;
    cursor: pointer;
    background-color: #f8f9fa;
    color: #333;

    &:hover {
      background-color: #e9ecef;
    }
  }

  &__content {
    max-height: 0;
    overflow: hidden;

    &-open {
      max-height: 500px;
    }
  }

  &__text {
    padding-bottom: 16px;
    margin: 10px;
    color: #555;
    line-height: 1.6;
  }
}
</style>
