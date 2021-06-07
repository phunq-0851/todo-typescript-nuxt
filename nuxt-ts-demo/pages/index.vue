<template>
  <div class="container">
    <div>
      <el-form ref="form" :model="form" label-width="120px">
        <el-form-item label="Name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">Create</el-button>
        </el-form-item>
      </el-form>

      <List :listData="list" />
    </div>
  </div>
</template>

<script lang="ts">
import {Component, Vue} from 'nuxt-property-decorator'
import List from '@/components/List.vue'

@Component({
  components: { List }
})

export default class MyNuxt extends Vue {
  form = {
    name: ''
  }

  list = [
  {
    name: 'Tom',
  },
  {
    name: 'Phu',
  },
  {
    name: 'Thuy',
  },
  {
    name: 'Thuy A',
  }]

  onSubmit () {
    if (this.form.name) {
      this.list.push({name: this.form.name})

      this.form.name = ''
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  text-align: center;
  margin-top: 30px;
}
</style>
