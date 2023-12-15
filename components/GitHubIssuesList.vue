<!-- components/GitHubIssuesList.vue -->
<template>
    <div>
      <h1>GitHub Issues</h1>
      <ul class="issues-list">
        <li v-for="issue in issues" :key="issue.id">
          <a @click="openModal(issue)">
            {{ issue.title }}
          </a>
        </li>
      </ul>
      <Modal :issue="selectedIssue" v-if="showModal" @close="closeModal" />
    </div>
  </template>
  
  <script>
  import Modal from '~/components/Modal.vue';
  
  export default {
    components: {
      Modal,
    },
    props: {
      issues: {
        type: Array,
        default: () => [],
      },
    },
    data() {
      return {
        showModal: false,
        selectedIssue: null,
      };
    },
    methods: {
      openModal(issue) {
        this.selectedIssue = issue;
        this.showModal = true;
      },
      closeModal() {
        this.showModal = false;
        this.selectedIssue = null;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add your CSS styles for GitHubIssuesList.vue here */
  .issues-list {
    list-style-type: none;
    padding: 0;
  }
  
  .issues-list li {
    margin: 10px 0;
  }
  
  .issues-list a {
    text-decoration: none;
    color: #0366d6;
    cursor: pointer;
  }
  </style>
  