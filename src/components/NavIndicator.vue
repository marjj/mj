<template>
  <div>
    <ul ref="navs">
      <a href="#me"  class="active" :class="{ 'active' : me, 'test': more }"><li></li></a>
      <a href="#more" :class="{ 'active' : more, 'test': contact }"><li></li></a>
      <a href="#contact" :class="{ 'active' : contact }"><li></li></a>
    </ul>
  </div>
</template>
<script>
export default {
  mounted () {
    let isScrolling = null
    window.addEventListener('scroll', (e) => {
      localStorage.setItem('scrollY', window.pageYOffset)
      this.isScroll = true;
      this.checkActive()
      
      window.clearTimeout( isScrolling );
      isScrolling = setTimeout(() => {
        this.isScroll = false
        this.checkActive()
      }, 66);
    })
  },
  
  data () {
    return {
      me: false,
      more: false, 
      contact: false,
      isScroll: false
    }
  },
  
  methods: {
    checkActive (hash) {
      let scrollY = 0
      
      if (localStorage.scrollY) {
        scrollY = parseInt(localStorage.scrollY)
      }

      if (0 == scrollY) {
        this.me = true
        this.more = false
        this.contact = false
      }
      if (scrollY >= window.innerHeight && scrollY <= window.innerHeight + (window.innerHeight/4) ) {
        this.me = true
        this.more = true
        this.contact = false
      }
      
      if (scrollY >= window.innerHeight * 2 ) {
        this.me = true
        this.more = true
        this.contact = true
      }
    }
  }
}
</script>
<style lang="scss" scoped>
@font-face {
  font-family: 'icomoon';
  src: url('../assets/fonts/icomoon.ttf');
  font-weight: normal;
}

@font-face {
  font-family: 'icomoon2';
  src: url('../assets/fonts/icomoon2.ttf');
  font-weight: normal;
}
$navw: 14px;
div {
  position: fixed;
  height: 10rem;
  left: 1rem;
  bottom: 0; top: 0;
  margin: auto;
  top: 150px;
  font-family: 'icomoon2';
}

ul {
  margin: 0;
  padding: 0;
  height: 100%;
}

li { 
  width: $navw;
  height: $navw;
  border-radius: 100%;
  border: 1px solid rgba(255, 255, 255, 0.2);
  list-style: none;
  position: relative;
  margin-bottom: 31px;
  &:hover {
    cursor: pointer;
    transition: background 0.2s ease;
    border-color: #fff;
    &:after {
      content: '\e907';
      position: absolute;
      font-size: 1.5rem;
      color: #fff;
      left: -4px;
      top: -4px
    }
  }
}

a {
  position:relative;
  width: $navw;
  display: block;
  margin: 0;
  &:not(:nth-last-child(1)) {
    &:before, &:after {
      content: '';
      position: absolute;
      width: 1px;
      background: rgba(255, 255, 255, 0.2);
      height: 31px;
      left: 0;
      right: 0;
      margin: auto;
      top: $navw;
    }
    
    &:after {
      transform: scaleY(0);
      -webkit-transform-origin-y: top;
      background: rgba(255, 255, 255, 1);
      transition: all 0.2s ease;
    }
  }
  
  &.test:after {
    transform: scaleY(1);
  }
  
  &.active {
    transition: background 0.2s ease;
    li {
      border: 0;
      &:after {
        content: '\e900';
        position: absolute;
        font-size: 1.5rem;
        color: #fff;
        left: -4px;
        top: -4px
      }
    }
  }

  // &:hover:nth-child(1),
  &.active:nth-child(1) {
    li {
      &:after {
        content: '\e901';
      }
    }
  }
  // &:hover:nth-child(2),
  &.active:nth-child(2) {
    li {
      &:after {
        content: '\e902';
        font-size: 16px;
        left: 0;
        top: 0
      }
    }
  }
  // &:hover:nth-child(3),
  &.active:nth-child(3) {
    li {
      &:after {
        content: '\e900';
        font-size: 18px;
        left: -2px
      }
    }
  }
}
</style> 