<script setup lang="ts">
import type { User } from "@/interfaces";

console.log("index.vue started"); //1
//2
definePageMeta({
  //3
  middleware: (to, from) => {
    const loginTokenCookie = useCookie<string | null>("loginToken"); //4
    const loginUserCookie = useCookie<User | null>("loginUser");
    if (loginTokenCookie.value == null || loginUserCookie.value == null) {
      return navigateTo("/login");
    } else {
      //5
      return;
    }
  },
});
</script>
<template>
  <h1>TOP</h1>
  <nav id="breadcrumbs">
    <ul>
      <li>TOP</li>
    </ul>
  </nav>
  <section>
    <p>
      <NuxtLink v-bind:to="{ name: 'member-memberList' }">
        会員管理はこちら
      </NuxtLink>
    </p>
  </section>
</template>
