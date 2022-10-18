<template>
  <div class="landing">
    <div class="cover-image" />
    <div class="landing-container">
      <div class="landing-container_content">
        <div class="container">
          <div>
            <div class="subtitle">BUSINESS DESCRIPTION</div>
            <div class="title mb-24">BUSINESS NAME HERE</div>
          </div>
          <div class="search-field flex">
            <Input
              :model.sync="search"
              :height="'40px'"
              :items="['test', 'hello', 'how', 'are', 'you', '!!']"
              :text-colour="'black'"
              :placeholder="'What are you looking for'"
              class="flex_1"
            />
          </div>
          <div class="quick-actions mt-48">
            <Button
              class="button"
              :text="'Call now'"
              :background="'transparent'"
              :border="'1px solid var(--primary)'"
              :height="'40px'"
              :border-radius="'4px'"
              :font-size="'20px'"
              :text-colour="'white'"
            />
            <Button
              class="button"
              :text="'Our Services'"
              :background="'var(--primary)'"
              :height="'40px'"
              :border-radius="'4px'"
              :font-size="'20px'"
              :text-colour="'white'"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  layout: "landing",
  data() {
    return {
      search: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/pages/landing.scss";
</style>
