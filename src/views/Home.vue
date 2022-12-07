<template>
  <Nav/>

  <Header/>

  <main class="main">

    <TechSteps/>

    <StudyComforts/>

    <HowWorks/>
  </main>

</template>

<script>
import Nav from '@/components/Nav.vue';
import Header from '@/components/Header.vue';
import TechSteps from '@/components/TechSteps.vue';
import StudyComforts from '@/components/StudyComforts.vue';
import HowWorks from '@/components/HowWorks.vue';

export default {
  name: 'Home',
  components: {
    Nav,
    Header,
    TechSteps,
    StudyComforts,
    HowWorks
  }
}

</script>

<style lang="scss" scoped>

.main {
  width: 100%;
  display: flex;
  flex-direction: column;
  padding-top: 50px;
}

</style>