<template>
  <div>
    <header-component />
    <div v-if="currentBuild" class="grid">
      <div class="grid-col_1-4">
        <nuxt-link to="/">
          <p class="back flex flex_align-center">
            <img src="~/assets/image/icons/arrow-left.svg" /> Вернуться назад
          </p>
        </nuxt-link>
      </div>
      <div v-if="currentBuild" class="grid-col_1-8 title-box">
        <a :href="currentBuild.link" target="_blank"
          ><h2 class="title flex flex_align-center">
            {{ currentBuild.name }}
            <span style="margin-left: 8px"
              ><svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M18 13V19C18 19.5304 17.7893 20.0391 17.4142 20.4142C17.0391 20.7893 16.5304 21 16 21H5C4.46957 21 3.96086 20.7893 3.58579 20.4142C3.21071 20.0391 3 19.5304 3 19V8C3 7.46957 3.21071 6.96086 3.58579 6.58579C3.96086 6.21071 4.46957 6 5 6H11"
                  stroke="#9A9A9A"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M15 3H21V9"
                  stroke="#9A9A9A"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M10 14L21 3"
                  stroke="#9A9A9A"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </span></h2
        ></a>
      </div>
      <div class="grid-col_1-8">
        <ul class="live-tabs">
          <li
            v-if="JSON.parse(currentBuild['translation']).length"
            @click="tabIndexSubmit(0)"
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
            v-if="JSON.parse(currentBuild['3d']).length"
            @click="tabIndexSubmit(2)"
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
      <div class="grid-col_1-11">
        <div v-if="tabIndex === 0" class="tabs-show">
          <p
            v-for="(item, index) in JSON.parse(currentBuild['translation'])"
            @click="virtualIndex = index"
            :class="{ active: virtualIndex === index }"
          >
            Онлайн трансляция {{ index + 1 }}
          </p>
        </div>
        <div v-if="tabIndex === 1" class="tabs-show">
          <p
            v-for="(item, index) in JSON.parse(currentBuild['around'])"
            @click="virtualIndex = index"
            :class="{ active: virtualIndex === index }"
          >
            {{item[1]}}
          </p>
        </div>
        <div v-if="tabIndex === 2" class="tabs-show">
          <p
            v-for="(item, index) in JSON.parse(currentBuild['3d'])"
            @click="virtualIndex = index"
            :class="{ active: virtualIndex === index }"
          >
            Виртуальный шоурум {{ index + 1 }}
          </p>
        </div>
        <img
          v-if="currentBuildContent && tabIndex === 0"
          :src="JSON.parse(currentBuildContent)[virtualIndex]"
          class="content content-image"
          alt=""
        />
        <iframe
          v-if="currentBuildContent && tabIndex === 1"
          :src="JSON.parse(currentBuildContent)[virtualIndex][0]"
          class="content"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
          frameborder="0"
          title="YouTube video player"
        >
        </iframe>
        <iframe
          frameborder="0"
          allowfullscreen
          allow="vr"
          v-if="currentBuildContent && tabIndex === 2"
          :src="JSON.parse(currentBuildContent)[virtualIndex]"
          class="content"
        >
        </iframe>
      </div>
    </div>
    <footer-component />
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'
import HeaderComponent from '~/components/layouts/header-component'
import FooterComponent from '~/components/layouts/footer-component'

export default {
  name: 'builds',
  components: { FooterComponent, HeaderComponent },
  data: () => ({
    tabIndex: 0,
    builds: [],
    virtualIndex: 0,
    transactionIndex: 0,
  }),
  watch: {
    tabIndex: function () {
      this.getTitle()
    },
  },
  computed: {
    currentBuild() {
      return this.builds.find((item) => item.id == this.$route.params.id)
    },
    currentBuildContent() {
      if (!this.currentBuild) {
        return undefined
      }
      if (this.tabIndex === 0) {
        return this.currentBuild.translation
      }
      if (this.tabIndex === 1) {
        return this.currentBuild.around
      }
      if (this.tabIndex === 2) {
        return this.currentBuild['3d']
      }
      return this.currentBuild.image
    },
    baseUrl() {
      return baseUrl
    },
  },
  methods: {
    getTitle() {
      if (!this.currentBuild) {
        setTimeout(() => this.getTitle(), 1000)
        return
      }
      const name = this.currentBuild.name
      if (!name) {
        document.title = ''
      }
      if (this.tabIndex === 0) {
        document.title = `Онлайн-трансляция - ${name}`
      }
      if (this.tabIndex === 1) {
        document.title = `Видео обзор - ${name}`
      }
      if (this.tabIndex === 2) {
        document.title = `Онлайн-трансляция - ${name}`
      }
    },
    tabIndexSubmit(index){
      this.virtualIndex = 0
      this.tabIndex = index
    }
  },
  mounted() {
    this.tabIndex = this.$route.hash ? parseInt(this.$route.hash[1]) : 0
    this.$axios.get(baseUrl).then((res) => {
      this.builds = res.data
      this.getTitle()
    })
  },
}
</script>

<style lang="scss" scoped>
.tabs-show {
  display: flex;
  align-items: center;
  overflow-x: auto;
  margin-bottom: 16px;
  p {
    margin-right: 8px;
    font-weight: 500;
    font-size: 16px;
    line-height: 20px;
    text-transform: uppercase;
    padding: 12px 20px;
    color: #747474;
    white-space: nowrap;
    user-select: none;
    &:hover {
      color: #004b94;
      cursor: pointer;
    }
    &.active {
      color: #004b94;
      border-bottom: 2px solid #004b94;
    }
  }
}
.back {
  font-size: 16px;
  line-height: 18px;
  color: #5c5c5c;
  margin-top: 30px;
  img {
    margin-right: 8px;
  }
  &:hover {
    color: #1369bf;
  }
}
.content {
  width: 100%;
  height: auto;
  min-height: 600px;
  &.content-image {
    min-height: auto;
  }
  @media screen and (max-width: 768px) {
    min-height: 400px;
  }
}
.live-tabs {
  display: flex;
  align-items: center;
  border-radius: 10px;
  list-style: none;
  margin-top: 0px;
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
      border-bottom-left-radius: 10px;
      border-top-left-radius: 10px;
    }
    &:last-child {
      border-radius: 0px 10px 10px 0px;
      border-top-right-radius: 10px;
      border-bottom-right-radius: 10px;
    }
  }
  @media screen and (max-width: 768px) {
    flex-direction: column;
    align-items: stretch;
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
  margin-top: 0px;
  .title {
    color: #333333;
    font-weight: bold;
    font-size: 40px;
    line-height: 1.2;
    &:hover {
      color: #1369bf;
    }
  }
  @media screen and (max-width: 768px) {
    margin-top: 24px;
    margin-bottom: 0px;
    .title {
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
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 16px;
      position: relative;
      font-size: 16px;
      line-height: 24px;
      color: #01152c;

      ul {
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
      .card-name {
        color: #01152c;
        font-weight: 500;
        font-size: 18px;
        margin-bottom: 8px;
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
