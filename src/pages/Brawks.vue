<template>
  <section class="brawksRoot">
    <div class="inner">
      <Breadcrumbs name="Brawks" project="Projet 1" url="/" />
      <p>
        Compteur en temps reel realise pour l'emission LaGrosseGame by Cdiscount
        pour le streamer Brawks.
      </p>
      <Counter />
    </div>
  </section>
</template>

<script>
import Breadcrumbs from "../components/Breadcrumbs.vue";
import Counter from "./Brawks/Counter.vue";
export default {
  components: { Breadcrumbs, Counter },
  name: "Brawks",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.brawksRoot {
  padding-top: 64px;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  @media screen and (min-width: 1024px) {
    flex-direction: row;
    padding-top: 0px;
  }
}
</style>
