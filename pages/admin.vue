<template>
  <div>
    <div v-if="!papaRoach">
      <form @submit.prevent="dell">
        <input type="text" placeholder="login" v-model="trueValue.upAndDown" />
        <input
          type="password"
          placeholder="password"
          v-model="trueValue.jackNumber"
        />
        <p v-if='authError' class='field_error'><span style='{color: red}'>Ошибка авторизации. Логин или пароль неверные</span></p>
        <input type="submit" />
      </form>
    </div>
    <div v-if="papaRoach" class="grid">
      <div class="grid-col_1-6">
        <form @submit.prevent="submit">
          <small>Имя</small>
          <input v-model="insertForm.name" type="text" placeholder="имя жк" />
          <small>ссылка на сайт</small>
          <input
            v-model="insertForm.link"
            type="text"
            placeholder="ссылка на сайт"
          />
          <small>город</small>
          <select v-model="insertForm.city">
            <option disabled selected :value="null">Город</option>
            <option value="Нур-Султан">Нур-Султан</option>
            <option value="Алматы">Алматы</option>
            <option value="Шымкент">Шымкент</option>
            <option value="Атырау">Атырау</option>
            <option value="Актау">Актау</option>
          </select>
          <small>Онлайн трансляция (ссылка)</small>
          <input
            v-for="(item, index) in insertForm['translation']"
            v-model="insertForm['translation'][index]"
            type="text"
            placeholder="Онлайн трансляция (ссылка)"
          />
          <button
            @click="insertForm['translation'] = [...insertForm['translation'], '']"
            type="button"
          >
            Добавить еще Трансляцию
          </button>
          <small>Видео обзор (ссылка)</small>
          <div  v-for="(item, index) in insertForm['around']">
            <input
              v-model="insertForm['around'][index][0]"
              type="text"
              placeholder="Видео обзор (ссылка)"
            />
            <input
              v-model="insertForm['around'][index][1]"
              type="text"
              placeholder="Видео обзор (наз. тэга)"
            />
          </div>

          <button
            @click="insertForm['around'] = [...insertForm['around'], ['','']]"
            type="button"
          >
            Добавить еще Видео обзор
          </button>
          <small>Виртуальный шоурум</small>
          <input
            v-for="(item, index) in insertForm['3d']"
            v-model="insertForm['3d'][index]"
            type="text"
            placeholder="Виртуальный шоурум (ссылка)"
          />
          <button
            @click="insertForm['3d'] = [...insertForm['3d'], '']"
            type="button"
          >
            Добавить еще Виртуальный шоурум
          </button>
          <p>Изображение</p>
          <small>{{ insertForm.image }}</small>
          <input type="file" @input="inputimage" placeholder="Изображение" />
          <p v-if="errorInsertForm" class="rate-change-red">
            Заполните все поля
          </p>
          <input type="submit" />
          <button
            v-if="insertForm.id !== null"
            @click="insertForm.id = null"
            type="button"
            class="button_yellow"
          >
            отмена редактирования
          </button>
        </form>
      </div>
      <div class="grid-col_6-11">
        <div v-for="item in builds" class="cards">
          <img :src="`${baseUrl}/get-image/${item.image}`" :alt="item.image" />
          <div>
            <h3>{{ item.name }}</h3>
            <p>{{ item.city }}</p>
            <p>{{ item.class }}</p>
            <p>ссылка - {{ item.link }}</p>
            <p>Видео обзор - {{ item.around }}</p>
            <p>трансляция - {{ item.translation }}</p>
            <p>3D шоурум - {{ item['3d'] }}</p>
            <a target="_blank" :href="`${baseUrl}/get-buklet/${item.buklet}`">{{
              item.buklet
            }}</a>
            <button @click="updateButton(item)" class="button_green">
              Редактировать
            </button>
            <button @click="deleteBuild(item.id)" class="button_red">
              Удалить
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'
import { Base64 } from 'js-base64'

export default {
  name: 'admin',
  data: () => ({
    trueValue: {
      upAndDown: '',
      jackNumber: '',
    },
    authError: false,
    papaRoach: false,
    builds: [],
    insertForm: {
      id: null,
      name: '',
      city: null,
      around: [['','']],
      image: '',
      link: '',
      active: true,
      class: null,
      '3d': [''],
      translation: [''],
    },
    errorInsertForm: false,
  }),
  methods: {
    updateButton(item) {
      this.insertForm = { ...item }
      this.insertForm['3d'] = JSON.parse(item['3d'])
      this.insertForm.translation = JSON.parse(item.translation)
      this.insertForm.around = item.around ? JSON.parse(item.around) : [['', '']]
    },
    async dell() {
      this.authError = false
      if (this.trueValue.upAndDown && this.trueValue.jackNumber) {
        this.$axios.post(`${baseUrl}/auth`, {
          user: `${Base64.encode(this.trueValue.upAndDown)}${Base64.encode(this.trueValue.jackNumber)}`
        }).then(() => {
          this.papaRoach = true
        }).catch(err => {
          console.log(err)
          this.authError = true
        })
      }else {
        this.authError = true
      }
    },
    async submit() {
      if (
        !this.insertForm.image ||
        !this.insertForm.name ||
        !this.insertForm.city ||
        !this.insertForm.link
      ) {
        this.errorInsertForm = true
        return
      }
      let checkAround = this.insertForm.around.filter(item => !!item[0] || !!item[1])
      if (checkAround.some(item => !item[0] || !item[1])) {
        console.log('mdf?', checkAround)
        this.errorInsertForm = true
        return
      }
      if (this.insertForm.id !== null) {
        await this.deleteBuild(this.insertForm.id)
      }
      this.insertForm['3d'] = JSON.stringify(
        this.insertForm['3d'].filter((item) => !!item)
      )
      this.insertForm.translation = JSON.stringify(
        this.insertForm.translation.filter((item) => !!item)
      )
      this.insertForm.around = JSON.stringify(
        this.insertForm.around.filter((item) => !!item[0])
      )
      this.$axios.post(baseUrl, this.insertForm).then((res) => {
        console.log(res)
        this.insertForm = {
          id: null,
          name: '',
          city: null,
          around: ['',''],
          image: '',
          link: '',
          active: true,
          class: null,
          '3d': [''],
          translation: [''],
        }
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
        this.builds = res.data.sort((a,b) => new Intl.Collator().compare(a.name, b.name))
      })
    },
    deleteBuild(id) {
      this.$axios.get(`${baseUrl}/delete/${id}`).then(() => {
        this.getBuilds()
      })
    },
  },
  computed: {
    baseUrl() {
      return baseUrl
    },
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
  .button_red {
    max-width: 200px;
    padding: 8px 10px;
    line-height: 1;
  }
  .button_green {
    max-width: 200px;
    padding: 8px 10px;
    line-height: 1;
    background: #6cd970;
  }
  img {
    width: 200px;
    height: 160px;
    object-fit: cover;
    margin-right: 10px;
  }
}
</style>
