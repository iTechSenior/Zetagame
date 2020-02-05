<template>
  <v-content>
    <div>
      <v-fade-transition mode="out-in">
        <router-view style="background-color: #161616;" />
      </v-fade-transition>
    </div>
  </v-content>
</template>

<script>
export default {
  metaInfo() {
    return {
      title: 'Bahiscup'
    }
  }
}
</script>

<style>
/* #core-view {
  padding-bottom: 100px;
} */
</style>
