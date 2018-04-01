<template>
  <div id="dataManage">
    <div class="leftWrapper">
      <div class="leftContent">
        <div class="topWrapper">
          <div class="img">
            <img src="./../assets/imgs/home_photo.png"/>
          </div>
          <div class="info">
            <span>小花</span>
          </div>
        </div>
        <div class="bottomWrapper">
          <ul class="layui-nav layui-nav-tree" lay-filter="test">
            <li class="layui-nav-item layui-nav-itemed">
              <a href="javascript:;">默认展开</a>
              <dl class="layui-nav-child">
                <dd><a href="javascript:;">选项1</a></dd>
                <dd><a href="javascript:;">选项2</a></dd>
                <dd><a href="">跳转</a></dd>
              </dl>
            </li>
            <li class="layui-nav-item">
              <a href="javascript:;">解决方案</a>
              <dl class="layui-nav-child">
                <dd><a href="">移动模块</a></dd>
                <dd><a href="">后台模版</a></dd>
                <dd><a href="">电商平台</a></dd>
              </dl>
            </li>
            <li class="layui-nav-item"><a href="">产品</a></li>
            <li class="layui-nav-item"><a href="">大数据</a></li>
          </ul>
        </div>
      </div>
    </div>
    <div class="rightWrapper">
      <div class="layui-tab layui-tab-card" lay-allowclose="true">
        <ul class="layui-tab-title">
          <li class="layui-this">网站设置</li>
          <li>用户基本管理</li>
          <li>权限分配</li>
          <li>商品管理</li>
          <li>订单管理</li>
        </ul>
        <div class="layui-tab-content" style="height: 150px;">
          <div class="layui-tab-item layui-show">
            <div class="title">网站设置</div>
            <div class="tableWrapper">
              <!--<table lay-even class="layui-hide" lay-skin="nob" id="test"></table>-->
              <table-com></table-com>
            </div>
          </div>
          <div class="layui-tab-item">2</div>
          <div class="layui-tab-item">3</div>
          <div class="layui-tab-item">4</div>
          <div class="layui-tab-item">5</div>
          <div class="layui-tab-item">6</div>
        </div>

      </div>
    </div>



    <!--<form class="layui-form" action="">-->
      <!--<div class="layui-form-item">-->
        <!--<label class="layui-form-label">输入框</label>-->
        <!--<div class="layui-input-block">-->
          <!--<input type="text" name="title" required  lay-verify="required" placeholder="请输入标题" autocomplete="off" class="layui-input">-->
        <!--</div>-->
      <!--</div>-->
      <!--<div class="layui-form-item">-->
        <!--<div class="layui-input-block">-->
          <!--<button class="layui-btn" lay-submit lay-filter="formDemo">立即提交</button>-->
          <!--<button type="reset" class="layui-btn layui-btn-primary">重置</button>-->
        <!--</div>-->
      <!--</div>-->
      <!--<select name="city" lay-verify="">-->
        <!--<option value="">请选择一个城市</option>-->
        <!--<option value="010">北京</option>-->
        <!--<option value="021">上海</option>-->
        <!--<option value="0571">杭州</option>-->
      <!--</select>-->
    <!--</form>-->



  </div>
</template>

<script>
  import TableCom from './common/Table';

  export default {
    name: "data-manage",
    data() {
      return {}
    },
    components: {
      'table-com': TableCom
    },
    methods: {
      //导航：
      navFn() {

        layui.use('element', function () {
          var $ = layui.jquery
            , element = layui.element; //Tab的切换功能，切换事件监听等，需要依赖element模块
          //触发事件

          var active = {
            tabAdd: function () {
              //新增一个Tab项
              element.tabAdd('demo', {
                title: '新选项' + (Math.random() * 1000 | 0) //用于演示
                , content: '内容' + (Math.random() * 1000 | 0)
                , id: new Date().getTime() //实际使用一般是规定好的id，这里以时间戳模拟下
              })
            }
            , tabDelete: function (othis) {
              //删除指定Tab项
              element.tabDelete('demo', '44'); //删除：“商品管理”


              othis.addClass('layui-btn-disabled');
            }
            , tabChange: function () {
              //切换到指定Tab项
              element.tabChange('demo', '22'); //切换到：用户管理
            }
          };

          $('.site-demo-active').on('click', function () {
            var othis = $(this), type = othis.data('type');
            active[type] ? active[type].call(this, othis) : '';
          });

          // //Hash地址的定位
          // var layid = location.hash.replace(/^#test=/, '');
          // element.tabChange('test', layid);
          //
          // element.on('tab(test)', function(elem){
          //   location.hash = 'test='+ $(this).attr('lay-id');
          // });

        });
      }
    },
    mounted() {
      this.navFn();
      console.log(1);

//
//      layui.use(['layer','form'], function(){
//        var form = layui.form;
//
//        //监听提交
//        form.on('submit(formDemo)', function(data){
//          layer.msg(JSON.stringify(data.field));
//          return false;
//        });
//      });

      //
      // //表格数据请求：
      // this.axios.get("./src/json/data.json").then((res) => {
      //   this.tableFn(res.data);
      // }).catch((err) => {
      //   console.log(err);
      // })
    }
  }
