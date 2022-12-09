<template>
  <div class="component">
    <section class="row">
      Jobs Page
    </section>
  </div>
</template>


<script>
import { AppState } from '../AppState';
import { computed, reactive, onMounted } from 'vue';
import { logger } from "../utils/Logger.js";
import Pop from "../utils/Pop.js";
import { jobsService } from "../services/JobsService.js";
export default {
  setup() {
    async function getJobs() {
      try {
        await jobsService.getJobs()
      } catch (error) {
        logger.error(error)
        Pop.error(error)
      }
    }

    onMounted(() => {
      getJobs()
    })
    return {
      jobs: computed(() => AppState.jobs)
    }
  }
};
</script>


<style lang="scss" scoped>

</style>
