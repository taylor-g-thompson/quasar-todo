<template>
  <div>
    <!-- Use the EssentialLink component here -->
    <EssentialLink />
    <!-- ... other template code -->
  </div>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-lg q-mb-lg q-mt-none"></div>
      <div class="text-h4">To Do List</div>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="200"
      :breakpoint="400"
    >
      <q-scroll-area
        style="
          height: calc(100% - 10px);
          margin-top: 150px;
          border-right: 5px solid #ceb4ff;
        "
      >
        <q-list padding>
          <q-item to="/ToDoList" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="check" />
            </q-item-section>

            <q-item-section> To Do </q-item-section>
          </q-item>

          <q-item to="/help" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> Help </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img
        class="absolute-top"
        src="https://cdn.pixabay.com/photo/2023/08/29/18/01/rainbow-8221835_1280.jpg"
        style="height: 138px"
      >
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="68px" class="q-mb-sm">
            <img
              src="https://cdn.pixabay.com/photo/2019/03/18/10/15/cat-4062809_1280.jpg"
            />
          </q-avatar>
          <div class="text-weight-bold">Taylor Thompson</div>
          <div>taylor@vitalitysouth.com</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
}
</style>
