<template>
  <div class="grid">
    <div class="grid-col_1-8 title-box">
      <h2 class="title">Каталог электронных буклетов</h2>
      <p class="secondary-text">
        Вы можете скачать электронные версии буклетов и ознакомиться с нашими
        проектами
      </p>
    </div>

    <div class="grid-col_1-11">
      <div class="filter-box">
        <div @click="selectsCity = !selectsCity" class="filter-field">
          <p class="indent_bottom-h5">Город</p>
          <div class="filter-select">
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
              <li @click="cityValue = null">Все города</li>
              <li v-for="item in cities" :key="item" @click="cityValue = item">
                {{ item }}
              </li>
            </ul>
          </div>
        </div>
        <div @click="selectsClass = !selectsClass" class="filter-field">
          <p class="indent_bottom-h5">Класс</p>
          <div class="filter-select">
            <span>{{ classValue || 'Все классы' }}</span>
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
            <ul v-if="selectsClass">
              <li @click="classValue = null">Все города</li>
              <li
                v-for="item in classes"
                :key="item"
                @click="classValue = item"
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
        <div v-for="item in filters" :key="item.id" class="build-card">
          <a class="card-link" target="_blank" :href="item.link">
            <div class="card-link-box">
              <div class="image-box">
                <img
                  class="build-card-image"
                  :src="`${baseUrl}/get-image/${item.image}`"
                  alt=""
                />
                <span
                  class="build-class"
                  :class="{
                    premium: item.class === 'Премиум',
                    comfort: item.class === 'Комфорт',
                    business: item.class === 'Бизнес',
                  }"
                  >{{ item.class }}</span
                >
                <div class="link-bg">
                  <img src="~/assets/image/icons/link.svg" alt="" />
                  <p>Перейти на сайт</p>
                </div>
              </div>
              <div class="flex flex_align-center flex_justify-between">
                <p class="card-name">{{ item.name }}</p>
                <p class="secondary-text">{{ item.city }}</p>
              </div>
            </div>
          </a>
          <div class="link-info-box">
            <a class="buklet-link" target="_blank" :href="`${baseUrl}/get-buklet/${item.buklet}`"
              >Скачать
            </a>
            <a class="go-site-link" target="_blank" :href="item.link"
              >Перейти на сайт</a
            >
          </div>
        </div>
      </div>
    </div>
    <div v-if='!filters.length' class="grid-col_1-11 no-content">
      <p>Нет данных</p>
    </div>
    <div v-if='filters.length > limit' @click='limit = limit + 6' class="grid-col_1-11 view-more">
      <p>Показать еще</p>
    </div>
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'

export default {
  name: 'catalog',
  data: () => ({
    selectsCity: false,
    selectsClass: false,
    cityValue: null,
    classValue: null,
    builds: [

    ],
    limit: 6,
  }),
  computed: {
    classes() {
      return [...new Set(this.builds.map((item) => item.class))]
    },
    cities() {
      return [...new Set(this.builds.map((item) => item.city))]
    },
    filters() {
      return this.builds
        .filter(
          (item) =>
            (this.cityValue ? item.city === this.cityValue : true) &&
            (this.classValue ? item.class === this.classValue : true)
        )
        .slice(0, this.limit)
    },
    baseUrl(){
      return baseUrl
    }
  },
  created() {
    this.$axios.get(baseUrl).then(res => {
      this.builds = res.data
    })
  }
}
</script>

<style lang="scss" scoped>

.title-box {
  margin-bottom: 80px;
  margin-top: 80px;
  .title {
    color: #01152c;
    font-weight: bold;
    font-size: 48px;
    margin-bottom: 12px;
  }
  .secondary-text {
    color: #01152c;
    opacity: 0.6;
    font-size: 18px;
  }
  @media screen and (max-width: 768px) {
    margin-top: 24px;
    margin-bottom: 0px;
    .title {
      font-size: 32px;
    }
  }
}
.secondary-text {
  color: #01152c;
  opacity: 0.6;
  font-size: 14px;

}
.filter-box {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 32px;
  .filter-field {
    user-select: none;
    .filter-select {
      background: #f4f5f7;
      border: 1px solid #e0e5ed;
      box-sizing: content-box;
      border-radius: 4px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 16px;
      position: relative;
      ul {
        border-left: 1px solid #e0e5ed;
        border-right: 1px solid #e0e5ed;
        border-bottom: 1px solid #e0e5ed;
        box-sizing: border-box;
        border-radius: 0 0 4px 4px;
        position: absolute;
        z-index: 10;
        top: calc(100% - 1px);
        right: -1px;
        left: -1px;
        list-style: none;
        background: #f4f5f7;
        li {
          cursor: pointer;
          padding: 6px 16px;
          &:hover {
            transition: 0.3s;
            background: #d9ecff;
          }
        }
      }
    }
    &:hover {
      cursor: pointer;
      .filter-select {
        transition: 0.3s;
        background: #dedede;
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
.no-content{
  color: #004b94;
  background: #d9ecff;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  padding: 20px 12px;
}
.view-more {
  color: #004b94;
  background: #d9ecff;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  padding: 12px;
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
