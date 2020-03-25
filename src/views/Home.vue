<template>
  <div class="home">

    <!-- ================================
      ЛОГО
     ================================ -->

    <div class="container">
      <div class="logo"></div>
    </div>

    <!-- ================================
      ПРОСМОТРЕННОЕ
     ================================ -->

    <section class="section">
      <div class="container">
        <div class="section__title">
          Просмотренное
        </div>
        <div class="section__subtitle"></div>
        <div class="section__content">
          <viewed></viewed>
        </div>
      </div>
    </section>

    <!-- ================================
      ИТОГИ ЗА НЕДЕЛЮ
     ================================ -->

    <section class="section">
      <div class="container">
        <div class="section__title">
          Итоги за неделю
        </div>
        <div class="section__subtitle"></div>
        <div class="section__content">
          <totalResult></totalResult>
        </div>
      </div>
    </section>

    <!-- ================================
      ПОСЛЕДНИЕ НОВОСТИ
     ================================ -->

    <section class="section">
      <div class="container">
        <div class="section__title">
          Ключевое за день
        </div>
        <div class="section__subtitle"></div>
        <div class="section__content">
          <keyDay></keyDay>
        </div>
      </div>
    </section>

  </div>
</template>

<script>
// @ is an alias to /src
import progressBar from '@/components/progressBar.vue'
import viewed from '@/components/viewed.vue'
import keyDay from '@/components/keyDay.vue'
import totalResult from '@/components/totalResult.vue'

export default {
  name: 'home',
  components: {
    keyDay,
    totalResult,
    progressBar,
    viewed
  }
}
</script>
