<template lang="html">
  <div class="chat-composer">
    <input type="text" placeholder="Masukkan teks . . ." v-model="messageText" v-on:keyup.enter="sendMessage">
    <button type="button" class="btn btn-primary" @click="sendMessage">send</button>
  </div>

</template>

<script>
  export default{
    data(){
      return{
        messageText: ''
      }
    },
    methods:{
      sendMessage(){
        this.$emit('messagesent', {
          message :this.messageText,
          user    :{
                  name : $('.navbar-right .dropdown-toggle').text()
          }
        });
        // console.log(this.messageText)
        this.messageText=''
      }
    }
  }
</script>

<style lang="css" media="screen">
.chat-composer{
  display: flex;
}

.chat-composer input{
  flex: 1 auto;
}
.chat-composer button{
  border-radius: 0px;
}
</style>
