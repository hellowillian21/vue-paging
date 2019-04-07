<template>
  <div class="list">
    <template v-if="count">
      <ul>
        <li v-for="item in items" :key="item.id">...</li>
      </ul>
      <Paging
        :perPages='perPages'
        :pageIndex="currentPage"
        :total="count"
        :pageSize="pageSize"
        @change="pageChange"
      >
      </Paging>
    </template>
  </div>
</template>
<script>
import Paging from "./components/Paging";
export default {
  //显示的声明组件
  name: 'app',
  components: {
    Paging
  },
  data() {
    return {
      perPages: 5,
      pageSize: 20, //每页显示20条数据
      currentPage: 1, //当前页码
      count: 200, //总记录数
      items: []
    };
  },
  methods: {
    //获取数据
    getList() {

    },

    //从paging组件传递过来的当前page
    pageChange(page) {
      this.currentPage = page;
      this.getList();
    }
  },
  mounted() {
    //请求第一页数据
    this.getList();
  }
};
</script>

<style>
.list {
  display: flex;
  justify-content: center;
}
</style>
