<template>
  <div class="contactRoot">
    <h2 data-aos="zoom-out-down">Fixer un <span>rendez-vous</span></h2>
    <form @submit.prevent="sendEmail">
      <div class="formRow" data-aos="fade-right" data-aos-delay="100">
        <label for="name">Hello Bastien, je suis </label>
        <input type="text" id="name" name="name" required v-model="name" />
        <label for="project"> et j'aimerais </label>
        <select name="project" id="project required" v-model="project">
          <option value="discuss">Discuter avec toi</option>
          <option value="quote">Un devis</option>
          <option value="project">Te parler d'un projet</option>
        </select>
      </div>
      <div
        class="formRow"
        data-aos="fade-left"
        data-aos-delay="200"
        style="flex-direction: column; display: flex;"
      >
        <label for="message">Pour te donner plus de détails : </label>
        <textarea
          id="message"
          name="message"
          rows="1"
          cols="33"
          v-model="message"
        >
        </textarea>
      </div>
      <div class="formRow" data-aos="fade-left" data-aos-delay="300">
        <label for="email">Rester en contact avec moi </label>
        <input type="email" id="email" name="email" required v-model="email" />
      </div>
      <div class="formRow" data-aos="fade-right" data-aos-delay="400">
        <input type="checkbox" id="aggrement" name="aggrement" required />
        <label for="aggrement" class="checkbox-label"
          >Prouves moi que tu n'es pas un robot en cochant cette case</label
        >
      </div>
      <div class="formRow" data-aos="fade-left" data-aos-delay="500">
        <button type="submit">Envoyer</button>
      </div>
    </form>
  </div>
</template>

<script>
import AOS from "aos";
import "aos/dist/aos.css";
import emailjs from "emailjs-com";
import { onMounted, ref } from "vue";
import { useToast } from "vue-toastification";
export default {
  name: "Contact",
  setup() {
    const toast = useToast();
    const name = ref("");
    const project = ref("");
    const email = ref("");
    const message = ref("");
    const sendEmail = (e) => {
      emailjs
        .sendForm(
          "service_3myt38i",
          "template_3ysie0p",
          e.target,
          "user_UCQM7Dx1nsQped1PwUprh",
          {
            name: name.value,
            email: email.value,
            project: project.value,
            message: message.value,
          }
        )
        .then(
          (result) => {
            toast.success("Email envoyé !", {
              position: "top-right",
            });
            resetForm();
          },
          (error) => {
            resetForm();
            toast.error("Une erreur est survenue", {
              position: "top-right",
            });
          }
        );
    };
    const resetForm = () => {
      name.value = "";
      project.value = "";
      email.value = "";
      message.value = "";
    };
    onMounted(() => {
      AOS.init();
    });
    return {
      sendEmail,
      name,
      project,
      email,
      message,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.contactRoot {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  max-width: 100vw;
  margin-top: 48px;

  @media screen and (min-width: 1024px) {
    margin-top: 0;
  }

  h2 {
    font-family: "Akira";
    font-weight: 900;
    font-size: 25px;
    margin: 0;
    color: white !important;

    @media screen and (min-width: 1024px) {
      font-size: 59px !important;
      max-width: 700px;
      text-align: left;
    }

    span {
      color: transparent;
      -webkit-text-stroke-width: 1px;
      -webkit-text-stroke-color: rgba(255, 255, 255, 1) !important;
    }
  }

  .formRow {
    position: relative;
    margin-bottom: 24px;

    .checkbox-label {
      margin-left: 12px;
      @media screen and (max-width: 375px) {
        margin-left: 32px;
      }
    }
  }
}
</style>