</script>

<style lang="less">
  @import "./../less/common";

  #dataManage {
    display: flex;
    .w(100%);
    .h(100%);
    .leftWrapper {
      .w(240px);
      .h(100%);
      padding-right: 20px;
      box-sizing: border-box;
      /*.b(lightgreen);*/
      .leftContent {
        .w(100%);
        .h(100%);
        border-radius: 7px;
        box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.1);
        .topWrapper {
          .w(100%);
          .h(150px);
          .p(30px 20px 20px 20px);
          .b(@contentBg);
          box-sizing:border-box;
          border-top-left-radius: 7px;
          border-top-right-radius: 7px;
          .img{
            .h(60%);
            text-align:center;
            img{
              .h(100%);
            }
          }
          .info{
            display: flex;
            .h(40%);
            color:#fff;
            justify-content: center;
            align-items: center;
            text-align: center;
            box-sizing: border-box;
          }
        }
        .bottomWrapper {
          .w(100%);
          .h(calc(~"100% - 150px"));
          .b(@whiteColor);
          border-bottom-left-radius: 7px;
          border-bottom-right-radius: 7px;
          .layui-nav-tree {
            .w(220px);
          }
          .layui-nav {
            .b(@whiteColor);
            li.layui-nav-item {
              .b(@navBg);
              a {
                color: @blackColor;
                &:hover {
                  .b(@navBg);
                  color: @whiteColor;
                }
                .layui-nav-child {
                  border-top-color: gray !important;
                }
              }
              .layui-nav-child {
                .b(@whiteColor) !important;
              }
            }
            li.layui-nav-itemed {
              a {

              }
            }
          }
          .layui-nav-itemed > a {
            color: @blackColor !important;
          }
        }
      }
    }
    .rightWrapper {
      //.w(calc(~"100% - 242px"));
      .h(100%);
      flex: 1;
      border-radius: 7px;
      /*background: lightpink;*/
      .layui-tab-card {
        .w(100%);
        .h(100%);
        .m(0);
        border: none;
        border-radius: 7px;
        .layui-tab-title {
          .h(46px);
          .b(@tableColor);
          border-top-left-radius: 7px;
          li {
            .h(100%);
            .l-h(46px);
            color: @blackColor;
            &:nth-child(1).layui-this {
              border-top-left-radius: 7px;
            }
          }
          .layui-this {
            color: @whiteColor;
            .b(@contentBg);
            &:after {
              .h(47px);
            }
            .layui-icon {
              color: @whiteColor;
            }
          }
        }
        .layui-tab-content {
          .p(0);
          .h(calc(~"100% - 47px")) !important;
          .layui-tab-item {
            .h(100%);
            .title {
              .h(40px);
              .l-h(40px);
              .p(0 20px);
              /*.b(yellow);*/
            }
            .tableWrapper {
              .h(calc(~"100% - 40px"));
              margin-top: 0px;
              .layui-table-view {
                margin: 0 !important;
              }
              .layui-table, .layui-table-view {
                .layui-table-header {
                  background: @tableColor;
                }
              }
            }
          }
          .layui-tab {
            margin: 0;
            .layui-tab-item {
              .w(100%);
              .h(100%);
            }
          }
        }
      }

    }
  }
</style>
