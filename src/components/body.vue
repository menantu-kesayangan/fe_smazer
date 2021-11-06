<template>
  <div class="view">
    <div
        class="page-wrapper"
    >
      <div class="page-header">
        <Header />
      </div>

        <div class="page-body">
          <transition name="fadeIn" enter-active-class="animated fadeIn">
            <router-view class="view"></router-view>
          </transition>
        </div>
        <Footer />

      <!-- <Customizer /> -->
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import Header from "./header";
import Footer from "./footer";

export default {
  name: "mainpage",
  data() {
    return {
      mobileheader_toggle_var: false,

      resized: false,
    };
  },

  components: {
    Header,
    Footer,
  },
  computed: {
    ...mapState({
      menuItems: (state) => state.menu.data,
      layout: (state) => state.layout.layout,

      body: (state) => state.body,
    }),
  },
  created() {
    window.addEventListener("resize", this.handleResize);
    this.handleResize();

    this.$store.dispatch("layout/set");
  },
  watch: {
    $route() {
      this.menuItems.filter((items) => {
        if (items.path === this.$route.path)
          this.$store.dispatch("menu/setActiveRoute", items);
        if (!items.children) return false;
        items.children.filter((subItems) => {
          if (subItems.path === this.$route.path)
            this.$store.dispatch("menu/setActiveRoute", subItems);
          if (!subItems.children) return false;
          subItems.children.filter((subSubItems) => {
            if (subSubItems.path === this.$route.path)
              this.$store.dispatch("menu/setActiveRoute", subSubItems);
          });
        });
      });
    },
  },
  methods: {
    hide() {
      this.$store.commit("hideForm", {});
    },

    mobiletoggle_toggle(value) {
      this.mobileheader_toggle_var = value;
    },
    handleResize() {
      this.$store.dispatch("menu/resizetoggle");
    },
  },
};
</script>
