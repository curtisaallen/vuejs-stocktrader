<template>
  <div>
  <app-header></app-header>
  <div class="container">
    <div class="row">
       <div class="col-md-12">
         <transition name="slide" mode="out-in">
           <router-view></router-view>
         </transition>
      </div>
     </div>
  </div>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Header from './components/Header'

export default {
  name: 'app',
  components: {
    appHeader: Header
  },
  created() {
    this.$store.dispatch('initsetStocks');
  }
}
</script>

<style>
  .slide-enter-active {
      animation: slide-in 200ms ease-out forwards;
  }
  .slide-leave-active {
      animation: slide-out 200ms ease-out forwards;
  }
  @keyframes slide-in {
    from {
      transform: translateY(-30px);
      opacity: 0;
    }
    to {
          transform: translateY(0);
          opacity: 1;
    }
  }
    @keyframes slide-out {
      from {
        transform: translateY(0);
        opacity: 1;
      }
      to {
            transform: translateY(-30px);
            opacity: 0;
      }
    }
</style>
