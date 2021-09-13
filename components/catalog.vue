<template>
  <div class="grid">
    <div class="grid-col_1-8 mobile_none top-tab">
      <ul class="live-tabs">
        <li
          @click="tabIndex = 0; cityValue = null; searchInput = ''; classValue = null;"

          :class="{
            active: tabIndex === 0,
          }"
        >
          <svg
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M15 8V16H5V8H15ZM16 6H4C3.45 6 3 6.45 3 7V17C3 17.55 3.45 18 4 18H16C16.55 18 17 17.55 17 17V13.5L21 17.5V6.5L17 10.5V7C17 6.45 16.55 6 16 6Z"
              fill="#004B94"
            />
          </svg>
          Онлайн трансляция
        </li>
        <li
          @click="tabIndex = 1; cityValue = null; searchInput = ''; classValue = null;"

          :class="{
            active: tabIndex === 1,
          }"
        >
          <svg
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M12 7C6.48 7 2 9.24 2 12C2 14.24 4.94 16.13 9 16.77V20L13 16L9 12V14.73C5.85 14.17 4 12.83 4 12C4 10.94 7.04 9 12 9C16.96 9 20 10.94 20 12C20 12.73 18.54 13.89 16 14.53V16.58C19.53 15.81 22 14.05 22 12C22 9.24 17.52 7 12 7Z"
              fill="#004B94"
            />
          </svg>
          360° панорама
        </li>
        <li
          @click="tabIndex = 2; cityValue = null; searchInput = ''; classValue = null;"

          :class="{
            active: tabIndex === 2,
          }"
        >
          <svg
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M7.52005 21.48C4.25005 19.94 1.91005 16.76 1.55005 13H0.0500488C0.560049 19.16 5.71005 24 12 24L12.66 23.97L8.85005 20.16L7.52005 21.48ZM8.41005 14.96C8.22005 14.96 8.04005 14.93 7.89005 14.88C7.73005 14.82 7.60005 14.75 7.49005 14.64C7.38005 14.54 7.29005 14.42 7.23005 14.27C7.17005 14.13 7.14005 13.97 7.14005 13.8H5.84005C5.84005 14.16 5.91005 14.48 6.05005 14.75C6.19005 15.02 6.38005 15.25 6.61005 15.44C6.85005 15.62 7.12005 15.76 7.43005 15.85C7.73005 15.95 8.05005 16 8.39005 16C8.76005 16 9.11005 15.95 9.42005 15.85C9.74005 15.75 10.02 15.6 10.25 15.41C10.48 15.22 10.67 14.98 10.8 14.69C10.93 14.4 11 14.08 11 13.72C11 13.53 10.98 13.34 10.93 13.16C10.88 12.98 10.81 12.81 10.7 12.65C10.6 12.49 10.46 12.35 10.3 12.22C10.13 12.09 9.93005 11.99 9.69005 11.91C9.89005 11.82 10.06 11.71 10.21 11.58C10.36 11.45 10.48 11.31 10.58 11.16C10.68 11.01 10.75 10.86 10.8 10.7C10.85 10.54 10.87 10.38 10.87 10.22C10.87 9.86 10.81 9.54 10.69 9.26C10.57 8.98 10.4 8.75 10.18 8.57C9.98005 8.38 9.71005 8.24 9.41005 8.14C9.10005 8.05 8.76005 8 8.39005 8C8.03005 8 7.70005 8.05 7.39005 8.16C7.09005 8.27 6.82005 8.42 6.60005 8.61C6.39005 8.8 6.22005 9.02 6.09005 9.28C5.97005 9.54 5.91005 9.82 5.91005 10.13H7.21005C7.21005 9.96 7.24005 9.81 7.30005 9.68C7.36005 9.55 7.44005 9.43 7.55005 9.34C7.66005 9.25 7.78005 9.17 7.93005 9.12C8.08005 9.07 8.23005 9.04 8.41005 9.04C8.81005 9.04 9.11005 9.14 9.30005 9.35C9.49005 9.55 9.59005 9.84 9.59005 10.21C9.59005 10.39 9.56005 10.55 9.51005 10.7C9.46005 10.85 9.37005 10.97 9.26005 11.07C9.15005 11.17 9.01005 11.25 8.85005 11.31C8.69005 11.37 8.49005 11.4 8.27005 11.4H7.50005V12.43H8.27005C8.49005 12.43 8.69005 12.45 8.87005 12.5C9.05005 12.55 9.20005 12.63 9.32005 12.73C9.44005 12.84 9.54005 12.97 9.61005 13.13C9.68005 13.29 9.71005 13.48 9.71005 13.7C9.71005 14.11 9.59005 14.42 9.36005 14.63C9.13005 14.86 8.81005 14.96 8.41005 14.96ZM16.96 9.04C16.64 8.71 16.26 8.45 15.82 8.27C15.39 8.09 14.9 8 14.36 8H12V16H14.3C14.85 16 15.36 15.91 15.81 15.73C16.26 15.55 16.65 15.3 16.97 14.97C17.29 14.64 17.54 14.24 17.71 13.78C17.88 13.31 17.97 12.79 17.97 12.21V11.81C17.97 11.23 17.88 10.71 17.71 10.24C17.53 9.77 17.28 9.37 16.96 9.04ZM16.57 12.2C16.57 12.62 16.52 12.99 16.43 13.33C16.33 13.66 16.19 13.95 16 14.18C15.81 14.41 15.57 14.59 15.29 14.71C15 14.83 14.67 14.89 14.3 14.89H13.39V9.12H14.36C15.08 9.12 15.63 9.35 16 9.81C16.38 10.27 16.57 10.93 16.57 11.8V12.2ZM12 0L11.34 0.03L15.15 3.84L16.48 2.51C19.75 4.06 22.09 7.23 22.44 10.99H23.94C23.44 4.84 18.29 0 12 0Z"
              fill="#004B94"
            />
          </svg>
          Виртуальный шоурум
        </li>
      </ul>
    </div>
    <div class="grid-col_1-8 title-box">
      <div v-if="tabIndex === 0">
        <h2 class="title">Онлайн трансляция</h2>
      </div>
      <div v-if="tabIndex === 1">
        <h2 class="title">360° панорама</h2>
      </div>
      <div v-if="tabIndex === 2">
        <h2 class="title">Виртуальный шоурум</h2>
      </div>
    </div>

    <div class="grid-col_1-11">
      <div class="desktop_none">
        <ul class="live-tabs">
          <li
            @click="tabIndex = 0; cityValue = null; searchInput = ''; classValue = null;"
            :class="{
              active: tabIndex === 0,
            }"
          >
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M15 8V16H5V8H15ZM16 6H4C3.45 6 3 6.45 3 7V17C3 17.55 3.45 18 4 18H16C16.55 18 17 17.55 17 17V13.5L21 17.5V6.5L17 10.5V7C17 6.45 16.55 6 16 6Z"
                fill="#004B94"
              />
            </svg>
            Онлайн трансляция
          </li>
          <li
            @click="tabIndex = 1; cityValue = null; searchInput = ''; classValue = null;"

            :class="{
              active: tabIndex === 1,
            }"
          >
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M12 7C6.48 7 2 9.24 2 12C2 14.24 4.94 16.13 9 16.77V20L13 16L9 12V14.73C5.85 14.17 4 12.83 4 12C4 10.94 7.04 9 12 9C16.96 9 20 10.94 20 12C20 12.73 18.54 13.89 16 14.53V16.58C19.53 15.81 22 14.05 22 12C22 9.24 17.52 7 12 7Z"
                fill="#004B94"
              />
            </svg>
            360° панорама
          </li>
          <li
            @click="tabIndex = 2; cityValue = null; searchInput = ''; classValue = null;"

            :class="{
              active: tabIndex === 2,
            }"
          >
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M7.52005 21.48C4.25005 19.94 1.91005 16.76 1.55005 13H0.0500488C0.560049 19.16 5.71005 24 12 24L12.66 23.97L8.85005 20.16L7.52005 21.48ZM8.41005 14.96C8.22005 14.96 8.04005 14.93 7.89005 14.88C7.73005 14.82 7.60005 14.75 7.49005 14.64C7.38005 14.54 7.29005 14.42 7.23005 14.27C7.17005 14.13 7.14005 13.97 7.14005 13.8H5.84005C5.84005 14.16 5.91005 14.48 6.05005 14.75C6.19005 15.02 6.38005 15.25 6.61005 15.44C6.85005 15.62 7.12005 15.76 7.43005 15.85C7.73005 15.95 8.05005 16 8.39005 16C8.76005 16 9.11005 15.95 9.42005 15.85C9.74005 15.75 10.02 15.6 10.25 15.41C10.48 15.22 10.67 14.98 10.8 14.69C10.93 14.4 11 14.08 11 13.72C11 13.53 10.98 13.34 10.93 13.16C10.88 12.98 10.81 12.81 10.7 12.65C10.6 12.49 10.46 12.35 10.3 12.22C10.13 12.09 9.93005 11.99 9.69005 11.91C9.89005 11.82 10.06 11.71 10.21 11.58C10.36 11.45 10.48 11.31 10.58 11.16C10.68 11.01 10.75 10.86 10.8 10.7C10.85 10.54 10.87 10.38 10.87 10.22C10.87 9.86 10.81 9.54 10.69 9.26C10.57 8.98 10.4 8.75 10.18 8.57C9.98005 8.38 9.71005 8.24 9.41005 8.14C9.10005 8.05 8.76005 8 8.39005 8C8.03005 8 7.70005 8.05 7.39005 8.16C7.09005 8.27 6.82005 8.42 6.60005 8.61C6.39005 8.8 6.22005 9.02 6.09005 9.28C5.97005 9.54 5.91005 9.82 5.91005 10.13H7.21005C7.21005 9.96 7.24005 9.81 7.30005 9.68C7.36005 9.55 7.44005 9.43 7.55005 9.34C7.66005 9.25 7.78005 9.17 7.93005 9.12C8.08005 9.07 8.23005 9.04 8.41005 9.04C8.81005 9.04 9.11005 9.14 9.30005 9.35C9.49005 9.55 9.59005 9.84 9.59005 10.21C9.59005 10.39 9.56005 10.55 9.51005 10.7C9.46005 10.85 9.37005 10.97 9.26005 11.07C9.15005 11.17 9.01005 11.25 8.85005 11.31C8.69005 11.37 8.49005 11.4 8.27005 11.4H7.50005V12.43H8.27005C8.49005 12.43 8.69005 12.45 8.87005 12.5C9.05005 12.55 9.20005 12.63 9.32005 12.73C9.44005 12.84 9.54005 12.97 9.61005 13.13C9.68005 13.29 9.71005 13.48 9.71005 13.7C9.71005 14.11 9.59005 14.42 9.36005 14.63C9.13005 14.86 8.81005 14.96 8.41005 14.96ZM16.96 9.04C16.64 8.71 16.26 8.45 15.82 8.27C15.39 8.09 14.9 8 14.36 8H12V16H14.3C14.85 16 15.36 15.91 15.81 15.73C16.26 15.55 16.65 15.3 16.97 14.97C17.29 14.64 17.54 14.24 17.71 13.78C17.88 13.31 17.97 12.79 17.97 12.21V11.81C17.97 11.23 17.88 10.71 17.71 10.24C17.53 9.77 17.28 9.37 16.96 9.04ZM16.57 12.2C16.57 12.62 16.52 12.99 16.43 13.33C16.33 13.66 16.19 13.95 16 14.18C15.81 14.41 15.57 14.59 15.29 14.71C15 14.83 14.67 14.89 14.3 14.89H13.39V9.12H14.36C15.08 9.12 15.63 9.35 16 9.81C16.38 10.27 16.57 10.93 16.57 11.8V12.2ZM12 0L11.34 0.03L15.15 3.84L16.48 2.51C19.75 4.06 22.09 7.23 22.44 10.99H23.94C23.44 4.84 18.29 0 12 0Z"
                fill="#004B94"
              />
            </svg>
            Виртуальный шоурум
          </li>
        </ul>
      </div>
      <div class="filter-box">
        <div @click="selectsCity = !selectsCity" class="filter-field">
          <p class="indent_bottom-h5">Город</p>
          <div
            class="filter-select"
            :class="{ active: selectsCity }"
            style="display: flex;align-items: center;justify-content: space-between;padding: 12px 16px;"
          >
            <span>{{ cityValue || 'Все города' }}</span>
            <svg
              width="16"
              height="16"
              viewBox="0 0 16 16"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M4.00002 5.80005L8.00002 9.80005L12 5.80005L13.6 6.60005L8.00002 12.2L2.40002 6.60005L4.00002 5.80005Z"
                fill="black"
              />
            </svg>
            <ul v-if="selectsCity">
              <li @click="cityValue = null">Все</li>
              <li v-for="item in cities" :key="item" @click="cityValue = item; searchInput = ''; classValue = null">
                {{ item }}
              </li>
            </ul>
          </div>
        </div>
        <div class="filter-field">
          <p class="indent_bottom-h5">Жилой комплекс</p>
          <div class="filter-select" :class="{ active: selectsClass }">
            <div
              class="flex flex_justify-between"
              @click="selectsClass = !selectsClass"
            >
              <span>{{ classValue || 'Все' }}</span>
              <svg
                width="16"
                height="16"
                viewBox="0 0 16 16"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M4.00002 5.80005L8.00002 9.80005L12 5.80005L13.6 6.60005L8.00002 12.2L2.40002 6.60005L4.00002 5.80005Z"
                  fill="black"
                />
              </svg>
            </div>

            <ul v-if="selectsClass">
              <input v-model="searchInput" type="text" />
              <li
                @click="
                  classValue = null
                  searchInput = ''
                  selectsClass = false
                "
              >
                Все
              </li>
              <li
                v-for="item in searchClasses"
                :key="item"
                @click="
                  classValue = null
                  searchInput = ''
                  selectsClass = false
                  classValue = item
                "
              >
                {{ item }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="grid-col_1-11">
      <div class="build-card-box">
        <div
          v-for="item in filters.slice(0, this.limit)"
          :key="item.id"
          class="build-card"
        >
          <nuxt-link class="card-link" :to="`/builds/${item.id}#${tabIndex}`">
            <div class="card-link-box">
              <div class="image-box">
                <img
                  class="build-card-image"
                  :src="`${baseUrl}/get-image/${item.image}`"
                  alt=""
                />
                <div v-if="tabIndex === 0" class="link-bg">
                  <img src="~/assets/image/icons/camera.svg" alt="" />
                  <p>Cмотреть онлайн-трансляцию</p>
                </div>
                <div v-if="tabIndex === 1" class="link-bg">
                  <img src="~/assets/image/icons/360.svg" alt="" />
                  <p>Cмотреть 360° панораму</p>
                </div>
                <div v-if="tabIndex === 2" class="link-bg">
                  <img src="~/assets/image/icons/3d.svg" alt="" />
                  <p>Cмотреть Виртуальный шоурум</p>
                </div>
              </div>
            </div>
          </nuxt-link>
          <div class="">
            <a :href="item.link" target="_blank"
              ><p class="card-name">{{ item.name }}</p></a
            >
            <p class="card-city secondary-text">
              <span
                ><svg
                  width="8"
                  height="9"
                  viewBox="0 0 8 9"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <circle cx="4" cy="4.5" r="4" fill="#F2994A" />
                </svg>
              </span>
              {{ item.city }}
            </p>
          </div>
        </div>
      </div>
    </div>
    <div v-if="!filters.length" class="grid-col_1-11 no-content">
      <p>Нет данных</p>
    </div>
    <div
      v-if="filters.length > limit"
      @click="limit = limit + 6"
      class="grid-col_1-11 view-more"
    >
      <p>Показать еще</p>
    </div>
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'

export default {
  name: 'catalog',
  data: () => ({
    tabIndex: 0,
    selectsCity: false,
    selectsClass: false,
    cityValue: null,
    classValue: null,
    builds: [],
    searchInput: '',
    limit: 6,
  }),
  computed: {
    classes() {
      return [...new Set(this.searchFilter.map((item) => item.name))]
    },
    searchClasses() {
      return this.classes.filter((item) =>
        new RegExp(this.searchInput, 'i').test(item)
      )
    },
    cities() {
      return [...new Set(this.builds.map((item) => item.city))]
    },

    sortBuilds() {
      return [
        ...this.sortByClass(
          this.builds.filter((item) => item.city === 'Нур-Султан')
        ),
        ...this.sortByClass(
          this.builds.filter((item) => item.city === 'Алматы')
        ),
        ...this.sortByClass(
          this.builds.filter((item) => item.city === 'Шымкент')
        ),
        ...this.sortByClass(
          this.builds.filter((item) => item.city === 'Атырау')
        ),
        ...this.sortByClass(
          this.builds.filter((item) => item.city === 'Актау')
        ),
      ]
    },
    searchFilter(){
      if (this.tabIndex === 0) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            JSON.parse(item.translation).length &&
            item.active
        )
      }
      if (this.tabIndex === 1) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            item.around &&
            item.active
        )
      }
      if (this.tabIndex === 2) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            JSON.parse(item['3d']).length &&
            item.active
        )
      }
      return this.sortBuilds.filter(
        (item) =>
          (this.cityValue ? item.city === this.cityValue : true) &&
          item.active
      )
    },
    filters() {
      if (this.tabIndex === 0) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            (this.classValue ? item.name === this.classValue : true) &&
            JSON.parse(item.translation).length &&
            item.active
        )
      }
      if (this.tabIndex === 1) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            (this.classValue ? item.name === this.classValue : true) &&
            item.around &&
            item.active
        )
      }
      if (this.tabIndex === 2) {
        return this.sortBuilds.filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            (this.classValue ? item.name === this.classValue : true) &&
            JSON.parse(item['3d']).length &&
            item.active
        )
      }
      return this.sortBuilds.filter(
        (item) =>
          (this.cityValue ? item.city === this.cityValue : true) &&
          (this.classValue ? item.name === this.classValue : true) &&
          item.active
      )
    },
    baseUrl() {
      return baseUrl
    },
  },
  methods: {
    sortByClass(arr) {
      return arr
      // return [
      //   ...arr.filter((item) => item.class === 'Стандарт'),
      //   ...arr.filter((item) => item.class === 'Комфорт'),
      //   ...arr.filter((item) => item.class === 'Бизнес'),
      //   ...arr.filter((item) => item.class === 'Премиум'),
      // ]
    },
  },
  created() {
    this.$axios.get(baseUrl).then((res) => {
      this.builds = res.data
    })
  },
}
</script>

