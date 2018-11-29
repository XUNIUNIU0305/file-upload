<template>
  <div class="file">
    <div class="inputbox">
      <span class="file-text">{{mess}}</span>
      <input type="file" class="input-choose" ref="pathClear" multiple="multiple" accept="application/vnd.openxmlformats-officedocument.spreadsheetml.sheet, application/vnd.ms-excel" @change="getFile($event)">
    </div>
    <!-- accept可限制上传文件的类型 -->
    <div class="btn" @click="Upload($event)">上传</div>
  </div>
</template>

<script>
export default {
  name: 'FileUpload',
  data () {
    return {
      file: "",
      mess: "选择文件"
    }
  },
  methods: {
    getFile(event) {
      this.mess = "选择文件";
      this.file = event.target.files[0];
      if (event.target.files[0].name) {
        this.mess = "已选择:" + event.target.files[0].name;
      }
    },
    Upload(event) {
      let formData = new FormData();
      formData.append("file", this.file);
      let config = {
        headers: {
          "Content-Type": "multipart/form-data",
        }
      };
      alert("请看console打印信息");
      // 请求接口时将headers设为"Content-Type": "multipart/form-data",
      // this.$axios.post(path,formData,config)
      // .then(({data}) =>{

      // })
      // .catch(error => {
      //   console.log(error);
      // })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "../assets/css/upload.css";
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
