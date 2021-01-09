<template>
	<section id="me">
    <div class="content">
      <h1> Hi, <span> I'm <i> Marjo </i></span></h1>
      <h2> Web Developer </h2>
      <p> I'm a web developer that can do front-end and backend web development.<br>
        Full-Stack in short. <br>
        I'm passionate , and I love coding. <br>
      </p>
      <a href="#more"><button></button></a>
    </div>
    <div class="content">
      <tag content="me" cls="parent">
        <tag content="name" cls="tabbed">Marjo S. Alinsug</tag>
        <tag content="age" cls="tabbed">26</tag>
        <tag content="ul" cls="parent tabbed">
          <tag content="li" cls="tabbed">Nodejs</tag>  
          <tag content="li" cls="tabbed">PHP</tag>  
          <tag content="li" cls="tabbed">Javascript</tag>  
          <tag content="li" cls="tabbed">MySQL</tag>  
          <tag content="li" cls="tabbed">MongoDB</tag>  
          <tag content="li" cls="tabbed">HTML5</tag>  
          <tag content="li" cls="tabbed">CSS</tag>  
        </tag>
      </tag>
    </div>
  </section>
</template>

<script type="text/javascript">
import Tag from '~/components/Tag.vue'

export default {
  components: { Tag }
}

</script>

<style type="text/css" lang="scss" scoped>
section {
  width: 100%;
  min-height: calc(100vh);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem 2rem;
  padding-top: 110px;
  justify-content: center;

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
    div { width: auto; }
  }
}

.content:nth-child(1) {
  font-family: 'Work Sans', 'sans-serif';
  text-align: left;

  i { font-style: normal; color: #86d7dc;  }
  h1 { text-transform: uppercase; font-size: 30px; margin: 0 }
  h2 { font-size: 20px; margin: 0 }
  p { font-weight: 100; font-size: 12px; letter-spacing: 2px; line-height: 24px }

  @media only screen and (min-width: 600px) {
    i { font-style: normal; color: #86d7dc;  }
    h1 { text-transform: uppercase; font-size: 50px; margin: 0 }
    h2 { font-size: 30px; margin: 0 }
    p { font-weight: 100; font-size: 13px; letter-spacing: 2px; line-height: 24px }
  }
}
.content:nth-child(2) {
  color: #7ecc97;
  padding: 1rem 2rem;
  background: rgba(43, 46, 62, 0.14);
}
button {
  border: 0;
  background: #ff4f7f;
  color: #fff;
  text-transform: uppercase;
  font-size: 12px;
  letter-spacing: 2px;
  position: relative;
  min-height: 30px;
  width: 120px;
  transition: all 0.3s ease;
  &:focus { outline: none; }
  &:after {
    content: 'LEARN MORE';
    position: absolute;
    left: 20%;
    top: 8px;
    width: 100%;
  }
  &:hover {
    cursor: pointer;
    background: #e44570;
    &:after {
      left: 60%;
      transition: all 0.2s ease
    }
  }
}
</style>