<template>
  <div class = "message">
   <p> Message component - {{ message }} </p>
  </div>
</template>

<script>


export default {
  props: {
    message: {
      tyepe: String,
      require: true
    }
  }
}
</script>
