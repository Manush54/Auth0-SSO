<template>
  <PageLayout>
    <div class="content-layout">
      <h1 id="page-title" class="content__title">Protected Page</h1>
      <div class="content__body">
        <p id="page-description">
          <span
            >This page retrieves a <strong>protected message</strong> from an
            external API.</span
          >
          <span
            ><strong
              >Only authenticated users should access this page.</strong
            ></span
          >
        </p>
        <CodeSnippet title="Protected Message" :code="message" />
      </div>
    </div>
  </PageLayout>
</template>

<script>
import CodeSnippet from "@/components/code-snippet.vue";
import PageLayout from "@/components/page-layout.vue";
import { getProtectedResource } from "@/services/message.service";
export default {
  components: {
    PageLayout,
    CodeSnippet,
  },
  data() {
    return {
      message: "",
    };
  },
  async mounted() {
    const { data, error } = await getProtectedResource();
    if (data) {
      this.message = JSON.stringify(data, null, 2);
    }
    if (error) {
      this.message = JSON.stringify(error, null, 2);
    }
  },
  created() {
    if (!this.$auth0.isAuthenticated) {
      this.$router.push("/not-authorized");
    }
  },
};
</script>
