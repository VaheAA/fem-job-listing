<template>
  <JobsFilter :tagsList="filterTags" @deleteTag="deleteTag" />
  <div class="jobs__list-wrapper">
    <ul class="jobs__list">
      <li v-for="job in filteredJobs" :key="job.id">
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
          @addTag="addFilterTag"
        />
      </li>
    </ul>
  </div>
</template>

<script setup>
import JobItem from './JobItem.vue';
import JobsFilter from './JobsFilter.vue';
import data from '../../public/data.json';
import { ref, computed, onMounted } from 'vue';

const filterTags = ref([]);
const jobs = ref(data);

jobs.value.forEach((job) => {
  const { role, level, languages, tools } = job;
  job.tags = [role, level, ...languages, ...tools];
});

const filteredJobs = computed(() => {
  if (filterTags.value.length) {
    return jobs.value.filter((job) =>
      filterTags.value.every((tag) => job.tags.includes(tag))
    );
  } else return jobs.value;
});

const addFilterTag = (tag) => {
  if (!filterTags.value.includes(tag)) {
    filterTags.value.push(tag);
  }
};

const deleteTag = (tag) => {
  filterTags.value = filterTags.value.filter((el) => el !== tag);
};

const equals = (a, b) => a.length === b.length && a.every((v, i) => v === b[i]);
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
