<template>
	<section id="more">
    <div class="content">
      <mini-me></mini-me>
      <a href="#contact"><button></button></a>
    </div>
    <div class="content"> 
      <div class="heading">
        <span>Experience</span>
      </div>
      <h2> Bluefrog 2014-2018 </h2>
      <p>
        Customizing and implemting multiple web applications with complex user interfaces as per clients' requirements. Implementing and developing HTML5 casino games licensed under PAGCOR PH.
      </p>
      <div class="stack-description--container">
        <label> Stack </label>
        <ul>
          <li>VueJs</li>
          <li>AngularJs</li>
          <li>Laravel</li>
          <li>CreateJs</li>
          <li>HTML5 Canvas</li>
          <li>PHP</li>
          <li>MySQL</li>
        </ul>
      </div>
      

      <h2> Cubic Solutions 2018-2019 </h2>
      <p>
        Customizing and implmenting multiple web applications with complex user interfaces as per clients' requirements. Creating administrative panels to control Client side operations of web applications. Designing and implmenting Database Structure.
      </p>
      <div class="stack-description--container">
        <label> Stack </label>
        <ul>
          <li>VueJs</li>
          <li>NodeJs</li>
          <li>KnexJs</li>
          <li>MySQL</li>
        </ul>
      </div>

      <h2> Compare Club 2019-present </h2>
      <p>
        Maintaining and implementing features of existing API. Developing new user interfaces to integrate to existing web applications.
      </p>
      <div class="stack-description--container">
        <label> Stack </label>
        <ul>
          <li>Symfony</li>
          <li>PHP</li>
          <li>Javascript</li>
          <li>ReactJS</li>
          <li>VueJS</li>
          <li>Gridsome</li>
          <li>MySQL</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script type="text/javascript">
import MiniMe from '~/components/MiniMe.vue'

export default {
  components: { MiniMe }
}
</script>

<style type="text/css" lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@100;300;400;600;700&display=swap');
section {
  width: 100%;
  min-height: calc(100vh);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem 2rem;
  padding-top: 110px;
  font-family: 'Work Sans', 'sans-serif';

  div {
    width: 100%;
    margin: 1rem 0;
  }

  @media only screen and (min-width: 600px) {
    padding: 1rem 4rem;
    display: flex;
    flex-direction: row;
    min-height: calc(100vh);
    align-items: center;
    justify-content: center;
    display: flex;
    div { width: auto; }
  }
}

.heading {
  position: relative;
  text-transform: uppercase;
  font-weight: 300;
  margin: 0;
  z-index: 1;
  font-size: 20px;
  color: #fff;
  margin-bottom: 2rem;
  span {
    color: #fff;
    position: relative;
    margin-top: 10px;
  }
}

.content {
  margin-top: 2rem;
  width: 100%;
  line-height: 20px;
  font-weight: 300;
  font-size: 12px;
  letter-spacing: 2px;
  position: relative;
  &:nth-child(1) {
    width: 100%;
    margin: 0;
    min-height: 200px;
    @media only screen and (min-width: 600px) {
      width: 30%;
      min-height: 120px;
    }
  }
}

.stack-description--container {
  margin:0;
  padding-bottom: 2rem;
  position: relative;

  &:after {
    content: '';
    position: absolute;
    width: 80%;
    height: 1px;
    background: rgba(255, 255, 255, 0.2);
    bottom: 0;
    left: 0; 
    right: 0;
    margin: auto;
  }
  &:nth-last-child(1) {
    &:after {
      display: none;
    }
  }
  label {
    border-radius: 10px;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 10px;
  }
  ul li { list-style: none; }
  ul {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding: 0;
    margin: 0;
    flex-wrap: wrap
  }
  li {
    margin: 0 0.2rem;
    // background: rgba(255, 255, 255, 0.1);
    color: #fff;
    padding: 0 0.2rem;
    font-size: 8px;
    font-weight: 700;
    position: relative;
    &:before {
      content :'';
      position: absolute;
      width: 1px;
      height: 80%;
      right: -0.1rem;
      margin: auto;
      background: rgba(255, 255, 255, 0.2);
      bottom: 0;
      top: 0;
      margin: auto;
    }
    &:nth-last-child(1) {
      &:before { display: none }
    }
  }
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
  width: 120px;
  position: absolute;
  left: 0; right: 0;
  margin: auto;
  transition: all 0.3s ease;
  bottom: 0;
  &:focus { outline: none; }
  &:after {
    content: 'CONTACT ME';
    position: absolute;
    left: 20%;
    top: 8px;
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

  @media only screen and (min-width: 600px) {
    bottom: -50px;
  }
}
</style>