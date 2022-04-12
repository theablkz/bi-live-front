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
    <block-admin v-if="papaRoach && !createModal && !editModal" @create="create" @editBlock="edit" :blocks="builds" />
    <block-admin-create-modal @close=" () => createModal = false" @uploadImage="inputimage" :inputImage="inputimage" @sendNewBlock="sendNewBlock" v-if="createModal" />
    <block-admin-edit-modal @close=" () => editModal = false" @uploadImage="inputimage" @deleteBlock="deleteBlock" :editData="editData" :inputImage="inputimage" @sendEditBlock="sendEditBlock" v-if="editModal"/>
  </div>
</template>

<script>
import { baseUrl } from '~/assets/config'
import { Base64 } from 'js-base64'

export default {
  name: 'admin-block',
  data: () => ({
    trueValue: {
      upAndDown: '',
      jackNumber: '',
    },
    authError: false,
    papaRoach: false,
    errorInsertForm: false,
    createModal: false,
    builds: [],
    editModal: false,
    editData: null
  }),
  methods: {
    create(){
      this.createModal = true
    },
    edit(item){
      console.log(item)
      let data = JSON.stringify(item)
      this.editData = JSON.parse(data)
      this.editModal = true
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
    async sendNewBlock(data) {
      this.$axios.post(`${baseUrl}/block`, data).then((res) => {
        console.log(res)
        this.createModal = false
        this.getBuilds()
      })
    },
    async sendEditBlock(data){
      await this.deleteBuild(data.id)
      this.$axios.post(`${baseUrl}/block`, data).then((res) => {
        console.log(res)
        this.editModal = false
        this.getBuilds()
      })
    },
    async inputimage(event) {
      let formData = new FormData()
      let imagefile = event.target
      formData.append('file', imagefile.files[0])
      return await this.$axios
        .post(`${baseUrl}/upload-image`, formData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        })
        .then((res) => {
          // this.insertForm.image = res.data.fileName
          return res.data.fileName
        })
        .catch((err) => {
          console.log(err)
          throw err
        })
    },
    getBuilds() {
      this.$axios.get(`${baseUrl}/block`).then((res) => {
        this.builds = res.data
      })
    },
    async deleteBlock(id){
      await this.deleteBuild(id)
      this.editModal = false
    },
    async deleteBuild(id) {
      await this.$axios.get(`${baseUrl}/block/delete/${id}`).then(() => {
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
