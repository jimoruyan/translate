<template>
  <div class="row" id="translateForm">
			<form id="transForm" class="well form-inline"  v-on:submit="formSubmit">
				<input class="form-control" type="text" v-model="textToTranslate" placeholder="请输入需要翻译的内容">
				<select class="form-control" v-model="language">
					<option value="en" selected>English</option>
					<option value="zh">Chinese</option>
					<option value="ko">Korean</option>
					<option value="ja">Japanese</option>
					<option value="ru">Russian</option>
				</select>
				<input class="btn btn-primary" type="submit" value="翻译">
			</form>
  </div>

</template>

<script>

export default {
  name: 'translateForm',
  data:function(){
  	return{
  		textToTranslate:"",
  		language:""
  	}
  },
  methods:{
  	formSubmit:function(e){
  		// alert(this.textToTranslate);
  		this.$emit("formSubmit",this.textToTranslate,this.language);
  		e.preventDefault();

  	}
  },
  created:function(){
  	this.language="en";
  }
}
</script>

<style>
  #transForm{
    margin: 0 auto;
  }
</style>
