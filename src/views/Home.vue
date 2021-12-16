<template>
  <b-container class="home-container fade-in">
    <Card :person="cards[0]" />
  </b-container>
</template>

<script>
import Card from "@/components/Card.vue";

const response = [
  {
    name: "Manuel Rodriguez",
    position: "Director Asociado",
    company: "Enmedio Asociados",
    description:
      "Description Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repudiandae, culpa.",
    site: "www.enmedioasociados.com",
    email: "manuel@enmedioasociados.com",
    whatsapp: "+52 871 118 8750",
    phones: ["+52 871 793 0230", "+52 871 793 0231"],
    facebook: "#",
    twitter: "#",
    instagram: "#",
  },
];

export default {
  name: "Home",
  components: {
    Card,
  },
  data() {
    return {
      cards: response,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/variables.scss";
@import "@/assets/scss/mixins.scss";
@import "@/assets/scss/style.scss";

.home-container {
  min-height: 100vh;
  padding: 0;
}
</style>
