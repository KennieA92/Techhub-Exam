<template>
  <div class="col-12 d-flex justify-content-center" v-if="showNavbar">
    <nav class="navbar navbar-expand-lg col-12 col-sm-12 col-md-12">
      <div class="d-flex container-fluid justify-content-md-around col-10 px-0">
        <a class="navbar-brand col-3 d-flex" href="/"
          ><img src="../assets/logo.svg" alt="logo" />
          <div
            class="
              brand-name
              d-flex
              flex-column
              align-items-center
              justify-content-center
            "
          >
            <p>Techhub Syd</p>
          </div>
        </a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarTogglerDemo02"
          aria-controls="navbarTogglerDemo02"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon">
            <i class="fas fa-bars"></i>
          </span>
        </button>
        <div
          class="collapse navbar-collapse col-md-10 justify-content-end"
          id="navbarTogglerDemo02"
        >
          <ul class="navbar-nav mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link class="nav-link" to="/techStartUp"
                >Start Ups</router-link
              >
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/events">Events</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/contact"
                >Contact Us</router-link
              >
            </li>
            <li class="nav-item">
              <router-link class="nav-link" to="/gallery">Gallery</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import { ref, onUnmounted, onMounted } from "vue";
import { useRoute } from "vue-router";
export default {
  setup() {
    const route = useRoute();
    let showNavbar = ref(false);
    onMounted(() => {
      window.addEventListener("scroll", handleScroll);
    });
    onUnmounted(() => {
      window.removeEventListener("scroll", handleScroll);
    });

    const handleScroll = () => {
      window.pageYOffset > 0 || route.path !== "/"
        ? (showNavbar.value = true)
        : (showNavbar.value = false);
    };
    return { showNavbar };
  },
};
</script>

<style lang="scss" scoped>
nav {
  background: rgba(darken($primary-color, 25), 0.65);
  backdrop-filter: blur(10px);
  position: fixed;
  top: 0;
  z-index: 5;
  height: 80px;
  overflow-x: visible;

  @media only screen and (max-width: 600px) {
    height: 90px;
  }

  a {
    font-size: 1rem;
    font-weight: bold;
    &:hover {
      color: $tertiary-color;
    }

    &:active {
      color: $tertiary-color;
    }
  }

  .navbar-nav {
    .nav-item {
      .nav-link {
        padding-left: 2rem;
        padding-right: 0.5rem;
      }
    }
  }

  .navbar-toggler {
    border-radius: 0px;
    border: 2px solid $quaternary-color;
    overflow-x: visible;

    .navbar-toggler-icon {
      text-align: center;
      color: $quaternary-color;
      overflow-x: visible;

      i {
        color: $quaternary-color;
        font-size: 28px;
      }
    }
  }

  a {
    font-weight: bold;
    color: $quaternary-color;

    &:hover {
      color: $tertiary-color;
    }
  }

  .navbar-collapse {
    @media only screen and (max-width: 990px) {
      background: rgba(darken($primary-color, 25), 0.85);
      backdrop-filter: blur(10px);

      .nav-item {
        .nav-link {
          font-size: 1rem;
          font-weight: bold;
          padding: 1.05rem;

          &:hover {
            color: $tertiary-color;
            text-decoration: none;
          }
        }
      }
    }
  }

  .navbar-brand {
    img {
      height: 60px;
    }
  }

  .brand-name {
    padding-left: 0.5rem;

    p {
      font-size: 1.2rem;
      font-weight: 400;
      margin: 0;
      padding: 0;
    }
  }
}
</style>