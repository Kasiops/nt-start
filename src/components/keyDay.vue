<template>
  <div>
<!--    <button @click="scrollRigth()">></button>-->
    <div class="blog-days-count" v-if="mind_quality">
      <div class="blog-days-count__success">Осознанных дней: {{ mind_quality.yes }}</div>
<!--      +15 Потому что с 19.01-02.02 забросил nailtoday -->
      <div class="blog-days-count__not-success">Неосознанных дней: {{ mind_quality.no }}</div>
    </div>
    <div class="blog-days">
      <article class="blog-days__item" :class="{'blog-days__item_not-mind' : item.mind === false}" v-for="(item, index) in article" v-bind:key="index">
        <div class="blog-days__img">
          <img :src="item.img" alt="" v-if="item.img">
          <img src="@/assets/nophoto.jpg" alt="" v-else>
        </div>
        <div class="blog-days__content">
          <div class="blog-days__date">{{ item.date }}</div>
          <div class="blog-days__title">{{ item.title }}</div>
          <div class="blog-days__text" v-html="item.text"></div>
        </div>
      </article>
      <div class="blog-days__add">
        <div class="blog-days__add-icon">+</div>
      </div>
      <div class="blog-days__add blog-days__add_all">
        Посмотреть все
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'keyDay',
  props: {},
  data () {
    return {
      article: [
        {
          date: '19.01.2020 - 02.02.2020',
          mind: false,
          title: 'Опять забросил NailToday',
          text: '' +
            '<p>...</p>'
        },
        {
          date: '18.01.2020 - Сб',
          mind: false,
          title: 'Работа над Nailtoday',
          text: '' +
            '<p>Поделал иконки для компонента viewed. Вечерком посидел, покурил калик с друзьями.</p>'
        },
        {
          date: '17.01.2020 - Пт',
          mind: false,
          title: 'Шепотка работы над Nailtoday',
          text: '' +
            '<p>Поделал немного дизайн компонента viewed.</p>'
        },
        {
          date: '16.01.2020 - Чт',
          mind: false,
          title: 'Ничего',
          text: '' +
            '<p>Высыпался ...</p>'
        },
        {
          date: '15.01.2020 - Ср',
          mind: false,
          title: 'Работа над NailToday',
          text: '' +
            '<p>Начал делать раздел "Просмотренное". Добавил прогресс-бар, статусы, типы, даты, историю, рейтинг</p>'
        },
        {
          date: '14.01.2020 - Вт',
          mind: true,
          title: 'Ничего',
          text: '' +
            '<p>...</p>'
        },
        {
          img: require('../assets/2.jpg'),
          mind: true,
          date: '16.09.2019 - Пн',
          title: 'Re:zero офигенен. Пилим NailToday',
          text: '<ul><li>Просмотрел Re:zero в обед</li><li>Стилизация и корректировки на NailToday</li></ul>'
        },
        {
          img: require('../assets/1.jpg'),
          mind: true,
          date: '15.09.2019 - вс',
          title: 'Весь день Re:zero. Перезапуск NailToday, опять?',
          text: '<ul><li>Просмотрел 8 серий подряд Re:zero</li><li>Прочитал 1 главу Брайна Трейси - Наука денег</li><li>Начал перезапуск NailToday</li></ul>'
        }
      ],
      mind_quality: {
        yes: 0,
        no: 0
      },
    }
  },
  methods: {
    countMind() {
      for (let i = 0; i < this.article.length; i++) {
        let item = this.article[i]
        if ( item.hasOwnProperty('mind') ) {
          if (item.mind) {
            this.mind_quality.yes++
          } else {
            this.mind_quality.no++
          }
        }
      }
    },
    scrollRigth () {
      let blog = document.querySelector('.blog-days')
      blog.scrollLeft += 1000
    },
    scroll () {
      document.onscroll = function(e){
        console.log(document.querySelector('.blog-days').scrollTop)
      }
    }
  },
  mounted () {
    this.scroll()
    this.countMind()
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
</style>
