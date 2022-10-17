<template>
  <div class="contain-button-reset">
    <button class="button-reset" @click="$emit('ButtonReset')">RESET</button>
  </div>
</template>

<script>
export default {
    name:'ButtonReset',
}
</script>



<style>
.button-reset {
  display: inline-block;
  padding: .75rem 1.25rem;
  border-radius: 10rem;
  color: #fff;
  text-transform: uppercase;
  font-size: 1rem;
  letter-spacing: .15rem;
  transition: all .3s;
  position: relative;
  overflow: hidden;
  z-index: 1;
}
.button-reset:after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: red;
    border-radius: 10rem;
    z-index: -2;
}
  
.button-reset:before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0%;
    height: 100%;
    background-color: nlue;
    transition: all .3s;
    border-radius: 10rem;
    z-index: -1;
}
.button-reset:hover {
    color: #fff;
}
.button-reset:before {
      width: 100%;
}



    
</style>