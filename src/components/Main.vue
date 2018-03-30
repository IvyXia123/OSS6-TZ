<template>
  <div id="mainPage">
    <!--头部导航-->
    <div class="header">
      <div class="nameWrapper">
        <img class="comLogo" src="./../assets/logo.png"/>
        <span class="comName">{{companyName}}</span>
      </div>
      <div class="headerNavWrapper">
        <router-link class="dataManage" tag="a" :to="{name:'dataManagement'}" @click.native="navActive('dataManagement')">
          报送数据管理
          <span class="line" v-show="currentNav=='dataManagement'"></span>
        </router-link>
        <router-link class="servicePaltform" tag="a" :to="{name:'servicePlatform'}" @click.native="navActive('servicePlatform')">
          一站式服务平台
          <span class="line" v-show="currentNav=='servicePlatform'"></span>
        </router-link>
        <input class="searchBox" type="text" placeholder="请输入关键字"/>
      </div>
      <div class="basicInfoWrapper">
        <span class="time">2018-03-28 星期四 09:45:27</span>
        <!--<img class="moreIcon" src="./../assets/home_preferences.png"/>-->
        <!--<span class="moreChoice">首选项</span>-->


        <ul class="layui-nav layui-layout-right">
          <li class="layui-nav-item">
            <a href=""><img src="./../assets/home_preferences.png" class="layui-nav-img moreIcon">首选项<span class="layui-nav-more"></span></a>
            <dl class="layui-nav-child layui-anim layui-anim-upbit" id="moreInfo">
              <dd><a href="javascript:;">修改密码</a></dd>
              <dd><a href="javascript:;">修改信息</a></dd>
              <dd><a href="javascript:;">关于软件</a></dd>
              <dd><a href="javascript:;">管理我的工作台</a></dd>
            </dl>
          </li>
          <span class="layui-nav-bar" style="left: 73.5px; top: 35px; width: 0px; opacity: 0;"></span>
        </ul>


      </div>
    </div>
    <!--导航-->
    <div class="navText">
      <span>首页 &gt;</span>
      <span>一站式服务平台 &gt;</span>
      <span>用户管理</span>
    </div>

    <!--一站式服务平台导航-->
    <div class="servicePlatformNav">
      <div class="my" >
        <ul v-for="item in navDatas" :style="{width:ulWidth}">
          <li class='title'>{{item.title}}</li>
          <li v-for="i in item.navs">{{i.text}}</li>
        </ul>
        <!--<div class="my">-->
          <!--<ul>-->
            <!--<li>那些花儿</li>-->
            <!--<li>那些花儿</li>-->
            <!--<li>那些花儿</li>-->
            <!--<li>那些花儿</li>-->
            <!--<li>那些花儿</li>-->
            <!--<li>那些花儿</li>-->
          <!--</ul>-->
          <!--<ul>-->
            <!--<li>dsangds sfm</li>-->
            <!--<li>dsangds sfm</li>-->
            <!--<li>dsangds sfm</li>-->
            <!--<li>dsangds sfm</li>-->
            <!--<li>dsangds sfm</li>-->
          <!--</ul>-->
        <!--</div>-->
      </div>
    </div>
    <div class="content">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
  export default {
    name: "mainPage",
    data() {
      return {
        companyName: '上海天正智能数据服务有限公司',
        currentNav:'dataManagement',
        navDatas:[
          {
            "title":'系统管理',
            "navs":[
              {"id":1,"text":"部门管理"},
              {"id":2,"text":"用户管理"},
              {"id":3,"text":"角色管理"},
              {"id":4,"text":"角色组管理"},
              {"id":5,"text":"资源管理"}
              ]
          },
          {
            "title":'系统参数',
            "navs":[
              {"id":1,"text":"业务参数代码"},
              {"id":2,"text":"技术参数代码"},
              {"id":3,"text":"系统图标"}
            ]
          },
          {
            "title":'日志管理',
            "navs":[
              {"id":1,"text":"业务参数代码"},
              {"id":2,"text":"技术参数代码"},
              {"id":3,"text":"系统图标"}
            ]
          },
          {
            "title":'通讯管理',
            "navs":[
              {"id":1,"text":"业务参数代码"},
              {"id":2,"text":"技术参数代码"},
              {"id":3,"text":"系统图标"}
            ]
          },
          {
            "title":'调度管理',
            "navs":[
              {"id":1,"text":"业务参数代码"},
              {"id":2,"text":"技术参数代码"},
              {"id":3,"text":"系统图标"}
            ]
          },
          {
            "title":'其他工具',
            "navs":[
              {"id":1,"text":"业务参数代码"},
              {"id":2,"text":"技术参数代码"},
              {"id":3,"text":"系统图标"},
              {"id":4,"text":"系统图标"},
              {"id":5,"text":"系统图标"}
              // ,
              // {"id":6,"text":"系统图标"},
              // {"id":7,"text":"系统图标"},
              // {"id":8,"text":"系统图标"},
              // {"id":9,"text":"系统图标"}
            ]
          },
        ],
        navLength:0,
        ulWidth:0
      }
    },
    methods:{
      navActive(val){
        this.currentNav=val;
      }
    },
    created(){
      this.navDatas.map((item,index)=>{
        // console.log(item,index);
        // console.log(item.navs.length);
        // console.log(Math.ceil(item.navs.length / 4));

        if(Math.ceil(item.navs.length/5)==1){

        }
        this.navLength+=Math.ceil(item.navs.length/5);
      });
      this.ulWidth=parseInt((100/this.navLength))+'%';
      console.log(this.ulWidth);
    },
    mounted() {
//       layui.use('laydate', function () {
//         // console.log(layui)
//         var laydate = layui.laydate;
// //        执行一个laydate实例
//         laydate.render({
//           elem: '#test1' //指定元素
//         });
//       });

      layui.use('element', function(){
        var element = layui.element;

        //…

        // element.render({
        //   elem: '#moreInfo' //指定元素
        // });
        element.on('nav(demo)', function(elem){
          //console.log(elem)
          layer.msg(elem.text());
        });
      });

    }
  }
