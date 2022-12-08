<template>
  <Nav/>

  <Header/>

  <main class="main">
    <TechSteps/>

    <StudyComforts/>

    <HowWorks/>

    <Support/>

    <Price/>

  </main>

  <Footer/>

</template>

<script>

import Nav from '@/components/Nav.vue';
import Header from '@/components/Header.vue';
import TechSteps from '@/components/TechSteps.vue';
import StudyComforts from '@/components/StudyComforts.vue';
import HowWorks from '@/components/HowWorks.vue';
import Support from '@/components/Support.vue';
import Price from '@/components/Price.vue';
import Footer from '@/components/Footer.vue';

export default {
  name: 'Home',
  components: {
    Nav,
    Header,
    TechSteps,
    StudyComforts,
    HowWorks,
    Support,
    Price,
    Footer
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