<template>
  <main>
    <div class="jobs__wrapper">
      <JobsHeaderBg />
      <div class="container">
        <JobsList />
      </div>
    </div>
  </main>
</template>

<script setup>
import JobsList from './JobsList.vue';
import JobsHeaderBg from './JobsHeaderBg.vue';
</script>

<style lang="scss"></style>