<style lang="scss" scoped>
.top-tab {
  margin-top: 32px;
}
.live-tabs {
  display: flex;
  align-items: center;
  border-radius: 10px;
  list-style: none;
  margin-top: 24px;
  li {
    transition: 0.2s;
    display: flex;
    align-items: center;
    background: #f2f9ff;
    height: 48px;
    padding: 0 20px;
    font-size: 16px;
    color: #004b94;
    font-style: normal;
    font-weight: 500;
    svg {
      margin-right: 10px;
    }
    &:hover {
      cursor: pointer;
    }
    &.active {
      color: white;
      background: #1369bf;
      font-weight: bold;
      svg {
        path {
          fill: white;
        }
      }
    }
    &:first-child {
      border-radius: 10px 0px 0px 10px;
    }
    &:last-child {
      border-radius: 0px 10px 10px 0px;
    }
  }
  @media screen and (max-width: 768px) {
    flex-direction: column;
    align-items: stretch;
    margin-bottom: 32px;
    margin-top: 0px;
    li {
      margin-bottom: 2px;
      border-radius: 2px;
      &:first-child {
        border-radius: 2px;
      }
      &:last-child {
        border-radius: 2px;
      }
    }
  }
}
.title-box {
  margin-top: 24px;
  .title {
    color: #333333;
    font-weight: bold;
    font-size: 32px;
    line-height: 1.2;
    margin-bottom: 12px;
  }
  @media screen and (max-width: 768px) {
    margin-top: 24px;
    margin-bottom: 0px;
    .title {
      margin-bottom: 0px;
      font-size: 32px;
    }
  }
}
.card-city {
  font-weight: normal;
  font-size: 14px;
  line-height: 120%;
  color: #01152c;
  display: flex;
  align-items: center;
  span {
    margin-right: 8px;
  }
}

