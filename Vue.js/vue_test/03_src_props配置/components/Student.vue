<template>
  <div>
    <h1>{{ msg }}</h1>
    <h2>学生性别：{{ name }}</h2>
    <h2>学生性别：{{ sex }}</h2>
    <h2>学生年龄：{{ myAge+1 }}</h2>
    <button @click="updateAge">尝试修改收到的年龄</button>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Student',
  data() {
    console.log(this);
    return {
      msg: 'I am a college student',
      myAge: this.age,
    }
  },
  methods: {
    updateAge() {
      this.myAge++;
    }
  },
  props: ['name', 'sex', 'age'], // 简单接收
  
  // 接受的同时对数据进行限制
  /* props: {
    name: String,
    age: Number,
    sex: String
  } */

  // 接收的同时对数据：进行类型限制 + 默认值的指定 + 必要性的限制
  /* props: {
    name: {
      type: String, // name 的类型是字符串
      required: true // name 是必要的
    },
    age: {
      type: Number,
      default: 99 // 默认值
    },
    sex: {
      type: String,
      required: true
    }
  } */
}
</script>
