<template>
  <q-layout view="lHr lpR fFf">
    <q-header class="bg-white text-black" bordered>
      <q-toolbar>
        <q-btn @click="toggleLeftDrawer" dense flat round icon="menu">
          <q-toolbar-title class="text-weight-bold">
            {{ menuList[selectedMenuItem].title }}
          </q-toolbar-title>
        </q-btn></q-toolbar
      >
    </q-header>

    <q-drawer
      :width="310"
      v-model="leftDrawerOpen"
      show-if-above
      side="left"
      bordered
    >
      <q-icon class="q-pa-md" name="fab fa-twitter" color="primary" size="md" />
      <q-list>
        <q-item
          v-for="(menu, index) in menuList"
          @click="handleMenuItemChange(index)"
          exact
          :to="menu.to"
          :key="index"
          clickable
          v-ripple
        >
          <q-item-section avatar>
            <q-icon :name="menu.icon" />
          </q-item-section>

          <q-item-section class="text-h6">{{ menu.title }}</q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer show-if-above side="right" bordered>
      <q-input
        style="background-color: #f7f9f9"
        class="q-ma-md"
        outlined
        rounded
        dense
        label="Buscar no Qwitter"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>
      <q-list
        padding
        class="q-ma-sm"
        style="background-color: #f7f9f9; border-radius: 10px"
      >
        <q-item class="q-pa-md">
          <q-item-section>
            <q-item-label overline>
              Campeonato Brasileiro - AO VIVO
            </q-item-label>
            <q-item-label class="text-weight-bold"
              >Corinthians x Ceará</q-item-label
            >
          </q-item-section>
        </q-item>
        <q-item class="q-pa-md">
          <q-item-section>
            <q-item-label overline> Internacional - AO VIVO </q-item-label>
            <q-item-label class="text-weight-bold">
              Presidente do Afeganistão deixa o país após Talibã chegar a Cabul
              para retomar o poder
            </q-item-label>
            <q-item-label caption>
              Assuntos do Momento: Afeganistão, Talibã
            </q-item-label>
          </q-item-section>
        </q-item>
        <q-item class="q-pa-md">
          <q-item-section>
            <q-item-label overline>
              Política · Assunto do Momento
            </q-item-label>
            <q-item-label class="text-weight-bold"> Os EUA </q-item-label>
            <q-item-label caption> 13,5 mil Tweets </q-item-label>
          </q-item-section>
        </q-item>
        <q-item class="q-pa-md">
          <q-item-section>
            <q-item-label overline> Covid-19 · AO VIVO </q-item-label>
            <q-item-label class="text-weight-bold">
              Paraná: as últimas notícias sobre a pandemia
            </q-item-label>
          </q-item-section>
        </q-item>
        <q-item class="q-pa-md">
          <q-item-section>
            <q-item-label overline> Futebol · Assunto do Momento </q-item-label>
            <q-item-label class="text-weight-bold">O Pedro </q-item-label>
            <q-item-label caption> 17,8 mil Tweets </q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container> <router-view /> </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const selectedMenuItem = ref(0);
    const menuList = [
      {
        title: "Página Inicial",
        to: "/",
        icon: "fas fa-home",
      },
      {
        title: "Sobre",
        to: "/about",
        icon: "fas fa-info-circle",
      },
    ];

    return {
      leftDrawerOpen,
      menuList,
      selectedMenuItem,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      handleMenuItemChange(index) {
        selectedMenuItem.value = index;
      },
    };
  },
};
</script>
