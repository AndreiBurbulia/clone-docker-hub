<template>
  <div class="home">
    <LoadingComponent v-if="showComponent" />
    <MainComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import MainComponent from "@/components/MainComponent.vue";
import LoadingComponent from "@/components/LoadingComponent.vue";
// import ErrorComponent from "@/components/ErrorComponent.vue";

// const MainComponent = () => ({
//   component: import(/* */"@/components/MainComponent"),
//   loading: LoadingComponent,
//   error: ErrorComponent,
//   timeout: 3000,
// });

export default {
  data() {
    return {
      showComponent: true,
    };
  },
  components: {
    MainComponent,
    LoadingComponent,
  },
  methods: {
    show() {
      this.showComponent = false;
    },
  },

  mounted() {
    setTimeout(() => {
      this.show();
    }, 2000);
  },
};
</script>
