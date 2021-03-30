<template>
  <div>
    <div v-if='!login'>
      <form @submit.prevent='loginSubmit'>
        <input type='text' placeholder='login' v-model='loginValue.login'>
        <input type='password' placeholder='password' v-model='loginValue.password'>
        <input type='submit'>
      </form>
    </div>
    <div v-if='login' class="grid">
      <div class="grid-col_1-6">
        <form @submit.prevent="submit">
          <input v-model='insertForm.name' type="text" placeholder="имя жк" />
          <input v-model='insertForm.link' type="text" placeholder="ссылка на сайт" />
          <select v-model='insertForm.class'>
            <option disabled selected :value='null'>Класс</option>
            <option value="Стандарт">Стандарт</option>
            <option value="Комфорт">Комфорт</option>
            <option value="Бизнес">Бизнес</option>
            <option value="Премиум">Премиум</option>

          </select>
          <select v-model='insertForm.city'>
            <option disabled selected :value='null'>Город</option>
            <option value="Нур-Султан">Нур-Султан</option>
            <option value="Алматы">Алматы</option>
            <option value="Шымкент">Шымкент</option>
            <option value="Атырау">Атырау</option>
            <option value="Актау">Актау</option>
          </select>
          <p>Буклет</p>
          <input type="file" @input="inputBuklet" placeholder="Буклет" />
          <p>Изображение</p>
          <input type="file" @input="inputimage" placeholder="Изображение" />
          <p>активность</p>
          <input v-model='insertForm.active' type='checkbox'>
          <p v-if="errorInsertForm" class="rate-change-red">Заполните все поля</p>
          <input type="submit" />
        </form>
      </div>
      <div class="grid-col_6-11">
        <div v-for="item in builds" class="cards">
          <img :src="`${baseUrl}/get-image/${item.image}`" :alt="item.image" />
          <div>
            <h3>{{ item.name }}</h3>
            <p>{{ item.city }}</p>
            <p>{{ item.class }}</p>
            <p>{{ item.link }}</p>
            <p>активность: {{!!item.active}}</p>
            <a target="_blank" :href="`${baseUrl}/get-buklet/${item.buklet}`">{{ item.buklet }}</a>
            <button @click='deleteBuild(item.id)' class='button_red'>Удалить</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'

export default {
  name: 'admin',
  data: () => ({
    loginData: {
      login: 'admin',
      password: 'gfhfijqpfgf[kj'
    },
    loginValue: {
      login: '',
      password: ''
    },
    login: false,
    builds: [],
    insertForm: {
      name: '',
      city: null,
      buklet: '',
      image: '',
      link: '',
      active: true,
      class: null,
    },
    errorInsertForm: false,
  }),
  methods: {
    loginSubmit(){
      if (this.loginValue.login === this.loginData.login && this.loginValue.password === this.loginData.password){
        this.login = true
      }
    },
    submit() {
      if (
        !this.insertForm.buklet ||
        !this.insertForm.image ||
        !this.insertForm.name ||
        !this.insertForm.city ||
        !this.insertForm.class ||
        !this.insertForm.link
      ) {
        this.errorInsertForm = true
        return
      }
      this.$axios.post(baseUrl, this.insertForm).then((res) => {
        console.log(res)
        this.getBuilds()
      })
    },
    inputBuklet(event) {
      var formData = new FormData()
      var imagefile = event.target
      formData.append('file', imagefile.files[0])
      this.$axios
        .post(`${baseUrl}/upload-buklet`, formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        })
        .then((res) => {
          this.insertForm.buklet = res.data.fileName
        })
        .catch((err) => {
          console.log(err)
        })
    },
    inputimage(event) {
      var formData = new FormData()
      var imagefile = event.target
      formData.append('file', imagefile.files[0])
      this.$axios
        .post(`${baseUrl}/upload-image`, formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        })
        .then((res) => {
          this.insertForm.image = res.data.fileName
        })
        .catch((err) => {
          console.log(err)
        })
    },
    getBuilds() {
      this.$axios.get(baseUrl).then((res) => {
        this.builds = res.data
      })
    },
    deleteBuild(id){
      this.$axios.get(`${baseUrl}/delete/${id}`).then(() => {
        this.getBuilds()
      })
    }
  },
  computed: {
    baseUrl(){
      return baseUrl
    }
  },
  created() {
    this.getBuilds()
  },
}
</script>

<style lang="scss" scoped>
.cards {
  border: 1px solid blue;
  padding: 10px;
  display: flex;
  .button_red{
    max-width: 200px;
    padding: 8px 10px;
    line-height: 1;
  }
  img {
    width: 200px;
    height: 160px;
    object-fit: cover;
    margin-right: 10px;
  }
}
</style>
