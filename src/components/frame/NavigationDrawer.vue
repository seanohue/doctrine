<template>
  <!-- v-model="drawer" -->
  <v-navigation-drawer :value="drawer" @input="$emit('input', $event)" app clipped>
    <v-list dense>
      <!-- Home nav item -->
      <v-list-item @click="navTo('/')">
        <v-list-item-action>
          <v-icon>mdi-home</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title>Home</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list-item @click="navTo('/playing')">
        <v-list-item-action>
          <v-icon>mdi-sword</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title>Playing</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-list-item
        v-for="nav_link in playing_links"
        :key="nav_link.route"
        @click="navTo(nav_link.route)"
      >
        <v-list-item-action />
        <v-list-item-content>
          <v-list-item-title>{{ nav_link.label }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list-item @click="navTo('/building')">
        <v-list-item-action>
          <v-icon>mdi-wrench</v-icon>
        </v-list-item-action>
        <v-list-item-content>
          <v-list-item-title>Building</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list-item
        v-for="(nav_link, index) in builder_links"
        :key="index"
        @click="navTo(nav_link.route)"
      >
        <v-list-item-action />
        <v-list-item-content>
          <v-list-item-title>{{ nav_link.label }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

  <script>
export default {
  name: "NavigationDrawer",
  props: {
    drawer: Boolean
  },
  data: () => ({
    // drawer: true,
    playing_links: [
      {
        label: "Experience",
        route: "/playing/experience"
      }
    ],
    builder_links: [
      {
        label: "Mob Items",
        route: "/building/mobs/items"
      },
      {
        label: "Mob Reactions",
        route: "/building/mobs/reactions"
      },
      {
        label: "Factions",
        route: "/building/factions"
      },
      {
        label: "Room Checks",
        route: "/building/roomchecks"
      },
      {
        label: "Quests",
        route: "/building/quests"
      }
    ]
  }),
  methods: {
    navTo(route) {
      if (route === this.$router.currentRoute.fullPath) {
        return;
      }
      this.$router.push({ path: route });
    }
  }
};
</script>