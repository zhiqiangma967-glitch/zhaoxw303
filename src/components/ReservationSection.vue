<script setup>
import { reactive, ref } from 'vue'

function localDate() {
  const now = new Date()
  return new Date(now.getTime() - now.getTimezoneOffset() * 60000).toISOString().slice(0, 10)
}
const minDate = ref(localDate())
const reservation = reactive({ date: minDate.value, guests: '2 位', time: '18:00', name: '' })
const feedback = ref('')
function refreshMinDate() { minDate.value = localDate() }
function submitReservation() {
  refreshMinDate()
  if (reservation.date < minDate.value) {
    feedback.value = '请选择今天或之后的用餐日期。'
    return
  }
  feedback.value = '已完成预订意向填写。此为演示页面，尚未向餐厅发送，亦未生成真实订位。'
}
</script>

<template>
<section class="visit" id="visit"><div><div class="eyebrow">SAVE A SEAT AT OUR TABLE</div><h2>为下一次相聚，留一席。</h2><p>午餐 11:30–14:30 · 晚餐 17:30–21:30<br>选择喜欢的日子，和喜欢的人一起赴约。</p><p class="fine">此页面为餐厅设计示例，菜品及价格为演示内容。<br>地址及联系方式待餐厅补充，表单暂不接收真实预订。</p></div><form id="reservation" @submit.prevent="submitReservation"><label>用餐日期<input v-model="reservation.date" type="date" id="date" :min="minDate" required @focus="refreshMinDate"></label><label>用餐人数<select v-model="reservation.guests" required><option>2 位</option><option>1 位</option><option>3 位</option><option>4 位</option><option>5–6 位</option></select></label><label>到店时间<select v-model="reservation.time" required><option>11:30</option><option>12:30</option><option>13:30</option><option>18:00</option><option>19:00</option><option>20:00</option></select></label><label>您的称呼<input v-model="reservation.name" required placeholder="请输入称呼" maxlength="30" autocomplete="name"></label><button type="submit">填写预订意向 <span class="arrow">↗</span></button><p id="feedback" role="status" aria-live="polite">{{ feedback }}</p></form></section>
</template>
