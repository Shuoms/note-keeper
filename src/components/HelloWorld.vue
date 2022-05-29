<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <div class="pa-4" style="min-height: calc(100vh - 172px)">
          <h2>新建笔记</h2>
          <v-card elevation="0" color="#f6f6f6" class="mt-4">
            <v-img width="100%"
                   height="196px"
                   contain
                   v-if="uploadUrl" :src="uploadUrl"></v-img>
          </v-card>
          <v-file-input
              v-model="file"
              prepend-icon="mdi-image"
              accept="image/*"
              label="上传图片"
          />
          <v-text-field v-model="title" label="标题"></v-text-field>
          <v-textarea label="内容" v-model="content" counter="500"></v-textarea>
        </div>
        <v-btn @click="sendMail" block dark large elevation="0" class="mt-4">发送
          <v-icon right>mdi-send</v-icon>
        </v-btn>
      </v-col>


    </v-row>
  </v-container>
</template>

<script>
const toBase64 = file => new Promise((resolve, reject) => {
  const reader = new FileReader()
  reader.readAsDataURL(file)
  reader.onload = () => resolve(reader.result)
  reader.onerror = error => reject(error)
})

export default {
  data: () => ({
    file: null,
    title: '',
    content: ''
  }),
  methods: {
    async sendMail () {
      const file = await toBase64(this.file)
      window.open('mailto:test@example.com?subject=' + this.title + '&body=' + this.content + '<img src="' + file + '"/>')
    }
  },
  computed: {
    uploadUrl: function () {
      console.log(this.file)
      return this.file ? URL.createObjectURL(this.file) : null
    }
  }

}
</script>
