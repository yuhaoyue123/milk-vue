<template>
  <div id="HelloWorld" style="height: 2500px">
    <el-container>
      <el-header class="header" style="padding: 0px">
        <vheader />
      </el-header>

      <el-header>
        <div class="header-left">
          <img src='../image/logo.jpg'>
        </div>
        <div class="header-right">
          <span class="huan-login">列表</span>
        </div>
      </el-header>
      <div style="width:100%;border-top: 1px solid  #CCCCCC;transform: scaleY(1);margin-top: 50px"></div>

      <div class="commodity-biaoqian">
        <div class="commodity-biaoqian-top">
           <span class="commodity-all-name">全部商品></span>
        </div>
      </div>

      <div class="list-boxs">
        <!--<div class="list-left">-->
          <el-aside style="width: 200px;float: left">
            <el-row class="tac">
              <el-col :span="24">
                <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
                         unique-opened
                         router>
                  <el-submenu index="1">
                    <template slot="title">

                      <span>新鲜牛奶</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="FreshMilk" style="min-width: 0px">致优</el-menu-item>
                      <el-menu-item index="FreshYogurt">优倍</el-menu-item>
                      <el-menu-item index="1-3">纯鲜牛奶</el-menu-item>
                      <el-menu-item index="1-4">农场恋人</el-menu-item>
                      <el-menu-item index="1-5">儿童牛奶</el-menu-item>
                      <el-menu-item index="1-6">经典玻璃瓶</el-menu-item>
                      <el-menu-item index="1-7">香浓高钙</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                  <el-submenu index="2">
                    <template slot="title">
                      <span>新鲜酸奶</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="2-1">白雪</el-menu-item>
                      <el-menu-item index="2-2">畅优</el-menu-item>
                      <el-menu-item index="2-3">如实</el-menu-item>
                      <el-menu-item index="2-4">赏味</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                  <el-submenu index="2">
                    <template slot="title">
                      <span>儿童乳品</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="2-1">白雪</el-menu-item>
                      <el-menu-item index="2-2">畅优</el-menu-item>
                      <el-menu-item index="2-3">如实</el-menu-item>
                      <el-menu-item index="2-4">赏味</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                  <el-submenu index="2">
                    <template slot="title">
                      <span>进口商品</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="2-1">白雪</el-menu-item>
                      <el-menu-item index="2-2">畅优</el-menu-item>
                      <el-menu-item index="2-3">如实</el-menu-item>
                      <el-menu-item index="2-4">赏味</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                  <el-submenu index="2">
                    <template slot="title">
                      <span>光明果汁</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="2-1">白雪</el-menu-item>
                      <el-menu-item index="2-2">畅优</el-menu-item>
                      <el-menu-item index="2-3">如实</el-menu-item>
                      <el-menu-item index="2-4">赏味</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                  <el-submenu index="2">
                    <template slot="title">
                      <span>经典礼盒</span>
                    </template>
                    <el-menu-item-group>
                      <el-menu-item index="2-1">白雪</el-menu-item>
                      <el-menu-item index="2-2">畅优</el-menu-item>
                      <el-menu-item index="2-3">如实</el-menu-item>
                      <el-menu-item index="2-4">赏味</el-menu-item>
                    </el-menu-item-group>
                  </el-submenu>

                </el-menu>
              </el-col>
            </el-row>
          </el-aside>
        <!--</div>-->
        <!--<div class="list-main">-->
          <el-main style="float: left;width: 1000px">
            <router-view></router-view>
          </el-main>
        <!--</div>-->
      </div>
    </el-container>
  </div>
</template>

<script>
  import Header from '@/components/Header'
    export default {
        name: "commodity",
      components: {
        'vheader': Header
      },
      data () {
        return {
          menu: menu
        }
      },
      methods: {
        handleOpen(key, keyPath) {
          console.log(key, keyPath)
        },
        handleClose(key, keyPath) {
          console.log(key, keyPath)
        }
      }
    }

</script>

<style rel="stylesheet/scss" lang="scss">
  .header-left{
    margin-left: 350px;
    float: left;
  }
  .header-right{
    width: 200px;
    height: 35px;
    border-left: 1px solid #cecdcd;
    margin-left: 50px;
    margin-top: 24px;
    float: left;
  }
  .huan-login{
    margin-left: 20px;
    line-height: 35px;
    font-size: 25px;
    font-family: '黑体';
    color: #979997;
  }
  .commodity-biaoqian{
    width: 100%;
    height: 94px;
  }
  .commodity-biaoqian-top{
    width: 1200px;
    height: 49px;
    margin: auto;
    border-bottom: 1px solid #b9b9b9;
  }
  .commodity-all-name{
    line-height: 49px;
    color: #405aa8;
    font-size: 14px;
    font-weight: 600;
    float: left;
  }
  .list-boxs{
    width: 1200px;
    height: 1308px;
    margin: auto;
  }
  span{
    float: left;
  }
  .list-left{
    width: 198px;
    height: 741px;
    float: left;
  }
  .list-main{
    width: 960px;
    height: 1308px;
    float: left;
    margin-left: 42px;
  }
  .over-hide{
    overflow: hidden;
  }
  .el-menu-item{
    /*float: left;*/
  }
</style>
