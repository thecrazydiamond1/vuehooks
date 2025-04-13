<template>
  <div>
    <button @click="showList = !showList">
      {{ showList ? 'Hide' : 'Show' }} User List
    </button>

    <UserList v-if="showList" />
  </div>
</template>

<script>
import UserList from './components/UserList.vue';

export default {
  components: {
    UserList
  },
  data() {
    return {
      showList: true,
    };
  },
};
</script>

<!-- When showList is true, UserList.vue is mounted.
When showList becomes false, Vue unmounts it — and your console will show:
1. beforeUnmount - Clearing interval.
2. unmounted - Component is destroyed.
Meanwhile, every time the users are fetched and DOM updates, you’ll also see the full lifecycle logs in order. -->