.filter-box {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 32px;
  .filter-field {
    user-select: none;
    p {
      font-size: 13px;
      color: #01152c;
    }
    .filter-select {
      background: #ffffff;
      /* Stroke color */

      border: 1px solid #e0e5ed;
      box-sizing: border-box;
      border-radius: 10px;

      position: relative;
      font-size: 16px;
      line-height: 24px;
      color: #01152c;
      div {
        padding: 12px 16px;
        display: flex;
        justify-content: space-between;
        align-items: center;
      }

      ul {
        padding: 6px 16px;
        max-height: 329px;
        overflow-y: auto;
        border-left: 1px solid #e0e5ed;
        border-right: 1px solid #e0e5ed;
        border-bottom: 1px solid #e0e5ed;
        box-sizing: border-box;
        border-radius: 0 0 10px 10px;
        position: absolute;
        z-index: 10;
        top: calc(100% - 1px);
        right: -1px;
        left: -1px;
        list-style: none;
        background: white;
        input {
          background: white;
        }
        li {
          cursor: pointer;
          padding: 6px 16px;
          &:hover {
            transition: 0.3s;
            background: #f2f9ff;
          }
        }
      }
      &.active {
        border-radius: 10px 10px 0 0;
      }
    }

    &:hover {
      cursor: pointer;
      .filter-select {
        transition: 0.3s;
        background: #f2f9ff;
      }
    }
  }
  @media screen and (max-width: 900px) {
    grid-template-columns: 1fr 1fr;
  }
  @media screen and (max-width: 600px) {
    grid-template-columns: 1fr;
  }
}
.card-name {
  color: #01152c;
  font-weight: 500;
  font-size: 18px;
  margin-bottom: 8px;
  &:hover {
    color: #004b94;
  }
}
.build-card-box {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 32px;
  .build-card {
    .card-link {
      margin-bottom: 16px;
      .card-link-box {
        .image-box {
          position: relative;
          .link-bg {
            transition: 0.3s;
            position: absolute;
            top: 0;
            right: 0;
            left: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0);
            display: none;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            color: white;
            border-radius: 2px;
            p {
              margin-left: 8px;
            }
          }
          .build-class {
            position: absolute;
            top: 12px;
            left: 12px;
            color: #ffffff;
            padding: 2px 12px;
            background: #feb205;
            border-radius: 12px;
            font-size: 12px;
            font-weight: bold;
            &.premium {
              background: #feb205;
            }
            &.comfort {
              background: #004b94;
            }
            &.business {
              background: #01152c;
            }
            &.standard {
              background: #004b94;
            }
          }
        }
      }
      &:hover {
        .image-box {
          .link-bg {
            display: flex;
            transition: background-color 0.3s;
            background-color: rgba(0, 0, 0, 0.65);
          }
        }
      }
    }
    .build-card-image {
      width: 100%;
      height: 200px;
      object-fit: cover;
      border-radius: 2px;
      margin-bottom: 6px;
    }
    .link-info-box {
      display: flex;
      align-items: center;
      a {
        margin-right: 16px;
      }
      .buklet-link {
        padding: 4px 16px;
        background: #d9ecff;
        border-radius: 4px;
        font-weight: 500;
        font-size: 14px;
        line-height: 150%;
        color: #004b94;
        &:hover {
          background: #c4e1fc;
        }
      }
      .go-site-link {
        font-weight: 500;
        color: #004b94;
        &:hover {
          color: #02407d;
        }
      }
    }
  }
  @media screen and (max-width: 900px) {
    grid-template-columns: 1fr 1fr;
  }
  @media screen and (max-width: 600px) {
    grid-template-columns: 1fr;
  }
}
.no-content {
  color: #004b94;
  background: #d9ecff;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  padding: 20px 12px;
}
.view-more {
  background: #1369bf;
  border-radius: 8px;
  color: white;
  display: flex;
  justify-content: center;
  padding: 12px;
  width: max-content;
  margin: auto;
  p {
    font-weight: 500;
    font-size: 16px;
  }
  &:hover {
    cursor: pointer;
    transition: 0.3s;
    background: #004b94;
    color: white;
  }
}
</style>
