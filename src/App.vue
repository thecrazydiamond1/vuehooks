<template>
  <div>
 

    <button @click="currentComponent = currentComponent === 'UserList' ? 'MountApiCall' : 'UserList'">
      Toggle User List
    </button>
    <component :is="currentComponent"></component>
  </div>
</template>

<script>
import UserList from './components/UserList.vue';
import MountApiCall from './components/MountApiCall.vue';
export default {
  components: {
    UserList,
    MountApiCall,
  },
 data(){
  return{
    currentComponent: 'UserList',
  }
 }
};
</script>

