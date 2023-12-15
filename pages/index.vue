<!-- pages/index.vue -->
<template>
  <div>
    <GitHubIssuesList :issues="issues" />
  </div>
</template>

<script>
import GitHubIssuesList from '~/components/GitHubIssuesList.vue';

export default {
  components: {
    GitHubIssuesList,
  },
  data() {
    return {
      issues: [],
    };
  },
  async asyncData({ $http }) {
    const owner = 'PrajwalThorat';
    const repo = 'Email-Notification-Service.git';
    const headers = {
      'Accept':'application/vnd.github+json',
      'Authorization':'Bearer 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',
      'X-GitHub-Api-Version':'2022-11-28'
    }

    try {
      const response = await $http.get(`https://api.github.com/repos/${owner}/${repo}/issues`, {headers});
      return { issues: response.data };
    } catch (error) {
      console.error('Error fetching GitHub issues:', error);
      return { issues: [] };
    }
  },
};
</script>

