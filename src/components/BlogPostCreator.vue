<template>
  <div class="blog-post-creator">
    <div class="post-inputs">
      <div class='title-input'>
        <error>标题必须多于10个字母</error>
        <Input v-model="title" placeholder="标题"/>
      </div>
      <div class='cat-input'>
        <error>文章必须有1个类别</error>
        <Select
        placeholder='选择类别'
        v-model="category"
        v-if='postCategories.length'
        >
        <Option
        v-for="(cat,index) in postCategories"
        :key='index'
        :value='cat.id'  
        >{{cat.label}}</Option>
        </Select>
      </div>
      <div class='image-input'>
         <error>文章必须配有一张图片</error>
         <div class='inner-image-input'>
           <img :src='image_url' width='40px' height='40px' v-if="image_url"/>
         <Button @click='showImageModal=true' type='primary' class='flex-center' icon='ios-camera-outline'>添加图片</Button>
        </div>
      </div>
    </div>
    <quill-editor
      v-model="content"
      ref="myQuillEditor"
      :options="editorOption"
    />
    <div class='post-actions-row'>
      <Button class='btn-delete' @click='del'>删除</Button>
      <Button type='primary' @click='save'>保存</Button>
      <Button type='primary' @click='publish'>发送</Button>

    </div>
  </div>
  
</template>

<script>
import "quill/dist/quill.snow.css";
import { quillEditor } from "vue-quill-editor";
import {Button,Input,Select} from 'iview';
import Error from './Error.vue'

export default {
  name: "BlogPostCreator",
  components: {
    quillEditor,
    Button,
    Input,
    Select,
    Error
  },
  data: () => ({
    title:'',
    category:'',
    image_url:'',
    showImageModal:false,
    content: "",
    editorOption: {
      debug: "info",
      placeholder: "输入内容。。。",
      readOnly: true,
      theme: "snow",
    },
    delta: undefined,
    postCategories: [
      {
        id: 1,
        label: "NodeJs",
        img:
          "https://pluralsight.imgx.net/paths/path-icons/nodejs-601628de9d.png?w=200",
      },
      {
        id: 2,
        label: "JavaScript",
        img: "https://cdn.auth0.com/blog/js-fatigue/JSLogo.png",
      },
    ],
  }),

  watch: {
    content(val) {
      this.delta = this.myQuillEditor.qull.getContents();
    },
  },
  methods:{
    del(){

    },

    save(){

    },

    publish(){

    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.quill-editor {
  height: 72vh;
}

.inner-image-input{
  display:flex;
  align-items:center;
}

.flex-center{
  display:flex;
  align-items:center;
  justify-content:center;
}

.post-actions-row{
  display:flex;
  justify-content:space-between;
  padding:10px;
}

.ivew-icon-ios-camera-outline{
  font-size:16px;
}
</style>
