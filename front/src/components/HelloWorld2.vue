<template>
  <div class="hello" v-if="step === 'welcome'">
    <input v-model="userName" placeholder="输入姓名开始答题"/>
    <button @click="begin">进入答题{{msg}}</button>
  </div>
  <div v-if="step === 'answer'">
    <div>
      {{ques[index].title}}
    </div>
    <div>
      <ul>
        <li v-for="item in ques[index].items" v-bind:key="item.id">{{item.item}}</li>
      </ul>
    </div>
    <div>
      <button @click="next">下一题</button>
    </div>
  </div>
  <div v-if="step === 'result'">
    恭喜🎉 {{result}} 分
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      userName: '',
      step: 'welcome',
      index: 0,
      ques: [],
      result: 100
    }
  },
  methods: {
    begin() {
      var ques = "[{\"id\": 1, \"title\": \"题目1\", \"items\": [{\"id\": 1, \"item\": \"选项A\"}, {\"id\": 2, \"item\": \"选项B\"},{\"id\": 3, \"item\": \"选项C\", \"right\": 1}]},\n" +
          "\n" +
          "{\"id\": 1, \"title\": \"题目2\", \"items\": [{\"id\": 1, \"item\": \"选项A2\"}, {\"id\": 2, \"item\": \"选项B2\"},{\"id\": 3, \"item\": \"选项C2\", \"right\": 1}]}]";
      var queJSON = JSON.parse(ques);
      console.log(queJSON);
      this.ques = queJSON;
      this.step = 'answer';
    },
    next() {
      if (this.ques.length > this.index + 1) {
        this.index++;
      } else {
        this.step = 'result';
        this.result = 90;
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
