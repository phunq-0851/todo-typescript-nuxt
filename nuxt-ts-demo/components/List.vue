<template>
  <div>
  <el-table
    :data="listData"
    style="width: 100%">
    <el-table-column
      label="Name"
      width="200">
      <template slot-scope="scope">
        <el-popover trigger="hover" placement="top">
          <p>Name: {{ scope.row.name }}</p>
          <div slot="reference" class="name-wrapper">
            <el-tag size="medium">{{ scope.row.name }}</el-tag>
          </div>
        </el-popover>
      </template>
    </el-table-column>
    <el-table-column
      label="Operations"
      width="200">
      <template slot-scope="scope">
        <el-button
          size="mini"
          @click="handleEdit(scope.$index, scope.row)">Edit</el-button>
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)">Delete</el-button>
      </template>
    </el-table-column>
  </el-table>
  </div>
</template>

<script>
import {Component, Vue, Prop} from 'nuxt-property-decorator'
@Component
export default class MyCom extends Vue {
  @Prop({ type: Array, required: true, default: () => { return [] } }) listData

  handleEdit(index, row) {
    console.log(index, row);
  }

  handleDelete(index, row) {
    console.log(index, row);
  }
  }
</script>
