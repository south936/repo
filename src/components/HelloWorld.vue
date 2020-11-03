<template>
  <div class="container">
    <el-row>
      <el-col :span="12" :offset="6">
        <el-card>
          <el-container>
            <el-header>
              <el-input v-model="toDoSth" size="small"></el-input>
              <el-button
                type="success"
                @click="add()"
                size="small"
                icon="el-icon-edit"
                >新增</el-button
              >
            </el-header>
            <el-main>
              <div class="left" v-if="list.toString() !== ''">
                <el-row v-for="(item, index) in list" :key="index">
                  <el-col :span="2" :class="item.state ? 'yes' : ''">
                    <span @click="changeState(index, item.state)">
                      <el-checkbox v-model="item.state"></el-checkbox
                    ></span>
                  </el-col>
                  <el-col :span="12" :offset="1">{{ item.content }}</el-col>
                  <el-col :span="4">{{ item.createTime }}</el-col>
                  <el-col :span="5">
                    <i
                      class="el-icon-delete red"
                      size="mini"
                      @click="del(index)"
                    ></i>
                  </el-col>
                </el-row>
              </div>
              <el-alert
                width="85%"
                class="infoText"
                v-if="list.toString() === ''"
                title="所有的事情都做完了"
                :closable="false"
              >
              </el-alert>
            </el-main>
          </el-container>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      toDoSth: "",
      list: [],
      finishList: [],
    };
  },
  methods: {
    add() {
      console.log(this.toDoSth);
      if (this.toDoSth == "") {
        return this.$message.error("请输入代办事件");
      }
      this.list.unshift({
        state: false,
        content: this.toDoSth,
        createTime: new Date().toLocaleTimeString(),
      });
    },
    del(index) {
      this.list.splice(index, 1);
      console.log(this.list);
    },
    changeState(index, state) {
      this.list[index].state = !state;
      console.log(this.list[index].state);
    },
  },
};
</script>


<style lang="scss" scoped>
.container {
  // height: 100vh;
  .el-row {
    .el-header {
      height: 10vh;
      .el-input {
        width: 50%;
        margin-left: 10%;
      }
      .el-button {
        // width: 20%;
      }
    }
    .el-main {
      height: 80vh;
      place-content: center;
      place-items: center;
      .left {
        // float: left;
        width: 98%;
        padding: 2%;
        // background: #000;
        .el-row > * {
          height: 10%;
          // line-height: 10%;
          .yes {
            color: #8c8c8c;
          }
          .red {
            color: red;
          }
        }
      }
      .infoText {
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
      }
      .el-alert {
        width: 40%;
      }
    }
  }
}
</style>
