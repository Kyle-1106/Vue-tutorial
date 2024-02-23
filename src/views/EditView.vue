<template>
 {{ memo.title }}
</template>

<script>
export default {
  name: "EditView",
  computed: {
    memo() {
      const id = parseInt(this.$route.params.id);
      return this.$store.getters.getMemoById(id)
      // ここで計算された結果を返す
    }
  }
}

</script>