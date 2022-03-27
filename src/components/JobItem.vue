<template>
  <div
    class="job__item"
    :class="{ 'job__item--featured': labelFeatured }"
    :job="job"
    :labelNew="labelNew"
    :labelFeatured="labelFeatured"
  >
    <div class="job__logo">
      <img :src="image" :alt="companyName" />
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
        <li
          class="job__tags-item"
          v-for="tag in tags"
          :key="tag"
          @click="addTag(tag)"
        >
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
  tags: Array,
  image: String
});

const emit = defineEmits(['addTag']);

const addTag = (tag) => {
  emit('addTag', tag);
};
</script>

<style lang="scss">
.job__item {
  max-width: 100%;
  background-color: #fff;
  padding: 40px;
  border-radius: 5px;
  box-shadow: 0px 0px 15px 5px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: space-between;

  @media (max-width: 728px) {
    flex-direction: column;
    align-items: flex-start;
    gap: 20px;
    padding: 10px 20px;
  }

  &--featured {
    border-left: 4px solid $primaryDarkCyan;
  }

  .job__logo {
    margin-right: 35px;
    max-width: 80px;

    img {
      width: 100%;
      object-fit: cover;
      display: block;
    }
    @media (max-width: 728px) {
      margin-top: -30px;
      max-width: 45px;
    }
  }

  .job__details {
    margin-right: auto;
    display: flex;
    flex-direction: column;
    gap: 5px;

    @media (max-width: 728px) {
      gap: 15px;
      position: relative;
      margin-right: 0;
      width: 100%;

      &::after {
        content: '';
        position: a;
        height: 1px;
        width: 100%;
        left: 0;
        bottom: 0;
        background-color: $darkCyan;
      }
    }

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
      color: #fff;
      padding: 2px 10px;
      border-radius: 15px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-transform: uppercase;
      font-weight: 600;
      font-size: 13px;

      &--new {
        background-color: $primaryDarkCyan;
      }
      &--featured {
        background-color: $veryDarkCyan;
      }
    }

    &-body {
      display: flex;
      flex-direction: column;
      gap: 5px;
    }

    .job__title {
      font-size: 18px;
      color: $veryDarkCyan;
      transition: all 0.3s ease;
      cursor: pointer;
      @media (max-width: 728px) {
        margin-bottom: 15px;
      }

      &:hover {
        color: $primaryDarkCyan;
      }
    }
    &-info {
      display: flex;
      justify-content: space-between;
      gap: 20px;

      @media (max-width: 728px) {
        justify-content: flex-start;
      }
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
      flex-wrap: wrap;

      @media (max-width: 728px) {
        padding-bottom: 15px;
      }
    }

    &-item {
      cursor: pointer;

      span {
        background-color: $bgLightCyan;
        border-radius: 5px;
        padding: 5px;
        font-size: 16px;
        color: $primaryDarkCyan;
        font-weight: bold;
        position: relative;
        z-index: 1;
        transition: all 0.3s ease;

        &::after {
          content: '';
          position: absolute;
          width: 100%;
          height: 100%;
          border-radius: 5px;
          top: 0;
          left: 0;
          background-color: $bgLightCyan;
          opacity: 0;
          z-index: -1;
          transition: all 0.3s ease;
        }

        &:hover {
          color: #fff;
        }

        &:hover::after {
          color: #fff;
          background-color: $primaryDarkCyan;
          opacity: 1;
        }
      }
    }
  }
}
</style>
