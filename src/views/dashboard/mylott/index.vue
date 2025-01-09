<template>
    <div  id="lottid">
    </div>
</template>

<script>
import lottie from 'lottie-web';
import animationData from '@/assets/404_images/json/animation_llg0kjap.json';
export default{
    name:'mylott',
    mounted() {
    this.initLottieAnimation();
  },
  methods: {
    initLottieAnimation() {
      const animationContainer = document.getElementById('lottid');
      const animationOptions = {
        container: animationContainer,
        animationData: animationData,
        loop: true,
        autoplay: true,
      };

      this.animationInstance = lottie.loadAnimation(animationOptions);
    }
  }
}
</script>

<style>

</style>