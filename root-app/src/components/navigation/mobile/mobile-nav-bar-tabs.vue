<template>
  <div class="mobile-nav-bar__tabs">
    <MobileNavBarTab
      path="/profile"
      label="Profile"
      :handle-click="handleClick"
    />
    <MobileNavBarTab
      path="/public"
      label="Public"
      :handle-click="handleClick"
    />
    <MobileNavBarTab
      path="/protected"
      label="Protected"
      :handle-click="handleClick"
    />
    <MobileNavBarTab path="/admin" label="Admin" :handle-click="handleClick" />
  </div>
</template>

<script>
import MobileNavBarTab from "@/components/navigation/mobile/mobile-nav-bar-tab.vue";

export default {
  components: { MobileNavBarTab },
  props: {
    handleClick: Function,
  },
};
</script>
