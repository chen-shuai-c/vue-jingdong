<template>
  <div class="wraaper">
    <StaticPart />
    <Nearby />
  </div>
  <Docker/>
</template>

<script>
import StaticPart from './StaticPart.vue'
import Nearby from './Nearby.vue'
import Docker from './Docker.vue'
export default {
  name: 'Home',
  components: {
    StaticPart,
    Nearby,
    Docker
    }
  }
</script>

<style lang="scss" scoped>
.wraaper{
  overflow-y: auto;
  position: absolute;
  left: 0;
  top: 0;
  bottom: .5rem;
  right: 0;
  padding: 0 .18rem .1rem .18rem;
}

</style>
