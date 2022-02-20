<template>
  <Head :title="title">
    <!-- <title>Home</title> -->
    <link
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap"
      rel="stylesheet"
    />
  </Head>

  <jet-banner />

  <div class="min-h-screen bg-gray-100">
    <!-- ShowCase & Navbar -->
    <div class="min-h-screen showcase bg-no-repeat bg-center bg-cover">
      <!-- Navbar -->
      <nav class="">
        <!-- Primary Nav Menu -->
        <div class="max-w-7xl mx-auto px-4 py-2 sm:px-6 lg:px-8">
          <div class="flex justify-between">
            <!-- Links & Logo -->
            <div class="flex">
              <!-- Logo y Nombre -->
              <div class="flex items-center">
                <!-- Logo -->
                <div
                  class="
                    shrink-0
                    flex
                    items-center
                    w-20
                    mr-2
                    rounded-full
                    overflow-hidden
                  "
                >
                  <Link :href="route('dashboard')">
                    <jet-application-mark class="block" />
                  </Link>
                </div>
                <!-- Nombre -->
                <h2
                  class="
                    font-poppins font-bold
                    text-2xl text-white
                    w-16
                    tracking-wide
                  "
                >
                  HBC
                </h2>
              </div>
            </div>

            <!-- Hamburguer -->
            <div class="flex items-center sm:hidden">
              <button
                @click="showingNavigationDropdown = !showingNavigationDropdown"
                class="
                  inline-flex
                  items-center
                  justify-center
                  p-2
                  rounded-md
                  text-gray-400
                  border border-dashed border-gray-400
                  focus:outline-none
                  transition
                "
              >
                <svg
                  class="h-6 w-6"
                  stroke="currentColor"
                  fill="none"
                  viewBox="0 0 24 24"
                >
                  <path
                    :class="{
                      hidden: showingNavigationDropdown,
                      'inline-flex': !showingNavigationDropdown,
                    }"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M4 6h16M4 12h16M4 18h16"
                  />
                  <path
                    :class="{
                      hidden: !showingNavigationDropdown,
                      'inline-flex': showingNavigationDropdown,
                    }"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M6 18L18 6M6 6l12 12"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>

        <!-- Responsive Navigation Menu -->
        <div
          :class="{
            block: showingNavigationDropdown,
            hidden: !showingNavigationDropdown,
          }"
          class="sm:hidden bg-gray-100 bg-opacity-80"
        >
          <div class="pt-2 pb-3 space-y-1">
            <jet-responsive-nav-link
              v-for="link in navLinks"
              :key="link.id"
              :href="route(link.routeName)"
              :active="route().current(link.routeName)"
            >
              {{ link.name }}
            </jet-responsive-nav-link>
          </div>
        </div>
      </nav>

      <!-- Page Heading -->
      <header v-if="$slots.header">
        <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
          <slot name="header"></slot>
        </div>
      </header>
    </div>
  </div>
</template>

<script>
import JetApplicationMark from "@/Components/ApplicationMark.vue";
import JetBanner from "@/Jetstream/Banner.vue";
import JetResponsiveNavLink from "@/Jetstream/ResponsiveNavLink.vue";
import { Head, Link } from "@inertiajs/inertia-vue3";

export default {
  components: {
    JetApplicationMark,
    JetBanner,
    JetResponsiveNavLink,
    Head,
    Link,
  },
  props: {
    title: String,
    showcaseUrl: String,
  },
  data() {
    return {
      showingNavigationDropdown: false,
      navLinks: [
        { id: 1, name: "Home", routeName: "home" },
        { id: 2, name: "Habitaciones", routeName: "dashboard" },
        { id: 2, name: "Comodidades", routeName: "dashboard" },
        { id: 2, name: "Contacto", routeName: "dashboard" },
      ],
    };
  },
  computed: {
    showCase() {
      return `url(${this.showcaseUrl})`;
    },
  },
};
</script>

<style scoped>
.showcase {
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    v-bind(showCase);
}
</style>