<template>
  <div class="block-admin-create-modal">
    <div>
      <button class="close-button" @click="() => $emit('close')">Back</button>

      <form @submit.prevent="createBlock">
        <label><small>Заголовок</small><input required v-model="title" type="text"></label>
        <label><small>город</small>
          <select required v-model="city">
            <option value="Актау">Актау</option>
            <option value="Алматы">Алматы</option>
            <option value="Атырау">Атырау</option>
            <option value="Нур-Султан">Нур-Султан</option>
            <option value="Шымкент">Шымкент</option>
          </select>
        </label>
        <label><small>формат</small>
          <select required v-model="format">
            <option value="МАСТЕР-КЛАСС">МАСТЕР-КЛАСС</option>
            <option value="ВЕБИНАР">ВЕБИНАР</option>
          </select>
        </label>
        <label><small>Описание</small><input required v-model="description" type="text"></label>
        <label><small>Дата проведения</small>
          <input required v-model="dateCalendar" type="date">
          <input required v-model="dateTime" type="time">
        </label>
        <label><small>Ссылка на ивент</small><input required v-model="link" type="text"></label>
        <label><small>Изображение</small><input required @input="uploadImage" type="file" accept="image/png, image/jpeg"></label>
        <label><small>Ссылка на видео</small><input required v-model="videolink" type="text"></label>
        <label class="checkbox"><small>статус</small><input v-model="status" type="checkbox"></label>
        <input type="submit">

      </form>
    </div>
    <div class="event-card">
      <div class="event-img-div">
        <img
          :src="`${baseUrl}/get-image/${image}`"

          loading="lazy"
          sizes="(max-width: 479px) 93vw, (max-width: 767px) 84vw, (max-width: 991px) 46vw, (max-width: 1279px) 30vw, 385.4375px"
          alt=""
          class="event-img"
        />
      </div>
      <div class="event-txt-div">
        <div class="event-label-div">
          <div class="event-label bestseller">{{city}}</div>
          <div class="event-label">{{format}}</div>
        </div>
        <div class="event-title">{{title}}</div>
        <div>
          {{description}}
        </div>
        <div class="event-card-spacer"></div>
        <div class="event-time-div">
          <div class="event-time-block">
            <div class="event-time-note">Дата проведения:</div>
            <div class="event-time">{{blockDate}}</div>
          </div>
          <div class="event-time-block">
            <div class="event-time-note">Начало:</div>
            <div class="event-time">{{blockTime}}</div>
          </div>
        </div>
        <div class="event-cta-div">
          <a :href="link" target="_blank" class="btn-cta link-hover w-inline-block"
          ><div>Записаться</div>
            <div class="btn-border-full"></div></a
          ><a
          :href="videolink"
          target="_blank"
          class="lightbox-link link-hover w-inline-block w-lightbox"
          aria-label="open lightbox"
          aria-haspopup="dialog"
        ><div class="btn-promo">
          <div class="btn-circle-promo">
            <img
              src="https://uploads-ssl.webflow.com/624c2e1143c0527c48c3fd6b/624c2e1143c05235e5c3fd8f_icon-play.svg"
              loading="lazy"
              alt=""
              class="btn-icon"
            />
            <div class="btn-border-promo"></div>
            <div class="btn-bg-promo"></div>
          </div>
          <div
            class="promo-txt-div"
            style="border-color: rgba(255, 255, 255, 0.098)"
          >
            <div>Видео-анонс</div>
          </div>
        </div>
        </a>
        </div>
      </div>
    </div>
  </div>
</template>
<!--city, status, format, title, description, date, link, image, videoLink, categories-->
<script>
import { baseUrl } from '~/assets/config'

export default {
  name: "block-admin-create-modal",
  props: ['inputImage'],
  data: () => ({
    title: '',
    city: '',
    status: true,
    format: '',
    description: '',
    date: '',
    link: '',
    image: '',
    videolink: '',
    categories: '',
    dateCalendar: '',
    dateTime: ''
  }),
  computed: {
    baseUrl() {
      return baseUrl
    },
    blockDate() {
      return new Intl.DateTimeFormat('ru', {
        day: 'numeric',
        month: 'short',
        year: 'numeric'
      }).format(this.dateJoiner)
    },
    blockTime() {
      return new Intl.DateTimeFormat('ru', {
        hour: 'numeric',
        minute: 'numeric'
      }).format(this.dateJoiner)
    },
    dateJoiner() {
      return this.dateCalendar && this.dateTime ? new Date(`${this.dateCalendar} ${this.dateTime}`) : ''
    }
  },
  methods: {
    async uploadImage(event){
      try {
        this.image = await this.inputImage(event)
        console.log(this.image)
      } catch (e) {

      }
    },
    createBlock(){
      const data = {
        title: this.title,
        city: this.city,
        status: this.status,
        format: this.format,
        description: this.description,
        date: new Date(`${this.dateCalendar} ${this.dateTime}`),
        link: this.link,
        image: this.image,
        videolink: this.videolink,
        categories: this.categories
      }
      console.log(data)
      this.$emit('sendNewBlock', data)
    }
  }
}
</script>

<style lang="scss" scoped>
form {
  display: grid;
  grid-template-columns: 1fr;
  gap: 16px;
}
.close-button {
  width: 90px;
}
.checkbox {
  input {
    width: 100px;
    height: 20px;
    min-height: 1rem;
  }
}
.block-admin-create-modal {
  display: grid;
  grid-template-columns: 1fr 400px;
  gap: 32px;
  padding: 32px;
}

