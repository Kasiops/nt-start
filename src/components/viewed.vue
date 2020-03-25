<template>
  <div class="viewed">
    <div class="viewed__item" v-for="(item, index) in article" :key="index">
      <div class="viewed__poster">
        <div class="img-hover">
          <i class="fas fa-search"></i>
        </div>
        <img src="../assets/konosuba_poster.jpg" alt="">
      </div>
      <div class="viewed__content">
        <div class="viewed__main">
          <div class="viewed__title">
            {{ item.title }}
            <span class="color-success" v-if="item.status_code === 2">
            - Завершено
          </span>
            <span class="viewed__date" v-if="item.date">
            <template v-if="item.status_code === 2">
              Завершено:
            </template>
            <template v-else>
              Последнее обновление:
            </template>
            {{ item.date }}
          </span>
            <span class="viewed__type" v-if="item.type">
            ({{ item.type }})
          </span>
          </div>
          <div class="viewed__progress">
            <div class="progress-bar">
              <div class="progress-bar__percent" v-if="item.progress.count.text">
                {{ item.progress.count.text.sum }} / {{ item.progress.count.text.total }} {{
                unit[item.progress.unit].units_total }}
              </div>
              <div class="progress-bar__bar" v-if="item.progress.count.style">
                <div class="progress-bar__line progress-bar__line_color progress-bar_animated"
                     :class="{ 'progress-bar__line_color_done' : item.progress.count.text.sum === item.progress.count.text.total }"
                     :style="{width: item.progress.count.style.sum + '%'}"></div>
              </div>
            </div>
            <button @click="up(index)" v-if="item.status_code !== 2">
              + {{ item.progress.count.text.one }} {{ unit[item.progress.unit].default }} ({{ item.progress.count.style.one
              }}%)
            </button>
          </div>
        </div>
        <div class="viewed__additionally" v-if="item.history || item.rating">
          <div class="viewed-link">
            <div class="viewed-link__item" @click="showList('history', index)" v-if="item.history">
              <template v-if="activeList.key === 'history' && activeList.i === index">-</template>
              <template v-else>+</template>
              История
            </div>
            <div class="viewed-link__item" @click="showList('rating', index)" v-if="item.rating">
              <template v-if="activeList.key === 'rating' && activeList.i === index">-</template>
              <template v-else>+</template>
              Рейтинг
            </div>
          </div>
          <div class="viewed-list" v-if="activeList.i === index">
            <ul id="viewed-history" class="viewed-list__list"
                :class="{'viewed-list__list_active' : activeList.key === 'history'}" v-if="item.history">
              <li class="viewed-list__item" v-for="(element, i) in item.history" :key="i">
                Процент: {{ element.percent }}% <br>
                <template v-if="element.quantity">
                  Количество: {{ element.quantity }} {{ unit[item.progress.unit].units }} <br>
                </template>
                Дата: {{ element.date }}
              </li>
            </ul>
            <ul id="viewed-rating" class="viewed-list__list"
                :class="{'viewed-list__list_active' : activeList.key === 'rating'}" v-if="item.rating">
              <li class="viewed-list__item" v-if="item.rating.number">
                Оценка: {{ item.rating.number }}
              </li>
              <li class="viewed-list__item" v-if="item.rating.text">
                Почему такая оценка: <br> {{ item.rating.text }}
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="circle-status circle-status_icon circle-status_proccess" v-if="index === 0">
        <i class="fas fa-spinner spinner_animated"></i>
        <span class="circle-status__text">12</span>
      </div>
      <div class="circle-status circle-status_icon circle-status_bomb" v-else-if="index === 1">
        <i class="fas fa-skull-crossbones"></i>
        <span class="circle-status__text">12</span>
      </div>
      <div class="circle-status circle-status_icon circle-status_success" v-else>
        <i class="fas fa-check"></i>
        <span class="circle-status__text">{{ index }}</span>
      </div>

    </div>

  </div>

</template>

<script>
  export default {
    name: 'viewed',
    props: {},
    data () {
      return {
        progress: 9.091,
        unit: {
          anime: {
            default: 'серия',
            units: 'серии',
            units_total: 'серий'
          },
          film: {
            default: 'фильм',
            units: 'фильмы',
            units_total: 'фильма'
          },
          empty: {
            default: '',
            units: '',
            units_total: ''
          }
        },
        article: [
          {
            status_code: 1,
            date: '16.01.20',
            title: 'Этот замечательный мир! / Konosuba (2 сезон)',
            type: 'Аниме',
            progress: {
              unit: 'anime',
              count: {
                style: {
                  total: 100,
                  one: 9.091,
                  sum: 18.182
                },
                text: {
                  total: 11,
                  one: 1,
                  sum: 2
                }
              },
            },
            history: [
              {
                percent: 9.091,
                quantity: 1,
                date: '15.01.20'
              },
              {
                percent: 18.182,
                quantity: 1,
                date: '16.01.20'
              },
            ]
          },
          {
            status_code: 2,
            date: '15.01.20',
            title: 'Этот замечательный мир! / Konosuba (1 сезон)',
            type: 'Аниме',
            progress: {
              unit: 'anime',
              count: {
                style: {
                  total: 100,
                  one: 9.091,
                  sum: 100.001
                },
                text: {
                  total: 11,
                  one: 1,
                  sum: 11
                }
              },
            },
            history: [
              {
                percent: 25,
                date: '13.01.20'
              },
              {
                percent: 60,
                date: '14.01.20'
              },
              {
                percent: 100,
                date: '15.01.20'
              }
            ],
            rating: {
              number: '2 из 5',
              text: 'Пересматриваю в третий раз. Видимо не прошло достаточно времени. Как-будто пожевал жеванную жевачку. Местами было смешно, но а так все серии помнил.'
            }
          },
          {
            status_code: 2,
            date: '13.01.20',
            title: 'Этот замечательный мир! / Konosuba',
            type: 'Фильм',
            progress: {
              unit: 'empty',
              count: {
                style: {
                  total: 100,
                  one: 100,
                  sum: 100
                },
                text: {
                  total: 1,
                  one: 1,
                  sum: 1
                }
              },
            },
            history: [
              {
                percent: 100,
                date: '13.01.20'
              }
            ],
            rating: {
              number: '4 из 5',
              text: 'Могу сказать одно, зашло!',
            }
          }
        ],
        activeList: { key: null, i: null }
      }
    },
    methods: {
      showList (key, i) {
        if (this.activeList.key === key && this.activeList.i === i) {
          this.activeList = { key: null, i: null }
        } else {
          this.activeList = { key, i }
        }
      },
      up (i) {
        let item = this.article[i]
        let count = item.progress.count

        for (let key in count) {
          if (count[key].sum < count[key].total) {
            count[key].sum += count[key].one
          }
        }
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
</style>
