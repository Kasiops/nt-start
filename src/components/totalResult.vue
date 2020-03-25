<template>
  <div>
    <div class="blog-week">
      <article class="blog-week__item">
        <div class="blog-week__col" style="display: flex;">
          <div class="blog-week__col">
            <div class="radial">
              <div class="circle left rotate"><span :style="{transform: `rotate(${rotate.left}deg)`}"></span></div>
              <div class="circle right rotate"><span :style="{transform: `rotate(${rotate.rigth}deg)`}"></span></div>

              <div class="loop">75%</div>
            </div>
          </div>
          <div class="blog-week__col">
            <div class="blog-week__percent">
              75% сентября завершено
            </div>
            <div class="blog-week__num">
              3/4 недель сентября
            </div>
          </div>
        </div>
        <div class="blog-week__col">
          <div class="blog-week__list">
            <div class="blog-week__title">Что было сделано за 3ю неделю:</div>
            <ul>
              <li>Запущен NailToday</li>
              <li>Прочитал около полторы главы Брайна Трейси - Наука денег</li>
            </ul>
          </div>
        </div>
        <div class="blog-week__col">
          Выводы за неделю (Кейсы)
          <p>Прочитал историю 19 парня,
            который уехал в США по учебной программе прошел акселератор и открыл стартап в США.
            Достаточно интересная история.</p>
        </div>
        <div class="blog-week__col">
          Оценка недели
          <p>0.5/5 Полный пиздец</p>
          <p>Если следующая неделя будет с оценкой ниже 3, то штраф 2500 руб</p>
        </div>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  name: 'keyDay',
  props: {},
  data () {
    return {
      rotate: {left: 180, rigth: 90}
    }
  },
  methods: {
  },
  mounted () {
  }
}
</script>

<style scoped lang="sass">
</style>