.event-card {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  overflow: hidden;
  width: 100%;
  height: 100%;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-pack: justify;
  -webkit-justify-content: space-between;
  -ms-flex-pack: justify;
  justify-content: space-between;
  border-radius: 24px;
  background-color: #061a49;
}
.event-card:hover {
  transform: translateY(12px);
  transition: 0.4s;
  cursor: pointer;
}
.event-img-div {
  overflow: hidden;
  width: 100%;
}

.event-img {
  width: 100%;
}

.event-txt-div {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  padding: 24px 16px;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-pack: justify;
  -webkit-justify-content: space-between;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-flex: 1;
  -webkit-flex: 1;
  -ms-flex: 1;
  flex: 1;
  letter-spacing: 0.1px;
  background-color: #051541;
  font-family: 'Gotham book', sans-serif;
  color: #e9ecff;
  font-size: 15px;
  line-height: 24px;
  font-weight: 400;
}

.event-label-div {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-flex-wrap: wrap;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
}

.event-label {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  height: 22px;
  margin-right: 4px;
  margin-bottom: 10px;
  padding-right: 8px;
  padding-left: 8px;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-flex: 0;
  -webkit-flex: 0 0 auto;
  -ms-flex: 0 0 auto;
  flex: 0 0 auto;
  border-radius: 20px;
  background-color: rgba(68, 44, 250, 0.5);
  font-family: Gotham, sans-serif;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
}

.event-label.bestseller {
  background-color: rgba(245, 78, 223, 0.5);
}

.event-label.master {
  background-color: rgba(36, 206, 255, 0.5);
}

.event-title {
  margin-bottom: 18px;
  font-family: Gotham, sans-serif;
  color: #fff;
  font-size: 20px;
  line-height: 26px;
  font-weight: 500;
}

.event-time-div {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  margin-top: auto;
  padding-top: 12px;
  padding-bottom: 20px;
  -webkit-box-pack: justify;
  -webkit-justify-content: space-between;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: start;
  -webkit-align-items: flex-start;
  -ms-flex-align: start;
  align-items: flex-start;
  border-top: 1px solid hsla(0, 0%, 100%, 0.1);
}

.event-time-note {
  margin-bottom: 4px;
  opacity: 0.5;
  font-size: 13px;
  line-height: 16px;
}

.event-time {
  font-family: Gotham, sans-serif;
  color: #fff;
  font-size: 15px;
  font-weight: 500;
}

.event-time-block {
  width: 48%;
}

.event-cta-div {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -webkit-justify-content: space-between;
  -ms-flex-pack: justify;
  justify-content: space-between;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
}

.btn-cta {
  position: relative;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  overflow: hidden;
  height: 44px;
  padding-right: 42px;
  padding-left: 42px;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  border-radius: 80px;
  background-color: rgba(0, 26, 57, 0.2);
  -webkit-transition: all 200ms ease;
  transition: all 200ms ease;
  font-family: Gotham, sans-serif;
  color: #fdfdfd;
  font-size: 15px;
  font-weight: 500;
  text-align: center;
  text-decoration: none;
}

.btn-cta:hover {
  background-image: -webkit-gradient(
    linear,
    left top,
    right top,
    from(#cf32ff),
    to(#005aff)
  );
  background-image: linear-gradient(90deg, #cf32ff, #005aff);
}

.btn-cta:active {
  background-image: -webkit-gradient(
    linear,
    left top,
    right top,
    from(#9417ba),
    to(#0049d0)
  );
  background-image: linear-gradient(90deg, #9417ba, #0049d0);
}

.btn-border-full {
  position: absolute;
  left: 0%;
  top: 0%;
  right: 0%;
  bottom: 0%;
  border-radius: 0px;
}

.lightbox-div {
  position: absolute;
  left: auto;
  top: auto;
  right: 12px;
  bottom: 48px;
  z-index: 20;
}

.btn-promo {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
}

.btn-border-promo {
  position: absolute;
  left: auto;
  top: auto;
  right: auto;
  bottom: auto;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 44px;
  height: 44px;
}

.btn-bg-promo {
  position: absolute;
  left: auto;
  top: auto;
  right: auto;
  bottom: auto;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 44px;
  height: 44px;
  border-radius: 100px;
  background-color: #001a39;
  opacity: 0.2;
}

.btn-border-full {
  --full: linear-gradient(blue 0 0);
  --slist: #b04ccf, #005aff;
  border: solid 1px transparent;
  border-radius: 50px;
  background: linear-gradient(-20deg, var(--slist)) border-box;
  -webkit-mask: var(--full) padding-box, var(--full);
  -webkit-mask-composite: xor;
  mask: var(--full) padding-box exclude, var(--full);
}
.btn-border-full:hover {
  border: solid 0px transparent;
}

.btn-bg-promo {
  position: absolute;
  left: auto;
  top: auto;
  right: auto;
  bottom: auto;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 44px;
  height: 44px;
  border-radius: 100px;
  background-color: #001a39;
  opacity: 0.2;
}

.btn-promo {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
}

.btn-border-promo {
  position: absolute;
  left: auto;
  top: auto;
  right: auto;
  bottom: auto;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 44px;
  height: 44px;
}

.btn-circle-promo {
  position: relative;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 32px;
  height: 32px;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
}
.promo-txt-div {
  display: none;
  margin-right: 10px;
  padding-top: 2px;
  padding-bottom: 2px;
  border-bottom: 1px solid hsla(0, 0%, 100%, 0.1);
  font-family: Gotham, sans-serif;
  color: #fdfdfd;
  font-size: 15px;
  font-weight: 500;
  letter-spacing: 0.1px;
}
.event-card-spacer {
  height: 24px;
}

</style>
