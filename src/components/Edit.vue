<template>
  <div 
    class="post-edit"
    :class="isModalOpen ? ' active' : ''"
  >
    <div class="overflow"></div>
    <div class="post-edit-card">
      <div class="card-title">
        <h4>Düzenle</h4>
        <i
          @click="closeModal()" 
          class="fas fa-times"
        ></i>
      </div>
      <div class="card-content">
        <div class="form-group">
          <label for="form-title">Title</label>
          <input 
            id="form-title"
            class="form-control"
            type="text"
            v-model="item.title"
          >
        </div>
        <div class="form-group">
          <label for="form-body">Body</label>
          <textarea 
            id="form-body"
            style="height: 100px"
            class="form-control"
            v-model="item.body"
          ></textarea>
        </div>
      </div>
      <div class="card-actions">
        <a
          @click="update()" 
          class="btn"
        >Güncelle</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  props: {
    item: Object,
    isModalOpen: Boolean
  },
  methods: {
    async update() {
      const { data } = await axios.put(
        `https://jsonplaceholder.typicode.com/posts/${this.item.id}`,
        this.item
      );

      if(data) {
        this.closeModal();
        console.log(data);
      }
    },
    closeModal() {
      this.$emit('closed');
    }
  }
}

</script>

<style lang="scss">
  .post-edit.active {
    .overflow {
      z-index: 1;
      visibility: visible;
      opacity: 1;
    }

    .post-edit-card {
      z-index: 1;
      opacity: 1;
      transform: translateY(25%);
    }
  }

  .overflow {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.3);
    top: 0;
    left: 0;
    position: fixed;
    z-index: -1;
    opacity: 0;
    visibility: hidden;
  }

  .post-edit-card {
    position: fixed;
    padding: 2rem 0;
    width: 50%;
    box-shadow: 0px 15px 35px rgba(50, 50, 93, 0.1), 0px 5px 15px rgba(0, 0, 0, 0.07);
    border-radius: 4px;
    left: 25%;
    top: 0%;
    background-color: #FFF;
    transition: 200ms ease-out;
    z-index: -1;
    opacity: 0;

    .card-title {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      padding: 0 2rem;
      border-bottom: 1px solid #E9ECEF;

      i {
        display: flex;
        align-items: center;
        font-size: 1.25rem;
        margin: auto 0;
      }
    }

    .card-content {
      padding: 2rem 2.2rem;
      border-bottom: 1px solid #E9ECEF;
    }

    .card-actions {
      a {
        background-color: #11CDEF;
        color: #FFF;
        margin-left: 2rem;
        margin-top: 1rem;
      }
    }
  }
</style>