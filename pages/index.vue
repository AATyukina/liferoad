<template>
  <div class="wrapper">
    <topmenu />
    <footer>
      <Downfooter />
    </footer>
  </div>
</template>

<script>
import Topmenu from '~/components/Topmenu.vue'
import Downfooter  from '~/components/Downfooter.vue'

export default {
  components: {
    Topmenu,
    Downfooter
  }
}
</script>