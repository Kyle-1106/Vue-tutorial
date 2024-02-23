
<!-- ここでフォームを定義 -->
<!-- ここでHTMLを定義 -->
<template>
  <h2>New</h2>
  <!-- v-modelで双方向バインディングを定義して、入力値とtitleとcontentをバインディング -->
<div><input type="text" v-model="title"></div>
<div><textarea v-model="content"></textarea></div>
<div class="center">
  <!-- saveメソッドと紐付け -->
  <button @click="save">保存</button>
</div>
</template>


<!-- ここからはロジック部分 -->
<script>
// MemoFormという名前でexportできるように設定
export default {
  name: "MemoForm",
  //オブジェクトを返すdataメソッドを定義 コンポーネント初期化時に実行される
  //ngOnInitみたいなもの
  data(){
    return{
      title:"",
      content:"",
    }
  },
  //メソッドを定義
  methods:{
    save(){
      let memo={
        //titleやcontentはdataメソッド内で定義しているのでthisde呼び出せる
        title:this.title,
        content:this.content,
      }
      //this.$storeと宣言すればVuexのストアにアクセスできる
      //ここではsaveという名前のmutationにmemoをコミットする
      this.$store.commit("save",memo)
      //画面遷移
      this.$router.push("/")
    }
  }
}
</script>



<style scoped>
div{
  margin-bottom: 10px;
}
input[type=text]{
  width: 100%;
}
textarea{
  width: 100%;
  height: 30em;
}
button{
  width: 5em;
  margin: 3px;
}
.center{
  text-align: center;
}
</style>