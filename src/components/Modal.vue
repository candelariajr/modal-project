<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{sale: theme ==='sale'}">
      <slot>Default Content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  //This brings in the value from App.vue into the scope of this component
  //Props are not needed if the values are being passed in the form of a template passed through
  //to the component with a slot
  props: ['theme'],
  methods: {
    closeModal() {
      this.$emit('close')
    }
  }
}
</script>

<style>
/*
NOTE- regular CSS works as well
 */
.modal{
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}

.backdrop{
  top: 0;
  position: fixed;
  background: rgba(0,0,0,0.5);
  width: 100%;
  height:100%;
}

.modal.h1{
  color: #03cfb4;
  border: none;
  padding: 0;
}

.modal.sale{
  background: crimson;
  color: white;
}

.modal.actions{
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .actions a{
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal.sale h1{
  color: white;
}
</style>