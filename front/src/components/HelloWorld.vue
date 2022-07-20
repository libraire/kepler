<template>
  <div class="container">
    <div class="header">
      <img src="../assets/logo_white.png" alt="Libra"/><span>Libra</span>

      <ul>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Docs</a></li>
      </ul>
    </div>
    <div class="content">
      <p class="title">"Hello world" at <span>Libra</span></p>
      <p>快乐的事情正在发生！</p>
      <p>这里的内容需要你们补充...</p>
      <p>老夫今晚肝不动了</p>
      <p>久了不写代码，手非常生👋</p>
    </div>
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

.container {
  max-width: 1280px;
  min-width: 600px;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
}
.header {
  text-align: left;
  padding: 10px 20px;
  display: flex;
  align-items: center;
}
.header img {
  width: 40px;
  height: 40px;
}
.header span {
  font-size: 32px;
  font-weight: bold;
  margin-top: 2px;
  margin-left: 8px;
}
.header ul {
  margin: 0 80px;
  line-height: 40px;
}
.header ul li {
  font-size: 26px;
  margin-top: 8px;
  margin-left: 20px;
}
.content {
  margin-top: 60px;
  padding: 10px;
}
.content p {
  font-size: 18px;
}
.content .title {
  font-size: 40px;
  font-weight: bold;
}
.content .title>span {
  color: #00e27b;
}
</style>
