<template>
  <div class="layout">
    <div class = "layout-header">
      <div class="layout-header-menu-handle" @click="toggleMenu">
        <icon v-if="$store.state.ui.menu" name="times"/>
        <icon v-else name="bars"/>
      </div>
    </div>
    <transition name="slide-left">
      <div class="layout-menu" v-show="$store.state.ui.menu">
        <navigation/>
      </div>
    </transition>
    <div class="layout-content">
      <nuxt />
    </div>
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import { mapMutations } from 'vuex'

export default {
  data() {
      return {

      }
  },

  methods: {
        ...mapMutations({
            toggleMenu: 'ui/toggleMenu',
        })
  },

  components: {
    'navigation' : Navigation
  }
}

</script>

<style>
.layout-header {
  background-color: #122035;
  position: fixed; right: 0; top: 0; left: 0; height: 64px;
}

.layout-content {
  background-color: #F7F7F7;
  position: fixed; right: 0; left: 0; top: 64px; bottom: 0;
}



.layout-menu {
  background-color: #122035; z-index: 10;
  position: fixed; right: 0; left: 0; top: 64px; bottom: 0;
}

.layout-header-menu-handle {
    color: #F7F7F7;
    width:       64px;
    height:      64px;
    line-height: 64px;
    text-align:  center;
}


</style>
