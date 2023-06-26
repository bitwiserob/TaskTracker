<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>ID</label>
      <input type="number" v-model="id" name="id" placeholder="Add Id" />
    </div>
    <div class="form-control">
      <label>Title</label>
      <input type="text" v-model="title" name="title" placeholder="Add Title" />
    </div>
    <div class="form-control">
      <label>Description</label>
      <input type="text" v-model="desc" name="desc" placeholder="Add Description" />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      id: '',
      title: '',
      desc:'',
      reminder: false,
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.title) {
        alert('Please add a task')
        return
      }

      const newTask = {
        // id: Math.floor(Math.random() * 100000),
        id: this.id,
        title: this.title,
        desc: this.desc,
        reminder: this.reminder,
      }

      this.$emit('add-task', newTask)
      this.id= Math.floor(Math.random() * 100000);
      this.title = ''
      this.desc = ''
      this.reminder = false
    },
  },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
