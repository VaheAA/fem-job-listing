<template>
  <Transition>
    <div class="jobs__filter" :tagsList="tagsList" v-if="tagsList.length">
      <ul class="jobs__filter-tags">
        <li class="jobs__filter-item" v-for="tag in tagsList" :key="tag">
          <span>{{ tag }}</span>
          <button class="close" @click="deleteTag(tag)">
            <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14">
              <path
                fill="#FFF"
                fill-rule="evenodd"
                d="M11.314 0l2.121 2.121-4.596 4.596 4.596 4.597-2.121 2.121-4.597-4.596-4.596 4.596L0 11.314l4.596-4.597L0 2.121 2.121 0l4.596 4.596L11.314 0z"
              />
            </svg>
          </button>
        </li>
      </ul>
    </div>
  </Transition>
</template>

<script setup>
const props = defineProps({
  tagsList: Array
});

const emit = defineEmits(['deleteTag']);

const deleteTag = (tag) => {
  emit('deleteTag', tag);
};
</script>

<style lang="scss">
.jobs__filter {
  background-color: #fff;
  min-height: 50px;
  border-radius: 5px;
  padding: 15px 45px;
  box-shadow: 0px 0px 15px 5px rgba(0, 0, 0, 0.1);
  margin-top: -30px;

  &-tags {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 15px;
  }
  &-item {
    display: flex;
    align-items: center;
    height: 30px;
    border-radius: 5px;
    background-color: $bgLightCyan;

    span {
      padding: 7px;
      font-size: 16px;
      color: $primaryDarkCyan;
      font-weight: bold;
      position: relative;
      z-index: 1;
      transition: all 0.3s ease;
    }
    .close {
      border: none;
      padding: 7px;
      height: 100%;
      background-color: $primaryDarkCyan;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      border-top-right-radius: 5px;
      border-bottom-right-radius: 5px;
      cursor: pointer;
      transition: all 0.3s ease;
      position: relative;
      z-index: 2;

      &::after {
        content: '';
        position: absolute;
        width: 100%;
        height: 100%;
        border-radius: 5px;
        top: 0;
        left: 0;
        background-color: transparent;
        opacity: 0;
        z-index: -1;
        transition: all 0.3s ease;
      }

      &:hover::after {
        background-color: $veryDarkCyan;
        opacity: 1;
      }
    }
  }
}
</style>
