<template>
  <v-app>
    <v-app-bar
      app
      color="pink accent-1"
      elevate-on-scroll
      scroll-target="#scrolling-techniques-7"
    >
      <v-app-bar-nav-icon class="ml-4" />

      <v-toolbar-title>Todo List</v-toolbar-title>
      <v-spacer />
      <div class="mr-4">
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </div>
    </v-app-bar>
    <v-navigation-drawer app color="pink accent-1" width="50px">
      <!-- -->
    </v-navigation-drawer>

    <!-- Sizes your content based upon application components -->
    <v-main>
      <!-- Provides the application the proper gutter -->

      <v-container fluid>
        <!-- If using vue-router -->
        <v-row>
          <nuxt />
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
