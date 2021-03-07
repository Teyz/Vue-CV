<template>
  <div class="hiddenAboutRoot">
    <div class="hiddenAboutMessage">
      <p>
        Et si on en discute tranquillement autour d'un cafe ?
      </p>
      <a href="/#contact" class="btn btn-primary">Contact</a>
    </div>
    <div class="hiddenAboutMain">
      <TextSection
        title="Qui suis-je"
        text="Je te felicite pour ta perceverance ! Je savais bien que des petits malins penserait a verifier avec l'inspecteur."
      />
      <TextImageSection
        image="img/about/CursusScolaire.png"
        text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
      />
    </div>
  </div>
</template>

<script>
import TextSection from "@/components/TextSection";
import TextImageSection from "@/components/TextImageSection";
export default {
  name: "HiddenAbout",
  components: { TextSection, TextImageSection },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.hiddenAboutRoot {
  .hiddenAboutMessage {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    margin: 0;
    z-index: 1;
  }
  .hiddenAboutMain {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    max-width: 80vw;
    filter: blur(20px);
    -webkit-filter: blur(20px);
    position: relative;
  }
}
</style>
