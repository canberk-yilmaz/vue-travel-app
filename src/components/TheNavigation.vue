<template>
  <nav id="nav">
    <p class="logo">Canberk's Travel App</p>
    <ul class="nav-links">
      <li class="links">
        <router-link to="/"> Home </router-link>
      </li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { id: destination.id, name: destination.name },
          }"
          >{{ destination.name }}</router-link
        >
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store";

export default {
  name: "TheNavigation",
  data() {
    return {
      destinationId: this.$route.params.id,
      destinationName: this.$route.params.name,
      destinations: store.destinations,
    };
  },
};
</script>

<style scoped>
#nav {
  display: flex;
}

#nav a {
  color: #2c3e50;
  text-decoration: none;
  font-weight: bold;
}

#nav a.router-link-exact-active {
  color: #4437b6;
}

.nav-links {
  display: flex;
}

.links {
  padding-right: 20px;
  list-style: none;
}

.links:hover {
  text-decoration: underline;
}
.logo {
  font-size: 20px;
  color: #4437b6;
  font-weight: bold;
}
</style>
