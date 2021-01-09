<template>
  <div class="layout night">
    <div id="canvas" ref="layout"></div>
    <header class="header">
      <nav class="nav">
        <a href="#me">About Me</a>
        <a href="#more">Experience</a>
        <a href="#contact">Contact me</a>
      </nav>
    </header>

    <div class="content">
      <slot/>
    </div>
  </div>
</template>

<script type="text/javascript">
  import * as THREE from 'three';
  export default {
    mounted () {
      var scene, camera, renderer;
      var speed = 5, iscroll = false;
      var shape = [];
      var ref = this.$refs.layout

      function init () {
        scene = new THREE.Scene();
        camera = new THREE.PerspectiveCamera(105,window.innerWidth/window.innerHeight, 1,5000);
        camera.position.z = 2000;

        renderer = new THREE.WebGLRenderer({alpha:true});
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.shadowMap.enabled = true;
        renderer.shadowMap.type = THREE.PCFSoftShadowMap;
        renderer.setClearColor( 0xffffff, 0);
        renderer.shadowMapSoft = true;
        renderer.autoClear = false;
        ref.appendChild(renderer.domElement); 

        window.addEventListener("resize", function (argument) {
          camera.aspect = window.innerWidth / window.innerHeight;
          camera.updateProjectionMatrix();
          renderer.setSize( window.innerWidth, window.innerHeight );
        })

        var isScrolling;
        window.addEventListener("scroll", function (argument) {
          iscroll = true
          window.clearTimeout( isScrolling );
          isScrolling = setTimeout(function() {
            iscroll = false
          }, 66);

        })

      }

      function render() {
        requestAnimationFrame(render);
        renderer.render(scene, camera);
        for(var x = 0; x< shape.length;x++) {
          if (!iscroll) {
            shape[x].position.z -= 5
          } else {
            shape[x].position.z -= 50
          }

          if(shape[x].position.z < -1000) {
            shape[x].position.z = getRandomArbitrary(0,2000)
          }
        }
      }

      function createSpotlights() {

        var sp = [];
        var helper = [];

        var spProps = [
          [0xfc6bcf , 1, 2000,128,0],
          [0x6bd6ff , 1, 2000,120,0,1],
          [0x6bd6ff , 1, 2000,100,0,1],
          [0x6bd6ff , 0.8, 2500,128,0,1]
        ]
        var spPos = [
          [0,800,800],
          [700,1000,1000],
          [700,1000,-1000],
          [0,-1300, 1200]
        ]

        for(var x = 0;x < spPos.length; x++) {
          // === spotlight
          sp[x] = new THREE.SpotLight(...spProps[x]);
          sp[x].position.set(...spPos[x])
          sp[x].castShadow = true;
          scene.add(sp[x]);
          sp[x].shadow.mapSize.width = 1024;
          sp[x].shadow.mapSize.height = 1024
        }
      }

      function randomStars() {
        var material;

        var rs = [];

        var pos = {
          x : 0,
          y : 0,
          z : 0
        }
        var color = "#86d7dc";

        for(var x = 0; x < 30; x++) {
          material = new THREE.MeshPhongMaterial({
            color      : new THREE.Color("#fff"),
            emissive   : new THREE.Color("#fff"),
            shininess  : new THREE.Color("#fff"),
            shininess  :  100,
            shading    :  THREE.FlatShading,
          });
          if(x %2 == 0) {
            material.emissive = new THREE.Color(color);
          }

          pos.x = getRandomArbitrary((window.innerWidth+500) * (-1),window.innerWidth+500);
          pos.y = getRandomArbitrary((window.innerHeight+1000) * (-1),window.innerHeight+1000);
          pos.z = getRandomArbitrary(-1000,1000);

          rs[x] = new THREE.SphereGeometry(getRandomArbitrary(2, 10), 10, 10 );
          shape[x] = new THREE.Mesh(rs[x], material);
          shape[x].castShadow = true;
          shape[x].position.set(pos.x,pos.y,pos.z);
          scene.add(shape[x])
        }
      }

      function getRandomArbitrary(min, max) {
        return Math.random() * (max - min) + min;
      }

      init();
      createSpotlights();
      randomStars();
      render();
    }
  }
</script>

<style lang="scss">
$bgcolor: #13151f;
$fontcolor: #fff;
* {
  box-sizing: border-box;
  transition: all 0.4s ease;
  scroll-behavior: smooth;
}

html {
  height: 100%
}
body {
  padding: 0;
  margin: 0;
  font-family: 'Merriweather', serif;
  font-size: 12px;
  background: $bgcolor;
  color: $fontcolor;
  height: 100%;
}

#canvas {
  z-index: -1;
  width: 100%;
  left: 0;
  position: fixed;
  opacity: 1
}

.layout {
  max-width: 1200px;
  display: flex;
  margin: auto;
  flex-direction: column;
}

.header {
  width: 100%;
  display: flex;
  justify-content: center;
  padding: 2rem;
  align-items: center;
  flex-direction: column;
  margin: auto;
  height: 100px;
  left: 0;
  position: fixed;
  background: #13151f;
  z-index: 2;
  .logo {
    margin: 1rem;
    font-size: 60px;
    font-weight: 900;
    text-align: center;
  }
}

.content { 
  @media only screen and (min-width: 600px) {
    display: flex;
    flex-direction: column
  }
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-around;
  a {
    color: $fontcolor;
    text-decoration: none;
    position: relative;
    letter-spacing: 2px;
    font-weight: 400;
    margin:  0 0.5rem;
    position: relative;
    &:before {
      content: '';
      position: absolute;
      right: -5px;
      height: 100%;
      width: 1px;
      background: rgba(255, 255, 255, 0.4);
    }
    &:hover { font-weight: 900 }
    &:nth-last-child(1) {
      &:before { display: none }
    }
  }
}
</style>
