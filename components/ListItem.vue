<template>
  <li>
    <ul>
      {{
        data
      }}
    </ul>
  </li>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    data: {
      type: String,
      require: true,
    },
  },
}
</script>

<style></style>
