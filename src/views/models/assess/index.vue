<template>
    <div id="assess"></div>
</template>

<script>
import lottie from 'lottie-web';
import animationData from '@/assets/404_images/json/animation_llki0mzg.json';
export default{
    name:'aiTrain',
    mounted() {
    this.initLottieAnimation();
  },
  methods: {
    initLottieAnimation() {
      const animationContainer = document.getElementById('assess');
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