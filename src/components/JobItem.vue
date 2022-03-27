<template>
  <div
    class="job__item"
    :job="job"
    :labelNew="labelNew"
    :labelFeatured="labelFeatured"
  >
    <div class="job__logo">
      <img src="../assets/img/photosnap.svg" alt="Photosnap vacancy" />
    </div>
    <div class="job__details">
      <div class="job__details-top">
        <h5 class="job__company">{{ companyName }}</h5>
        <div class="job__lables">
          <span class="job__label job__label--new" v-if="labelNew">New</span>
          <span class="job__label job__label--featured" v-if="labelFeatured"
            >Featured</span
          >
        </div>
      </div>
      <div class="job__details-body">
        <h2 class="job__title">{{ jobTitle }}</h2>
        <div class="job__details-info">
          <span class="job__info job__info--date">{{ posted }}</span>
          <span class="job__info job__info--time">{{ type }}</span>
          <span class="job__info job__info--location">{{ location }}</span>
        </div>
      </div>
    </div>
    <div class="job__tags">
      <ul class="job__tags-list">
        <li class="job__tags-item" v-for="tag in tags" :key="tag">
          <span>{{ tag }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  job: Object,
  companyName: String,
  labelNew: Boolean,
  labelFeatured: Boolean,
  jobTitle: String,
  posted: String,
  type: String,
  location: String,
  tags: Array
});
</script>

<style lang="scss">
.job__item {
  max-width: 100%;
  background-color: #fff;
  padding: 40px;
  border-radius: 5px;
  border-left: 4px solid $primaryDarkCyan;
  box-shadow: 0px 0px 15px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: space-between;

  .job__logo {
    margin-right: 35px;
    max-width: 80px;

    img {
      width: 100%;
      object-fit: cover;
      display: block;
    }
  }

  .job__details {
    margin-right: auto;
    display: flex;
    flex-direction: column;
    gap: 5px;
    &-top {
      display: flex;
      align-items: center;
      gap: 15px;
    }

    .job__company {
      color: $primaryDarkCyan;
      font-size: 14px;
    }

    .job__lables {
      display: flex;
      align-items: center;
      gap: 5px;
    }
    .job__label {
      background-color: black;
      color: #fff;
      padding: 2px 10px;
      border-radius: 15px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-transform: uppercase;
      font-weight: 500;
      font-size: 13px;
    }

    &-body {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }

    .job__title {
      font-size: 18px;
      color: $veryDarkCyan;
    }
    &-info {
      display: flex;
      justify-content: space-between;
      gap: 20px;
    }
    .job__info {
      color: $darkCyan;
      position: relative;
      text-transform: capitalize;

      &:not(:last-of-type) {
        padding-right: 20px;

        &::after {
          content: '';
          position: absolute;
          right: 0;
          bottom: 50%;
          transform: translate(50%, 50%);
          height: 4px;
          width: 4px;
          background-color: $darkCyan;
          border-radius: 50%;
        }
      }
    }
  }

  .job__tags {
    &-list {
      display: flex;
      align-items: center;
      gap: 15px;
    }

    &-item {
      background-color: $bgLightCyan;
      padding: 5px;
      border-radius: 5px;
      cursor: pointer;

      span {
        font-size: 16px;
        color: $primaryDarkCyan;
        font-weight: bold;
      }
    }
  }
}
</style>
