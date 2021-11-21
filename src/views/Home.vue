<template>
  <div class="post-list">
    <Edit 
      :item="itemEdit" 
      :isModalOpen="isModalOpen"
      @closed="closeModal"
    />
    <div 
      v-for="post in posts"
      :key="post.id"
      class="post"
    >
      <div class="post-info">
        <span class="number">{{ post.id }}</span> {{ post.title }}
      </div>
      <div class="post-actions">
        <router-link
          :to="`/post/${post.id}`"
          class="action-button details"
        >
          DETAY
        </router-link>
        <a
          @click="edit(post.id)"
          class="action-button edit"
        >
          DÜZENLE
        </a>
        <a
          @click="remove(post.id)" 
          class="action-button delete"
        >
          SİL
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Edit from '../components/Edit';

export default {
  name: 'Home',
  components: {
    Edit
  },
  created: function(){
    this.fetchPosts();
  },
  methods: {
    async fetchPosts() {
      const { data } = await axios.get('https://jsonplaceholder.typicode.com/posts');
      if(data.length) {
        this.posts = data;
      }
    },
    async edit(id) {
      const { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts/${id}`); 

      if(data) {
        this.itemEdit = data;
        this.isModalOpen = true;
      }
    },
    async closeModal() {
      this.isModalOpen = false;
      await this.fetchPosts();
    }
  },
  data: function() {
    return {
      posts: [],
      itemEdit: {},
      isModalOpen: false
    }
  }
}
</script>

<style lang="scss">
  ::-webkit-scrollbar {
    width: 10px;
  }

  ::-webkit-scrollbar-track {
    background: #f1f1f1;
  }

  ::-webkit-scrollbar-thumb {
    background: #888;
  }

  ::-webkit-scrollbar-thumb:hover {
    background: #555;
  }
  
  .post-list {
    display: block;
    width: 100%;
    height: 100%;
    background-color: #FFF;
    overflow-y: scroll;


    .post {
      display: flex;
      height: 80px;
      align-items: center;
      justify-content: space-between;
      margin: 0 2rem;
      border-bottom: .1rem solid #0000001A;

      .post-info {
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;

        .number {
          font-weight: bold;
        }
      }

      .post-actions {
        height: 100%;
        display: flex;
        align-items: center;

        a {
          text-decoration: none;
        }

        .action-button {
          cursor: pointer;
          box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.08), 0px 4px 4px rgba(50, 50, 93, 0.11);
          border-radius: 3px;
          color: #FFF;
          padding: 0.75rem 1.25rem;
          margin: 0 0.25rem;

          &.details {
            background-color: #5E72E4;
          }

          &.edit {
            background-color: #2DCE89;
          }

          &.delete {
            background-color: #FB6340;
          }
        }
      }
    }
  }

</style>