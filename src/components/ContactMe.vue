<template>
	<section id="contact">
    <div class="content" :class="{ 'success': showSuccess }">
      <div class="loading" v-if="showLoading">
        <h1> sending... </h1>
      </div>
      <div class="form-wrap"  v-if="!showSuccess && !showLoading">
        <div>
          <label> Name </label>
          <input v-model="name">
        </div>
        <div>
          <label> Email </label>
          <input v-model="email" required>
        </div>
        <div>
          <label> Message </label>
          <textarea v-model="message" required></textarea>
        </div>
        <button @click="sendMessage"></button>
      </div>
      <div v-if="showSuccess && !showLoading">
        <h1> SENT </h1>
        <h2> Hi, thanks for reaching out! </h2>
        <p> I will reply as soon as I read your email! </p>
      </div>
    </div>

    <div class="content">
      <ul>
        <a href="https://www.linkedin.com/in/marjo-sobrecaray-2844a6ba/" target="_blank">
          <li><i class="icons linkedin"> </i> <span>LinkedIn</span> </li>
        </a>
        <a href="https://github.com/marjj" target="_blank">
          <li><i class="icons github"> </i> <span>Github</span></li>
        </a>
        <a href="https://codepen.io/maaarj" target="_blank">
          <li><i class="icons codepen"> </i><span>Codepen</span></li>
        </a>
        <a href="mailto:marjo.sobrecaray@gmail.com" target="_blank">
          <li><i class="icons gmail"> </i><span>Mail</span></li>
        </a>
      </ul>
    </div>
  </section>
</template>

<script type="text/javascript">
import { init, send } from 'emailjs-com';
export default {
  data () {
    return {
      name: '',
      email: '',
      message: '',

      showSuccess: false,
      showLoading: false
    }
  },

  created () {
    init("user_Sn9emjhtuOPjSjTEMo2bS")
  },

  methods: {
    async sendMessage() {
      let templateParams = {
          to_name: 'Marjo',
          from_name: this.name,
          message: this.message,
          reply_to: this.email
      };

      try {
        this.showLoading = true
        let response = await send('service_qfe3b08', 'template_niponlq', templateParams)
        console.log(response.status)
        if (response.status === 200 ) {
          this.showSuccess = true
        } 
        this.showLoading = false
      } catch (err) {
        console.log(err.message)
      }
    }
  }
}

</script>
<style type="text/css" lang="scss" scoped>
@font-face {
  font-family: 'icomoon';
  src: url('../assets/fonts/icomoon.ttf');
  font-weight: normal;
}

section {
  width: 100%;
  min-height: calc(100vh);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem 2rem;
  padding-top: 110px;
  justify-content: center;
  font-family: 'Work Sans', sans-serif;
  div {
    width: 100%;
    margin: 1rem 0;
  }

  @media only screen and (min-width: 600px) {
    padding: 1rem 4rem;
    display: flex;
    flex-direction: row;
    min-height: calc(100vh);
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding-top: 110px;
  }
}
.content.success {
  text-align: center;
  position: relative;
  &:before {
    content: '\e900';
    font-family: 'icomoon';
    position: absolute;
    font-size: 5rem;
    width: 100px;
    left: 0;
    right: 0;
    margin: auto;
    margin-top: -5rem;
  }
}

.content {
  width: 100%;

  &:nth-child(2) {
    text-align: center;
    justify-content: center;
    align-items: center;
    ul, li {
      list-style: none;
      padding: 0;
    }
    li {
      margin: 1rem 0
    }
  }
  @media only screen and (min-width: 600px) {
    width: 50%;
  }
}


label {
  font-weight: 300;
  letter-spacing: 1px;
  margin-bottom:1rem;
  display: block;
}
input, textarea {
  width: 100%;
  background: rgba(17, 19,27, 0.7);
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 0.5rem;
  color: #fff;
  &:focus {
    outline: none;
    border: 1px solid rgba(255, 255, 255, 0.4);
  }
}

textarea {
  min-height: 6rem
}

button {
  border: 0;
  background: #469196;
  color: #fff;
  text-transform: uppercase;
  font-size: 12px;
  letter-spacing: 2px;
  position: relative;
  min-height: 30px;
  width: 80px;
  transition: all 0.3s ease;
  &:focus { outline: none; }
  &:after {
    font-family: 'icomoon', 'Work Sans', sans-serif;
    content: "Send \e901";
    position: absolute;
    left: 20%;
    top: 0px;
    line-height: 30px;
    width: 100%;
  }
  &:hover {
    cursor: pointer;
    background: #276569;
    &:after {
      left: 60%;
      transition: all 0.2s ease
    }
  }
}

a { color: #fff }
li {
  text-align: center;
  @media only screen and (min-width: 600px) {
    text-align: left;
  }
}

.icons {
  text-transform: none;
  font-style: normal;
  width: 20px;
  height: 20px;
  display: inline-block;
  font-family: 'icomoon';
  color:#fff;
  position:relative;
  font-size: 1.5rem;
  &:before {
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto;
    left: 0
  }
  & + span {
    padding-left: 1.5rem;
    line-height: 1.5rem;
    display: none;
    @media only screen and (min-width: 600px) {
      display: inline-block
    }
  }
}
.linkedin {
  &:before {
    content: '\e906';
  }
}
.github {
  &:before {
    content: '\e903';
  }
}
.codepen {
  &:before {
    content: '\e905';
  }
}
.gmail {
  &:before {
    content: '\e902';
  }
}

</style>