<template>
  <b-container class="card-container">
    <b-row>
      <b-col class="img-container" cols="12" md="5" lg="4">
        <div class="logo-container">
          <img src="@/assets/logo.png" alt="" class="logo" />
        </div>

        <div class="picture">
          <div class="img">photo</div>
        </div>

        <div class="separator"></div>
      </b-col>

      <b-col class="data-container" cols="12" md="7" lg="8">
        <div class="name-and-position">
          <h1>{{ person.name }}</h1>
          <p>{{ person.position }}</p>
          <p>{{ person.company }}</p>
        </div>
        <p class="description">{{ person.description }}</p>
        <button class="download">descargar contacto</button>
      </b-col>

      <b-col class="contact-container" cols="12" md="6">
        <div class="data" v-if="person.site">
          <font-awesome-icon class="icon" icon="globe" />
          <a :href="person.site" class="link">
            {{ person.site }}
          </a>
        </div>

        <div class="data">
          <font-awesome-icon class="icon" icon="envelope" />
          <a :href="'mailto:' + person.email" class="link">
            {{ person.email }}
          </a>
        </div>

        <div class="data">
          <font-awesome-icon class="icon" :icon="['fab', 'whatsapp']" />
          <a :href="'https://wa.me/' + person.whatsapp" class="link">
            {{ person.whatsapp }}
          </a>
        </div>

        <template v-for="(phone, i) in person.phones">
          <div :key="i" class="data">
            <font-awesome-icon class="icon" icon="phone-alt" />
            <a :href="'tel:' + phone.replace(/\s/g, '')" class="link">
              {{ phone }}
            </a>
          </div>
        </template>
      </b-col>

      <b-col class="social-container" cols="12" md="6">
        <div class="data" v-if="person.facebook">
          <font-awesome-icon class="icon" :icon="['fab', 'facebook']" />
          <a :href="person.facebook" class="link"> Facebook </a>
        </div>

        <div class="data" v-if="person.twitter">
          <font-awesome-icon class="icon" :icon="['fab', 'twitter']" />
          <a :href="person.twitter" class="link"> Twitter </a>
        </div>

        <div class="data" v-if="person.instagram">
          <font-awesome-icon class="icon" :icon="['fab', 'instagram']" />
          <a :href="person.instagram" class="link"> Instagram </a>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
export default {
  name: "Card",
  props: {
    person: {},
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/variables.scss";
@import "@/assets/scss/mixins.scss";

.card-container {
  background-color: #222;
  width: 100%;

  .img-container {
    position: relative;
    padding: 0;

    .logo-container {
      position: absolute;
      height: 3rem;
      width: 3rem;
      top: 1rem;
      left: 1rem;

      .logo {
        width: 100%;
        height: auto;
      }
    }

    .picture {
      height: 20rem;
      .img {
        content: "";
        background-color: #555;
        width: 100%;
        height: 100%;
        @include center;
      }
    }

    .separator {
      content: "";
      background-color: $primary;
      height: 1rem;
      width: 100%;
    }
  }

  .data-container {
    .name-and-position {
      position: relative;
      padding: 1rem;

      &:before {
        position: absolute;
        left: 0;
        content: "";
        width: 0.2rem;
        height: calc(100% - 2rem);
        background-color: #555;
      }
    }

    .description {
      text-align: start;
    }

    .download {
      border: none;
      // border-radius: 0.5rem;
      background-color: $primary;
      color: $textcolor;
      padding: 0.5rem;
      width: 100%;
    }
  }

  .contact-container {
    padding: 1rem;
    padding-bottom: 0;

    .data {
      display: flex;
      gap: 0.5rem;
      align-items: center;
      margin-bottom: 1rem;

      .icon {
        font-size: 1.2rem;
        color: $primary;
      }

      p {
        margin: 0;
      }

      .link {
        text-decoration: none;
        color: $textcolor;
        &:hover {
          color: $primary;
        }
      }
    }
  }

  .social-container {
    padding: 1rem;
    padding-bottom: 0;

    .data {
      display: flex;
      gap: 0.5rem;
      align-items: center;
      margin-bottom: 1rem;

      .icon {
        font-size: 1.2rem;
        color: $primary;
      }

      p {
        margin: 0;
      }

      .link {
        text-decoration: none;
        color: $textcolor;
        &:hover {
          color: $primary;
        }
      }
    }
  }
}
</style>