</script>

<style lang="less" scoped>
  @import "./../less/common";
  #mainPage {
    .w(100%);
    .h(100%);
    .header {
      position: relative;
      .w(100%);
      /*min-width:1240px;*/
      .h(60px);
      .p(10px 40px 10px 20px);
      overflow: hidden;
      box-sizing: border-box;
      background: @headerBgColor;
      .nameWrapper {
        .w(300px);
        .h(100%);
        float: left;
        .comLogo {
          .w(40px);
          .h(40px);
          margin-right: 5px;
          vertical-align: middle;
        }
        .comName {
          .f-s(16px);
          color: @whiteColor;
        }
      }
      .headerNavWrapper {
        position: absolute;
        .w(calc(~"100% - 660px"));
        .h(60px);
        .p(10px 6%);
        top: 0;
        left: 320px;
        box-sizing: border-box;
        overflow: hidden;
        .dataManage, .servicePaltform {
          position: relative;
          .h(30px);
          .l-h(30px);
          .f-s(14px);
          margin-top: 3px;
          color: #fefefe;
          margin-right: 25px;
          .d-i(inline-block);
          .line {
            position: absolute;
            .d-i(inline-block);
            .w(50%);
            .h(2px);
            left: 25%;
            bottom: -2px;
            border-bottom: 2px solid #fff;
          }
        }
        .searchBox {
          float: right;
          .h(30px);
          .p(3px 10px);
          .l-h(24px);
          margin-top: 5px;
          box-sizing: border-box;
          outline: none;
          color: @whiteColor;
          border-radius: 15px;
          border: 1px solid @inputBorder;
          .b(@inputBg);
          &::-webkit-input-placeholder {
            color: @whiteColor;
          }
        }
      }
      .basicInfoWrapper {
        .w(300px);
        .h(100%);
        text-align: right;
        float: right;
        color: @whiteColor;
        .time, .moreChoice {
          .d-i(inline-block);
          .h(100%);
          .l-h(40px);
          .f-s(14px);
        }
        .time {
          margin-right: 15px;
        }
        .moreIcon {
          .w(15px);
          .h(13px);
          vertical-align: middle;
        }
        .moreChoice {
        }
        .layui-nav {
          .d-i(inline-block);
        }
      }
    }
    .navText {
      .h(40px);
      .p(5px 20px);
      .b(@bodyBg);
      .l-h(30px);
      .f-s(14px);
      box-sizing: border-box;
    }

    .servicePlatformNav{
      position:absolute;
      .w(80%);
      .h(250px);
      .p(30px 40px 40px);
      .b(lightyellow);
      left:10%;
      top:60px;
      z-index:99;
      box-sizing:border-box;
      .my{
        overflow: hidden;
        ul {
          //.w(210px);
          .h(100%);
          float:left;
          border-left:1px solid @navText;
          .title{
            color:@navText;
            .f-s(16px);
          }
          li {
           // width: 210px; /*如果显示三列 则width改为70px*/
            .w(100%);
            .h(30px);
            .l-h(30px);
            padding-left:20px;
            float: left;
            display: block;
            box-sizing: border-box;
          }
        }
      }
    }

    .content {
      .w(100%);
      .h(calc(~"100% - 100px"));
      .p(0 20px 20px);
      .b(@bodyBg);
      /*.b(@bodyBg);*/
      /*.b(lightblue);*/
      box-sizing: border-box;
    }
    @media only screen and (min-width: 1400px) {
      .header {
        .headerNavWrapper {
          .p(10px 12%);
        }
      }
    }
  }
</style>
