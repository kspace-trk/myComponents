<template>
  <div class="pagination">
    <button @click="prev()">&lt;</button>
    <div v-if="pageNumArray[0] > 2" class="num" @click="toPageNum(1)">1</div>
    <div v-if="pageNumArray[0] > 2" class="num">...</div>
    <div v-for="elem of pageNumArray" :key="elem" >
      <div v-if="elem === pageNum" class="num red" @click="toPageNum(elem)">{{ elem }}</div>
      <div v-else class="num" @click="toPageNum(elem)">{{ elem }}</div>
    </div>
    <div v-if="pageNumArray[pageNumArray.length - 1] !== pageMaxNum" class="num">...</div>
    <div v-if="pageNumArray[pageNumArray.length - 1] !== pageMaxNum" class="num" @click="toPageNum(pageMaxNum)">{{ pageMaxNum }}</div>
    <button @click="next()">></button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      pageNum: 1,
      pageMaxNum: 12,
      pageNumArray: []
    }
  },
  created () {
    if (this.pageMaxNum <= 5) {
      // 記事数が5以内のときは、配列に数字が5つ入る
      for (let i = this.pageNum; i < this.pageNum + 5; i++) {
        this.pageNumArray.push(i)
      }
    } else {
      // 記事数が6以上のときは、配列に数字が3つ入る
      for (let i = this.pageNum; i < this.pageNum + 3; i++) {
        this.pageNumArray.push(i)
      }
    }
    console.log(this.pageNumArray)
  },
  methods: {
    next () {
      if (this.pageNum < this.pageMaxNum) {
        this.pageNum++
      }
      this.formatPageNum(this.pageNum)
    },
    prev () {
      if (this.pageNum > 1) {
        this.pageNum--
      }
      this.formatPageNum(this.pageNum)
    },
    toPageNum (n) {
      this.formatPageNum(n)
    },
    formatPageNum (n) {
      if (n <= 3) {
        // 1 2 3 ... 6のような場合
        this.pageNumArray = []
        this.pageNumArray.push(1)
        this.pageNumArray.push(2)
        this.pageNumArray.push(3)
      } else if (n > 3 && n < this.pageMaxNum - 2) {
        // 1 ... 3 4 5 ... 7のような場合
        this.pageNumArray = []
        this.pageNumArray.push(this.pageNum - 1)
        this.pageNumArray.push(this.pageNum)
        this.pageNumArray.push(this.pageNum + 1)
      } else if (n > this.pageMaxNum - 2) {
        // 1 ... 5 6 7のような場合
        this.pageNumArray = []
        this.pageNumArray.push(this.pageMaxNum - 2)
        this.pageNumArray.push(this.pageMaxNum - 1)
        this.pageNumArray.push(this.pageMaxNum - 0)
      }
      console.log(this.pageNum)
      console.log(this.pageNumArray)
    }
  }
}
</script>

<style scoped>
.pagination {
  max-width: 400px;
  width: 90%;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
}

button {
  margin: 0 1rem;
  cursor: pointer;
}

.num {
  margin: 0 1rem;
  cursor: pointer;
}

.red {
  color: red;
}
</style>