<template>
  <Nav/>

  <Header @modalOpen="modalOpen1"/>

  <Transition name="modal-fade">
    <div class="test__modal" v-if="modalVisible" @click.self="modalVisible = false">
      <div class="test__modal-content">

        <button class="close-btn" @click="modalVisible = false"><i class="fal fa-times"></i></button>

        <div class="content-1" v-if="content1Opened">
          <p class="content-1-title">{{ modalContents.content1.title }}</p>
          <p class="content-1-text">{{ modalContents.content1.text }}</p>

          <button class="content-1-btn orange-btn" @click="content1Opened = false, content2Opened = true" v-html="modalContents.content1.btnText">
          </button>
        </div>

        <div class="content-2" v-if="content2Opened">
          <p class="test-num-text">ЗАДАНИЕ №{{ modalContents.content2.testNum }}</p>

          <p class="content-2-text">{{ modalContents.content2.text }}</p>

          <div class="test-options-list">

            <span class="test-option" v-for="(option, idx) in modalContents.content2.options" :key="idx">
              <input type="radio" class="test-option-inp" name="test-option" :id="`option-${idx + 1}`">
              <label :for="`option-${idx + 1}`" class="test-option-name">{{ option.text }}</label>
            </span>

          </div>

          <button class="content-2-btn orange-btn" @click="content2Opened = false, content3Opened = true" v-html="modalContents.content2.btnText">
          </button>
        </div>

        <div class="content-3" v-if="content3Opened">
          <p class="test-num-text">ЗАДАНИЕ №{{ modalContents.content2.testNum }}</p>
          <p class="content-3-title">{{ modalContents.content3.title }}</p>

          <p class="content-3-text">{{ modalContents.content3.text }}</p>

          <button class="content-3-btn orange-btn" @click="content3Opened = false, content4Opened = true" v-html="modalContents.content3.btnText"></button>
        </div>

        <div class="content-4" v-if="content4Opened">
          <div class="content-4-points">
            <span class="point-icon"><i class="fas fa-thumbs-up"></i></span>

            <p class="points-num">Набрано {{ modalContents.content4.totalNum }}/4</p>
          </div>

          <p class="content-4-text">{{ modalContents.content4.text }}</p>

          <button class="start-study-btn orange-btn" @click="modalVisible = false" v-html="modalContents.content4.btnText"></button>
        </div>

      </div>
    </div>
  </Transition>

  <main class="main">

    <TechSteps/>

    <StudyComforts/>

    <HowWorks @modalOpen="modalOpen2"/>

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
  },
  data() {
    return {
      modalVisible: false,
      content1Opened: true,
      content2Opened: false,
      content3Opened: false, 
      content4Opened: false, 
      modalContents: {
        content1: {
          title: 'Перед тем, как приступить к обучению, необходимо пройти небольшой тест',
          text: 'Тест состоит из 4 заданий на логическое мышление и прочие навыки, необходимые программисту. Задания не самые простые. Но ни в коем случае не выбирайте ответы наугад. Если вы не можете дать правильный ответ – выбирайте пункт «Не знаю».',
          btnText: 'Начать тест <i class="fal fa-external-link" data-v-61dd7a3d=""></i>'
        },
        content2: {
          testNum: 1,
          text: 'Иван Иванович купил в магазине у дома несколько пачек макарон по 40 рублей, несколько пачек печенья по 32 рубля и 2 пакета сока. Продавщица сказала, что с него 525 рублей (скидка не предусмотрена). Иван Иванович заявил, что его пытаются обсчитать. Действительно ли продавщица ошиблась в подсчетах?',
          options: [
            {
              text: 'Да, сумма явно неверная'
            },
            {
              text: 'Нет, такая сумма вполне могла получиться'
            },
            {
              text: 'Не знаю, не получается решить'
            }
          ],
          btnText: 'Ответить <i class="fal fa-long-arrow-right"></i>'
        },
        content3: {
          title: 'Правильно! С логикой у вас все отлично',
          text: 'Так как 1 пачка макарон стоит 40 рублей, то любое количество пачек будет стоить четное число рублей. Аналогично с печеньем. А так как пакетов сока ровно 2, то за сок тоже нужно будет отдать четное число рублей. Получается, что ни при каких условиях в результате не может получиться нечетное число 525, а значит, продавщица действительно пыталась обсчитать Ивана Ивановича. В этом задании проверялось ваше логическое мышление. Это критически важный навык для любого программиста.',
          btnText: 'Далее <i class="fal fa-long-arrow-right"></i>'
        },
        content4: {
          totalNum: 4,
          text: 'Это великолепный результат! У вас есть все шансы стать отличным программистом. Начните обучение прямо сейчас, доступ ко вводным урокам уже открыт',
          btnText: 'Начать <i class="fal fa-long-arrow-right"></i>'
        }
      }
    }
  },
  methods: {
    modalOpen1() {
      this.modalVisible = !this.modalVisible
    },
    modalOpen2() {
      this.modalVisible = !this.modalVisible
    }
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

.test__modal {
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  background: rgba($color: #191A26, $alpha: .9);
  z-index: 9099;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;

  &-content {
    max-width: 740px;
    width: 100%;
    background: var(--main-white);
    border-radius: 30px;
    overflow: auto;
    max-height: 450px;
    padding: 25px 30px;
    display: flex;
    flex-direction: column;
    row-gap: 3px;

    .close-btn {
      color: var(--copyright-gray);
      background: transparent;
      border: 0;
      font-size: 25px;
      width: 25px;
      height: 25px;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-left: auto;
    }

    .content-1 {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      row-gap: 20px;

      p {
        max-width: 515px;
      }

      &-title {
        font-size: calc(16px + 8 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 600;
      }

      &-text {
        font-size: calc(13px + 2 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 500;
      }
    }

    .content-2 {
      width: 100%;
      display: flex;
      flex-direction: column;
      row-gap: 20px;

      &-text {
        font-size: calc(13px + 2 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 500;
      }

      .test-options-list {
        display: flex;
        flex-direction: column;
        row-gap: 15px;

        .test-option {
          display: flex;
          align-items: center;

          &-name {
            font-size: calc(13px + 2 * (100vw / 1920));
            font-weight: 600;
            color: var(--main-blue);
            padding-left: 10px;
          }

          input, label {
            cursor: pointer;
          }

          input[type="radio"] {
            appearance: none;
            background-color: #EAEAEA;
            margin: 0;
            width: 20px;
            height: 20px;
            border: solid 4px #EAEAEA;
            border-radius: 4px;
            transition: .4s;

            &:checked {
              background: var(--main-orange);
            }
          }
        }
      }

      &-btn {
        margin-left: auto;
      }
    }

    .content-3 {
      width: 100%;
      display: flex;
      flex-direction: column;
      row-gap: 20px;

      &-title {
        font-size: calc(16px + 8 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 600;
      }

      &-text {
        font-size: calc(13px + 2 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 500;
      }

      &-btn {
        margin-left: auto;
      }
    }

    .content-4 {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      row-gap: 20px;

      &-points {
        max-width: max-content;
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
        padding: 15px 25px;
        background: #EAEAEA;
        border-radius: 39px;
        row-gap: 2px;

        .point-icon {
          color: var(--main-orange);
          font-size: 20px;
        }

        .points-num {
          font-size: calc(13px + 2 * (100vw / 1920));
          color: var(--main-blue);
          font-weight: 500;
          text-transform: uppercase;
        }
      }

      &-text {
        max-width: 500px;
        width: 100%;
        font-size: calc(15px + 2 * (100vw / 1920));
        color: var(--main-blue);
        font-weight: 600;
      }
      
    }

  }
}

.test-num-text {
  max-width: max-content;
  width: 100%;
  padding: 8px 20px;
  background: #EAEAEA;
  border-radius: 50px;
  font-size: 15px;
  color: var(--main-blue);
  font-weight: 500;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity .5s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

@media (min-width: 1920px) {
  .content-1,
  .content-2,
  .content-3 {
    &-title {
      font-size: 24px !important;
    }

    &-text {
      font-size: 15px !important;
    }
  }

  .content-4 {
    &-text {
      font-size: 17px !important;
    }

    .points-num {
      font-size: 15px !important; 
    }
  }
}

</style>