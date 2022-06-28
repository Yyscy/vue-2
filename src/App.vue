<template>
  <div>
    <div>
      <span>求[{ a: 100 }, { a: 20 }, { a: -10 }]中a的和</span><br />
      <button @click="he">数组内求和</button>
      <span>和为：{{ sum }}</span>
    </div>
    <br />
    <br />
    <br />
    <div>
      <span>输入字母在“asdasdasdadasdasd”中查看出现次数</span><br />
      <input type="text" v-model="shuru" />
      <button @click="cazhao(shuru)">查找</button><br />
      <span>出现次数{{ chishu }}</span>
    </div>
    <br />
    <br />
    <br />
    <div>
      <span>
        输入带参的路径<br />
        实例 “http://www.baidu.com?name=zhangsan&age=18&sex=nan#” </span
      ><br />
      <input type="text" v-model="urls" />
      <button @click="jiexi(urls)">参数解析</button>
      <span>解析：{{ urln }}</span>
    </div>
    <br />
    <br />
    <br />
    <div>
      <span> 模拟实现v-model </span><br />
      <input type="text" :value="value1" @input="inputsj($event)" /> <br />
      <span>参数：{{ value1 }}</span>
    </div>
    <br />
    <br />
    <br />
    <div>
      <span>反转字符串</span>
      <p>{{ message }}</p>
      <button @click="fanz">反转</button>
    </div>
    <br />
    <br />
    <br />
    <div>
      <zhed> </zhed>
    </div>
    <br />
    <br />
    <br />
    <div>
      <baidu> </baidu>
    </div>
  </div>
</template>

<script>
import zhed from './zhedemianban.vue'

import baidu from './baiduhuanfu.vue'
export default {
  data() {
    return {
      arr: [{ a: 100 }, { a: 20 }, { a: -10 }],
      sum: '',
      str: 'asdasdasdadasdasd',
      shuru: '',
      chishu: '',
      urls: '',
      urln: {},
      value1: '请输入',
      message: 'HELLO, WORLD',
    }
  },
  methods: {
    he() {
      this.sum = this.arr.reduce((a, b) => {
        return a + b.a
      }, 0)
    },
    cazhao(zm) {
      this.chishu = this.str.split('').reduce((a, b) => {
        if (zm == b) {
          a++
        }
        return a
      }, 0)
    },
    jiexi(http) {
      this.urln = http
        .slice(http.indexOf('?') + 1, http.indexOf('#'))
        .split('&')
        .reduce((a, b) => {
          const [key, value] = b.split('=')
          a[key] = value
          return a
        }, {})
    },
    inputsj(e) {
      this.value1 = e.target.value
    },
    fanz() {
      this.message = this.message.split('').reverse().join('')
    },
  },
  components: {
    zhed: zhed,
    baidu: baidu,
  },
}
</script>

<style></style>
