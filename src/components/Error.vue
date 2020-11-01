<template>
  <div class='err-text'>
    <slot></slot>
  </div>
</template>

<script>
export default{
name:"Error"
}
</script>


<style>
  .err-text{
    color:red
  }
</style>