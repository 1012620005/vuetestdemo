<template>
  <div>
    <h1 class="logo">cnodejs Api Test</h1>
    <ul class="list">
      <li v-for="item in lists" v-text="item.title" :id="item.id" @click="goToCon(item.id)"></li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      lists:[]
    }
  },
  created () {
    // 组件创建完后获取数据，这里和1.0不一样，改成了这个样子
    this.get_data()
  },
  methods: {
  	get_data: function(params) {
      var v = this
      if (!params) params = {}
      // 我们这里用全局绑定的 $api 方法来获取数据，方便吧~
      //v.$api.get('topics', params, function(r) {
       // v.lists = r.data
      //})
      this.$http.get('https://cnodejs.org/api/v1/topics').then(function(response){
      		// alert('sussess')
      		v.lists = response.data.data
      		
      }).catch(function(response){
      		// alert('error')
      })
    },
    goToCon: function(id) {
    	
    }
  }
}
</script>