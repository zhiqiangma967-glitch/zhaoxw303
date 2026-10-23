<script setup>
import { computed, ref } from 'vue'
import { menu } from '../data/menu.js'

const categories = [
  { id: 'all', label: '主厨推荐' },
  { id: 'main', label: '暖心主食' },
  { id: 'light', label: '轻食与甜点' },
]
const selectedCategory = ref('all')
const visibleDishes = computed(() => selectedCategory.value === 'all'
  ? menu.slice(0, 3)
  : menu.filter(dish => dish.cat === selectedCategory.value))
</script>

<template>
<section id="menu" class="menu-section"><div class="section-top"><div><div class="eyebrow">A LITTLE TASTE OF THE SEASON</div><h2>一餐一味，都是惦念</h2></div><p>把喜欢的味道，留给一起吃饭的人。</p></div><p class="menu-intro">忙碌了一天，总要留些时间，好好吃顿饭。我们把时蔬的清甜、热菜的香气和一点点甜蜜端上桌，等你和惦念的人坐下来。不必赶时间，喜欢的菜慢慢尝，想说的话慢慢聊。</p><div class="tabs" role="group" aria-label="菜品分类">
  <button v-for="category in categories" :key="category.id" type="button" :class="{ active: selectedCategory === category.id }" :aria-pressed="selectedCategory === category.id" @click="selectedCategory = category.id">{{ category.label }}</button>
</div>
<div class="dishes" id="dishes">
  <article v-for="dish in visibleDishes" :key="dish.name" class="dish">
    <div class="crop"><img loading="lazy" :src="`https://images.unsplash.com/${dish.img}?auto=format&fit=crop&w=800&q=80`" :alt="dish.name"></div>
    <h3>{{ dish.name }}<span>¥ {{ dish.price }}</span></h3>
    <p>{{ dish.desc }}</p>
    <p class="dish-note">{{ dish.note }}</p>
    <div class="tag">{{ dish.tag }}</div>
  </article>
</div>
</section>
</template>
