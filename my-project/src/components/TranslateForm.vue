<template>
  <div id="translateForm" class="container">
    <div class="row">
      <div class="col-xs-6  col-xs-offset-3">
        <form v-on:submit="formSubmit" class="form-inline">
          <div class="form-group">
            <input type="text" class="form-control" v-model="textToTranslate" placeholder="输入需要翻译的内容">
          </div>
          <div class="form-group">
            <select v-model="language" class="form-control">
              <option value="en">English</option>
              <option value="ru">Russian</option>
              <option value="ko">korean</option>
              <option value="ja">Japanese</option>
              <option value="zh">中文</option>
            </select>
          </div>
          <input type="submit" class="btn btn-info" value="翻译">
        </form>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "translateForm",
      data(){
        return{
          textToTranslate:"",
          language:""
        }
      },
      methods:{
        formSubmit:function (e) {
          if(this.textToTranslate==""){
            alert("记得填写内容呀！")
          };
          this.$emit("formSubmit",this.textToTranslate,this.language);
          e.preventDefault();
        }
      },
      created:function () {
        this.language='en'
      }
    }
</script>

<style scoped>
.container{
  border: 2px solid #888;
  border-radius: 10px;
  padding: 10px 0;
}
</style>
