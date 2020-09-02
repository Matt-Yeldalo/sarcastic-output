<template>
<div>
<div class="flex mb-4 content-center">
  <img src="../assets/sponge.jpg" alt="Spongebob">
</div>
<div class="w-full mx-auto max-w-md">
  <form @submit.prevent="" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="input">
        Enter text
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="input" @input="computeText" v-model="input" type="text">
    </div>
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
        Sarcastic output
      </label>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" v-model="output" id="output" type="text">
    </div>
    <div class="flex items-center justify-between">
      <button @click="copyText" class="bg-blue-500 hover:bg-blue-700 text-white font-bold mb-8 py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Copy
      </button>
    </div>
    <p>{{msg}}</p>
  </form>
</div>
</div>
</template>
<script>
export default {
  name: "Input",
  data(){
    return{
      input:"",
      output:"",
      msg:""
    }
  },
  methods:{
    computeText(){
      let inputArray = this.input.split("");
      this.output = this.stringBuilder(inputArray);
    },
    stringBuilder(inputArray){
      let caps = false;
      let result = "";
      for (let i = 0; i < inputArray.length; i++){
        if (caps){
          result += inputArray[i].toUpperCase();
        }else{
          result += inputArray[i];
        }
        caps = !caps;
      }
      return result;
    },
    copyText(){
      let text = document.getElementById("output");
      text.select();      
      document.execCommand("copy");
      this.msg = "Text copied to clipboard"
      console.log("FUCK OFF");
    }
  }
}
</script>
<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
img{
  margin: auto;
}

</style>