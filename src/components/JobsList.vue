<template>
  <div class="jobs__list-wrapper">
    <ul class="jobs__list">
      <li v-for="job in jobs" :key="job.id">
        <JobItem
          :job="job"
          :companyName="job.company"
          :labelNew="job.new"
          :labelFeatured="job.featured"
          :jobTitle="job.position"
          :posted="job.postedAt"
          :type="job.contract"
          :location="job.location"
          :tags="job.tags"
          :image="job.logo"
        />
      </li>
    </ul>
  </div>
</template>

<script setup>
import JobItem from './JobItem.vue';
import data from '../../public/data.json';
import { ref } from 'vue';

const jobs = ref(data);

jobs.value.forEach((job) => {
  const { role, level, languages, tools } = job;
  job.tags = [role, level, ...languages, ...tools];
});
</script>

<style lang="scss">
.jobs__list-wrapper {
  margin-top: 80px;
}

.jobs__list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}
</style>
