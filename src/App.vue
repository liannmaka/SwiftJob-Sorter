<template>
 <div>
  <div class="title">
    <Heart class="title-image"/>
    <Title title="Hyrule Jobs" class="header-title"/>
    </div>
    <div class="btn-wrapper">
    <Button text="Order by title" bgColor="#d5f0ff" color="#C20000" border="3px solid #1195c9" @click="handleOrder('title')"/>
    <Button text="Order by salary" bgColor="#d5f0ff" color="#C20000" border="3px solid #1195c9" @click="handleOrder('salary')"/>
    <Button text="Order by location" bgColor="#d5f0ff" color="#C20000" border="3px solid #1195c9" @click="handleOrder('location')"/>
    </div>
    <ListJob :jobList="jobs" :order="orderTerm"/>
 </div>
</template>

<script lang="ts">
import Title from "./components/Title.vue"
import Button from "./components/Button.vue"
import ListJob from "./components/JobList.vue"
import Heart from "./svg/HeartSvg.vue"
import { defineComponent, ref } from 'vue';
import { Job } from './composition/jobs';
import { orderTerm } from './composition/order';

export default defineComponent({
  name: 'App',
  components: {Title, Heart, Button, ListJob},
  setup(){
  const jobs = ref<Job[]>([
    {title: 'farm worker', location:"lon lon ranch", salary: 40000, id: 1},
    {title: 'quarryman', location:"death mountain", salary: 250000, id: 2},
    {title: 'flute player', location:"the lost woods", salary: 90000, id: 3},
    {title: 'fisherman', location:"lake hylia", salary: 80000, id: 4},
    {title: 'prison guard', location:"gerudo valley", salary: 70000, id: 5}
  ])

  const orderTerm = ref<orderTerm>("title")

  const handleOrder = (term: orderTerm) => {
  orderTerm.value = term
  }

  return{ jobs, handleOrder, orderTerm}
  }
});
</script>

<style scoped>
.title {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.title .title-image {
  width: 60px;
  height: 60px;
  margin-right: 20px;
}

.title .header-title {
  font-size: 3rem;
}

.btn-wrapper {
  text-align: center;
  margin-top: 20px;
}
</style> 


