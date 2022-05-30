<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <form action="mailto:juhaodong@gmail.com" method="post" enctype="multipart/form-data">
          <div class="pa-4" style="min-height: calc(100vh - 172px)">
            <h2>新建笔记</h2>
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
                label="上传图片"
            />
            <v-text-field name="subject" v-model="title" label="标题"></v-text-field>
            <v-textarea label="内容" name="body" v-model="content" counter="500"></v-textarea>
          </div>
          <v-btn name="submit" block dark large elevation="0" class="mt-4" type="submit">发送
            <v-icon right>mdi-send</v-icon>
          </v-btn>
        </form>
      </v-col>


    </v-row>
  </v-container>
</template>

<script>


export default {
  data: () => ({
    file: null,
    title: '',
    content: ''
  }),
  methods: {
  },
  computed: {
    uploadUrl: function () {
      console.log(this.file)
      return this.file ? URL.createObjectURL(this.file) : null
    }
  }

}
</script>
