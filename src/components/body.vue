<template>
  <div class="view">
    <div class="page-body">
      <div class="page-header" :class="{ close_icon: !togglesidebar }">
        <Header @clicked="sidebar_toggle" />
      </div>

      <router-view class="view"></router-view>
      <div class="page-footer" :class="{ close_icon: !togglesidebar }">
        <Footer @clicked="sidebar_toggle" />
      </div>
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
      sidebar_toggle_var: false,

      resized: false,
    };
  },
  // props:['sidebar_toggle_var'],
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
    this.resized = this.sidebar_toggle_var;
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
    sidebar_toggle_var: function() {
      this.resized =
        this.width <= 991 ? !this.sidebar_toggle_var : this.sidebar_toggle_var;
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
