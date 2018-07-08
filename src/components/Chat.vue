<template>
<div class="wrapper">
    <div class="container">
        <div class="left">
            <div class="top">
                <input type="text" />
                <a href="javascript:;" class="search"></a>
            </div>
            <ul class="people">
                <li class="person active">
                    <!--<img :src="require('./assets/img/profile.jpg')" alt="" />-->
                    <span class="name">Thomas Bangalter</span>
                    <span class="time">2:09 PM</span>
                    <span class="preview">I was wondering...</span>
                </li>
            </ul>
        </div>
        <div class="right">
            <div class="top">
                <span>To:
                    <span class="name">Thomas Bangalter</span>
                </span>
            </div>
            <div class="chat active-chat">
                <div
                class="bubble me"
                v-for="(message, index) in messages"
                :key="index">
                    {{ message.text }}
                </div>
            </div>
            <div class="write">
                <a href="javascript:;" class="write-link attach"></a>
                <input type="text" placeholder="Your message here"  autocomplete="off" v-model="new_message" class="js-focus" @keypress.enter="pushMessage()"/>
                <a href="javascript:;" class="write-link smiley"></a>
                <a @click="pushMessage()" class="write-link send"></a>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      new_message: '',
      messages: [ { text: 'Hello', sender: 'me' }, { text: 'How are you?', sender: 'me' } ]
    }
  },
  methods: {
    pushMessage () {
      if (this.new_message.trim().length > 0) {
        this.messages.push({text: this.new_message, sender: 'me'})
      }
      this.new_message = ''
      document.querySelector('.js-focus').focus()
    }
  }
}
</script>

<style scoped>
</style>
