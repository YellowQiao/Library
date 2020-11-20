<template>
  <div class="container">
    <!-- 选择器 -->
    <div class="multiSelector">
      <!-- 选择器1 -->
      <span class="pre1">国家</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in nation"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
      <!-- 选择器2 -->
      <span class="pre"> 类型</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in type"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
      <!-- 选择器3 -->
      <span class="pre"> 篇幅</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in length"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
      <!-- 选择器4 -->
      <span class="pre"> 主题</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in theme"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
      <div class="searchButton">
        <el-button type="primary" icon="el-icon-search">搜索</el-button>
      </div>

      <div class="keywordSearch">
        <el-input
          class="inputText"
          v-model="input"
          placeholder="请输入内容"
        ></el-input>
        <el-button type="primary"> 搜索</el-button>
      </div>

      <div class="borrowInfo">
        <el-card class="box-card">
          <div v-for="o in 4" :key="o" class="text item">
            {{ "列表内容 " + o }} {{"11111"+ o}} <button>11</button>
          </div>
        </el-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
      nation: [
        {
          value: "选项1",
          label: "黄金糕",
        },
        {
          value: "选项2",
          label: "双皮奶",
        },
        {
          value: "选项3",
          label: "蚵仔煎",
        },
        {
          value: "选项4",
          label: "龙须面",
        },
        {
          value: "选项5",
          label: "北京烤鸭",
        },
      ],
      type: [
        {
          value: "选项1",
          label: "黄金糕",
        },
        {
          value: "选项2",
          label: "双皮奶",
        },
        {
          value: "选项3",
          label: "蚵仔煎",
        },
        {
          value: "选项4",
          label: "龙须面",
        },
        {
          value: "选项5",
          label: "北京烤鸭",
        },
      ],
      length: [
        {
          value: "选项1",
          label: "黄金糕",
        },
        {
          value: "选项2",
          label: "双皮奶",
        },
        {
          value: "选项3",
          label: "蚵仔煎",
        },
        {
          value: "选项4",
          label: "龙须面",
        },
        {
          value: "选项5",
          label: "北京烤鸭",
        },
      ],
      theme: [
        {
          value: "选项1",
          label: "黄金糕",
        },
        {
          value: "选项2",
          label: "双皮奶",
        },
        {
          value: "选项3",
          label: "蚵仔煎",
        },
        {
          value: "选项4",
          label: "龙须面",
        },
        {
          value: "选项5",
          label: "北京烤鸭",
        },
      ],
      value: "",
    };
  },
};
</script>

<style scoped>
.multiSelector {
  margin-top: 50px;
}
.multiSelector .pre {
  margin-left: 5px;
  font-size: 30px;
  font-family: "FZZhaoMFXSJF";
}
.multiSelector .pre1 {
  font-size: 30px;
  font-family: "FZZhaoMFXSJF";
}
.searchButton {
  margin-left: 950px;
  margin-top: 5px;
}
.inputText {
  width: 250px;
  margin-left: 650px;
  margin-top: 20px;
}
.container {
  margin-left: -200px;
}
</style>
