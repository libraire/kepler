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
      <p class="title">"Hello world" @ <span>Libra</span></p>
      <p>快乐的事情正在发生！</p>
      <p>这里的内容需要你们补充...</p>
      <p>老夫今晚肝不动了</p>
      <p>久了不写代码，手非常生👋</p>
      <p>目标是<u>星辰大海</u></p>
      <div class="img_libra">
        <img src="../assets/libra.png" alt="back"/>
      </div>
    </div>

    <div class="libra_cards">
      <div class="libra_card">
        <div class="card_content">
          <font-awesome-icon icon="fa-solid fa-user-secret" />
          <div class="keyword">develop</div>
        </div>
      </div>
      <div class="libra_card">
        <div class="card_content">
          <font-awesome-icon icon="fa-brands fa-weebly" />
          <div class="keyword">Woop!</div>
        </div>
      </div>
      <div class="libra_card">
        <div class="card_content">
          <font-awesome-icon icon="fa-brands fa-algolia" />
          <div class="keyword">For HJW</div>
        </div>
      </div>
    </div>

    <div class="footer">
      <p>Made with ❤️ by LIBRA</p>
    </div>

<!--    <div class="hello" v-if="step === 'welcome'">-->
<!--      <input v-model="userName" placeholder="输入姓名开始答题"/>-->
<!--      <button @click="begin">进入答题{{msg}}</button>-->
<!--    </div>-->
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
  height: 100%;
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
  border-bottom: 2px solid #fff;
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
.content .img_libra {
  float: right;
  margin-top: -300px;
}
.content .img_libra img {
  width: 400px;
}

.libra_cards {
  margin-top: 160px;
  display: flex;
  align-items:center;
  justify-content:center;
  height: 140px;
}
.libra_cards .libra_card {
  background: #fff;
  color: #33aaee;
  box-shadow: inset 0px 0 30px 0 rgb(0 0 0 / 20%);
  width: 100%;
  height: 100%;
  text-align: center;
  position: relative;
}
.libra_cards .libra_card:hover {
  box-shadow: inset 0px 0 30px 0 rgb(0 0 0 / 30%);
}

.libra_cards .libra_card .card_content {
  position: relative;
  top:50%;
  transform:translateY(-50%);
}
.libra_cards .libra_card .card_content:hover {
  color: #00e27b;
  cursor: pointer;
}

.libra_cards .libra_card .card_content .keyword {
  font-weight: 600;
}

.libra_cards .libra_card svg{
  width: 60px;
  height: 60px;
}

.footer {
  position: absolute;
  bottom: 20px;
  text-align: center;
  width: 100%;
}
</style>
