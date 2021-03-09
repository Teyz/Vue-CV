<template>
  <div class="contactRoot">
    <div class="contactHeaderRoot" data-aos="fill" data-aos-delay="100">
      <h2>Fixer <br />un <span>rendez-vous</span></h2>
      <span class="drawText" data-aos="fade-right" data-aos-delay="200"
        >On s'appelle ? :)</span
      >
      <svg
        width="768"
        height="203"
        viewBox="0 0 768 203"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          data-aos="fill"
          data-aos-duration="1000"
          d="M3.00684 110.418C18.9536 91.7875 35.9553 74.9315 55.7805 60.3342C84.4391 39.2328 116.656 19.4739 150.988 9.17413C152.715 8.65611 183.359 0.0367267 184.039 3.43656C184.616 6.32127 175.363 15.4018 174.656 16.2266C163.665 29.0414 152.548 41.7142 141.844 54.7759C120.09 81.3212 98.5834 108.465 80.4641 137.672C79.3212 139.514 66.2938 159.968 73.3519 156.259C83.5145 150.919 93.2986 141.281 101.98 134.325C124.652 116.158 147.237 97.8274 170.592 80.5352C191.539 65.0256 213.565 50.6991 237.231 39.655C238.563 39.0337 246.334 34.5006 248.408 36.7862C251.482 40.1746 244.135 52.6204 243.447 54.0587C226.542 89.4241 208.776 124.412 191.63 159.666C187.006 169.171 181.974 178.656 178.003 188.473C176.965 191.039 174.744 195.605 175.074 198.574C175.454 201.99 181.789 196.58 184.577 194.569C198.812 184.303 212.379 172.997 226.234 162.236C258.11 137.479 290.005 112.788 326.104 94.401C335.975 89.3733 346.219 84.458 356.824 81.1329C360.06 80.1182 366.278 77.9744 369.494 80.6547C374.168 84.5493 372.065 93.9318 370.929 98.5846C367.326 113.333 360.036 127.162 353.238 140.6C345.222 156.446 334.108 172.342 328.196 189.19C324.415 199.967 335.132 190.675 338.774 188.115C375.248 162.482 411.087 135.849 451.016 115.678C477.951 102.071 508.549 87.9242 539.111 85.3165C543.592 84.9342 553.532 83.7645 556.264 89.1415C559.03 94.5841 552.931 103.533 550.706 107.789C541.94 124.555 531.976 140.666 523.811 157.753C523.009 159.431 514.318 175.496 521.899 172.814C531.921 169.269 541.62 162.802 550.646 157.455C567.411 147.522 583.951 137.19 600.432 126.794C613.209 118.734 625.829 110.449 638.503 102.23C642.862 99.4037 647.873 95.6324 652.906 93.9229C664.561 89.9648 649.731 121.358 648.842 123.208C641.761 137.954 632.455 152.7 628.522 168.75C628.168 170.192 625.967 176.894 628.582 177.954C633.466 179.934 644.759 173.76 648.245 172.097C676.538 158.603 702.743 141.052 731.2 127.751C732.92 126.947 763.336 111.829 764.67 117.351C765.918 122.524 759.638 131.35 757.498 135.162C753.58 142.139 749.306 148.911 745.305 155.841C740.892 163.486 734.784 171.507 731.798 179.867C730.058 184.739 736.399 180.019 737.775 179.269"
          stroke="#F2C94C"
          stroke-width="5"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </div>
    <form @submit.prevent="sendEmail">
      <div class="formRow" data-aos="fade-right" data-aos-delay="300">
        <label for="name">Hello Bastien, je suis </label>
        <input
          type="text"
          id="name"
          name="name"
          required
          v-model="name"
          placeholder="Bob"
        />
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
        data-aos-delay="400"
        style="flex-direction: column; display: flex;"
      >
        <label for="message">Pour te donner plus de détails : </label>
        <textarea
          id="message"
          name="message"
          rows="1"
          cols="33"
          v-model="message"
          placeholder="J'ai très envie de travailler avec toi ;)"
        >
        </textarea>
      </div>
      <div class="formRow" data-aos="fade-left" data-aos-delay="500">
        <label for="email"
          >Tu peux me recontacter sur mon adresse mail :
        </label>
        <input
          type="email"
          id="email"
          name="email"
          required
          v-model="email"
          style="max-width: 240px;"
        />
      </div>
      <div class="formRow" data-aos="fade-right" data-aos-delay="600">
        <input type="checkbox" id="aggrement" name="aggrement" required />
        <label for="aggrement" class="checkbox-label"
          >Bien sûr, je ne suis pas un robot</label
        >
      </div>
      <div class="formRow" data-aos="fade-left" data-aos-delay="700">
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
[data-aos="fill"] {
  path {
    stroke-dasharray: 1991;
    stroke-dashoffset: 1991;
  }

  &.aos-animate {
    path {
      stroke-dashoffset: 0;
    }
  }
}
.contactRoot {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  max-width: 100vw;
  margin-top: 48px;

  .contactHeaderRoot {
    position: relative;
    padding: 24px;

    .drawText {
      position: absolute;
      right: 0;
      top: -15%;
      transform: rotate(5deg);
      color: #f2c94c;
      letter-spacing: 0.04em;
      font-weight: 300;
      font-size: 30px;
      line-height: 30px;
      font-family: blambot-fx-pro, sans-serif;
    }
    svg {
      width: 100%;
      display: block !important;
      position: absolute;
      top: -45px;
      left: -15px;
    }

    // [data-aos="example-anim1"] {
    //   stroke-dasharray: 1991;
    //   stroke-dashoffset: 1991;
    //   animation: dash 1s linear forwards;
    //   &.aos-animate {
    //     @keyframes dash {
    //       to {
    //         stroke-dashoffset: 0;
    //       }
    //     }
    //   }
    // }
  }

  @media screen and (min-width: 1024px) {
    margin-top: 0;

    .contactHeaderRoot {
      position: relative;

      .drawText {
        position: absolute;
        right: 0;
        top: -15%;
        transform: rotate(5deg);
        color: #f2c94c;
        letter-spacing: 0.04em;
        font-weight: 300;
        font-size: 30px;
        line-height: 30px;
        font-family: blambot-fx-pro, sans-serif;
      }
      svg {
        display: block !important;
        position: absolute;
        top: -45px;
        left: -15px;
      }

      // [data-aos="example-anim1"] {
      //   stroke-dasharray: 1991;
      //   stroke-dashoffset: 1991;
      //   animation: dash 1s linear forwards;
      //   &.aos-animate {
      //     @keyframes dash {
      //       to {
      //         stroke-dashoffset: 0;
      //       }
      //     }
      //   }
      // }
    }
  }

  h2 {
    font-family: "Akira";
    font-weight: 900;
    font-size: 25px;
    margin: 0;
    color: white !important;

    @media screen and (min-width: 1024px) {
      font-size: 59px !important;
      max-width: 800px;
      text-align: left;
      position: relative;

      // &:before {
      //   content: "";
      //   background-image: url("/img/contact/line.svg");
      //   background-repeat: no-repeat;
      //   width: 780px;
      //   height: 200px;
      //   position: absolute;
      //   top: -45px;
      //   left: -15px;
      // }
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
