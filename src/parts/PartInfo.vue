<template>
  <div>
    <h1>{{part.title}}</h1>
    <div>{{part.description}}</div>
  </div>
</template>
<script>
  export default {
    name: 'PartInfo',
    created() {
      this.$store.dispatch('getParts')
    },
    props: {
      partType: {
        type: String
      },
      id: {
        type: [Number, String],
        validator(value) {
          return Number.isInteger(Number(value));
        },
      },
    },
    computed: {
      part() {
        const {
          partType,
          id
        } = this;
        return this.$store.state.parts[partType].find((part) => part.id === +id);
      },
    },
  };
</script>