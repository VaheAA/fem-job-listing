<template>
  <div class="bg-pattern"></div>
</template>

<script setup></script>

<style lang="scss">
.bg-pattern {
  background-image: url('/img/bg-header-desktop.svg');
  background-repeat: no-repeat;
  background-color: $primaryDarkCyan;
  background-position: center;
  height: 150px;

  @media (max-width: 728px) {
    background-image: url('/img/bg-header-mobile.svg');
  }
}
</style>
