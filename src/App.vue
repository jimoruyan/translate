<template>
  <div id="app">
  	<h1>在线翻译</h1>
  	<h5 class="text-muted">简单 / 易用 / 便捷</h5>
	<translateForm v-on:formSubmit="translateText"></translateForm>
	<translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>
<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function(){
  	return{
  		translatedText:""
  	}
  },
  components:{
  	TranslateForm,TranslateOutput
  },
  methods:{
  	translateText:function(text,language){
  		// alert(text);
  		this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180516T121012Z.cbcdef348ca70ff1.ba70c4931e8c29b7a2d2463e77665b67430d1cfa&lang='+language+'&text='+text)
  		.then((response)=>{
  			// console.log(response.body.text[0]);
  			this.translatedText=response.body.text[0];
  		})
  	}
  }
}
</script>

<style>
	#app{
		font-family:'Avenir',Helvetica,Arial,sans-serif;
		-webkit-font-smoothing:antialiased;
		-moz-osz-font-smoothing:grayscale;
		text-align:center;
		color:#2c3e50;
		margin-top:60px;
	}
</style>
