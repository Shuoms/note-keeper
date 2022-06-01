<template>
  <v-container>
    <v-row>
      <v-col cols="12">

        <div class="pa-4" style="min-height: calc(100vh - 172px)">
          <h2>Steckbrief</h2>
          <v-card elevation="0" color="#f6f6f6" class="mt-4">
            <v-img width="100%"
                   height="196px"
                   contain
                   v-if="uploadUrl" :src="uploadUrl"></v-img>
          </v-card>
          <v-file-input
              name="file"    
              v-model="file"
              prepend-icon="mdi-image"
              accept="image/*"
              label="Foto hochladen"
          />
          <v-text-field name="subject" v-model="title" label="Ideentitel"></v-text-field>
          <v-textarea label="Ideenbeschreibung" name="body" v-model="content" counter="500"></v-textarea>
        </div>
        <v-btn v-if="linkReady" ref="link" block color="primary" large elevation="0" class="mt-4">Unterladen und Absenden</v-btn>
        <v-btn v-else @click="sendMail" block dark large elevation="0" class="mt-4">
          Absenden
          <v-icon right>mdi-send</v-icon>
        </v-btn>


      </v-col>


    </v-row>
  </v-container>
</template>

<script>




export default {
  data: () => ({
    file: null,
    title: '',
    content: '',
    imgUrl: '',
    linkReady: false
  }),
  methods: {
    sendMail () {
      this.$nextTick(() => {
        window.open(`mailto:Shuo Ma<shuo.ma.ma@bmw.de>?subject= "Ideetitel": ${this.title}&body= "Ideebeschreibung": ${this.content}\n
`)
      })

    }
  },
  watch: {
    async file () {
      // const currentUrl = baseUrl + (await uploadImg(val))
      // console.log(currentUrl)
      // this.imgUrl = currentUrl
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
