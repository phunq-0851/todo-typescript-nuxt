<template>
  <div>
  <el-table
    :data="cloneData"
    style="width: 100%">
    <el-table-column
      label="Name"
      width="200">
      <template slot-scope="scope">
        <el-popover v-if="edit !== scope.$index" trigger="hover" placement="top">
          <p>Name: {{ scope.row.name }}</p>
          <div slot="reference" class="name-wrapper">
            <el-tag size="medium">{{ scope.row.name }}</el-tag>
          </div>
        </el-popover>
        <div v-else>
          <el-input v-model="scope.row.name"></el-input>
        </div>
      </template>
    </el-table-column>
    <el-table-column
      label="Operations"
      width="200">
      <template slot-scope="scope">
        <div v-if="edit !== scope.$index">
          <el-button
            size="mini"
            @click="handleEdit(scope.$index)">Edit</el-button>
          <el-button
            size="mini"
            type="danger"
            @click="handleDelete(scope.$index)">Delete</el-button>
        </div>
        <div v-else>
          <el-button
            size="mini"
            @click="save(scope.$index, scope.row)">Save</el-button>
          <el-button
            size="mini"
            type="danger"
            @click="save(scope.$index, scope.row)">Cancel</el-button>
        </div>
      </template>
    </el-table-column>
  </el-table>
  </div>
</template>

<script>
import {Component, Vue, Prop} from 'nuxt-property-decorator'
@Component
export default class MyList extends Vue {
  @Prop({ type: Array, required: true, default: () => { return [] } }) listData

  cloneData = []
  edit = -1

  handleEdit(index) {
    this.edit = index
  }

  handleDelete(index) {
    this.cloneData.splice(index, 1)
  }

  save (index, row) {
    this.edit = -1
  }

  mounted () {
    this.cloneData = this.listData
  }
}
</script>
