<template>
  <div>
    Main Page
  </div>
</template>

<script>
  export default {
    name: 'IndexPage',
    created() {
      this.$router.push('/administrator')
    }
  }
</script>
