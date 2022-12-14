<template>
  <div>
    <Banner />
    <div class="menu" :class="showMenu ? 'menu_show' : 'menu_hide'">
      <div
        v-for="(item, index) in navItems"
        :key="`item_${index}`"
        class="menu_item"
        @click="navRoute(item)"
      >
        {{ item.label }}
      </div>
      <div class="flex center nav-auth">
        <Button
          class="mr-8"
          :text="'Login'"
          :height="'30px'"
          :text-colour="'white'"
          :background="'transparent'"
          :border="'1px solid white'"
          @click="showAuth('login')"
        />
        <Button
          :text="'Sign up'"
          :height="'30px'"
          @click="showAuth('register')"
        />
      </div>
      <div class="flex center w-100 mt-24">
        <img class="cart" src="~/assets/icons/white-shopping-cart.svg" alt="" />
      </div>
    </div>
    <div class="nav" :class="{ 'nav_fill-bg': showMenu }" :style="navStyles">
      <div class="flex space-between links container align-center">
        <div class="flex align-center">
          <img
            @click="showMenu = !showMenu"
            class="burger-menu hide-desktop pointer"
            :src="burgerSource"
            alt=""
          />
          <div class="logo pointer">Your logo here</div>
          <div class="flex hide-mobile">
            <div
              @click="$router.push(`/${item.route}`)"
              class="item pointer flex"
              v-for="(item, index) in navItems"
              :key="`item_${index}`"
            >
              <div
                class="nav-link"
                v-if="!item.links"
                :class="{ selected: isSelected(item) }"
              >
                {{ item.label }}
              </div>
              <DropdownLink v-else :item="item" />
            </div>
          </div>
        </div>
        <div class="flex center nav-auth hide-mobile">
          <Button
            class="mr-8"
            :text="'Login'"
            :height="'30px'"
            :text-colour="'white'"
            :background="'transparent'"
            :border="'1px solid white'"
            @click="showAuth('login')"
          />
          <Button
            :text="'Sign up'"
            :height="'30px'"
            @click="showAuth('register')"
          />
          <img
            class="cart"
            src="~/assets/icons/white-shopping-cart.svg"
            alt=""
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nav",
  props: {
    absolute: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      search: "",
      showMenu: false,
      navItems: [
        {
          label: "Home",
          route: "",
          name: "home",
        },
        {
          label: "Link1",
          route: "",
          name: "link1",
        },
        {
          label: "Link2",
          route: "",
          name: "link2",
          links: [
            {
              label: "Sublink1",
            },
            {
              label: "Sublink2",
            },
          ],
        },
        {
          label: "Link3",
          route: "",
          name: "link3",
        },
      ],
    };
  },
  watch: {
    showMenu(val) {
      if (val) document.documentElement.style.overflow = "hidden";
      else document.documentElement.style.overflow = "visible";
    },
  },
  computed: {
    isSelected() {
      return (item) => item.name === this.$route.name;
    },
    navStyles() {
      const styles = {
        position: "relative",
        background: "black",
      };

      if (this.absolute) {
        styles.position = "absolute";
        styles.background = "rgba($color: black, $alpha: 0.5)";
      }

      return styles;
    },
    burgerSource() {
      return this.showMenu
        ? require("~/assets/icons/white-close.svg")
        : require("~/assets/icons/white-burger-menu.svg");
    },
  },
  methods: {
    navRoute(item) {
      this.$router.push(`/${item.route}`);
      setTimeout(() => (this.showMenu = false), 500);
    },
    async showAuth(type) {
      await this.$store.commit("setModal", {
        show: true,
        type: "auth",
      });
      this.$router.replace({ query: { ...this.$route.query, auth: type } });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/components/nav.scss";
</style>