<template>

<MTop />
<main class="content">

  <!--基本信息-->
  <header class="content-hd">
    <section class="title">
      <div class="name">
        <h1>{{baseInfo.name}}</h1>
      </div>
      <div class="job">
        <h2>{{baseInfo.job}}</h2>
      </div>
    </section>
    <section class="info">
      <ul>
        <li v-for="item in baseInfo.infoLeft" :key="item">{{item}}</li>
      </ul>
    </section>
    <section class="contact">
      <ul>
        <li v-for="item in baseInfo.infoRight" :key="item.title">
          <a :href="item.href">
            <span class="contact-link">{{item.title}}</span>
            <span class="iconfont">
              <component  :is="item.svg"></component >
            </span>
          </a>
        </li>
      </ul>
    </section>
  </header>

  <div class="content-bd">

    <div class="content-left">
      <section class="practice">
        <header class="section-hd">
          <span class="section-title-l"></span>
          <h2 class="section-title">当前工作</h2>
          <span class="section-title-r"></span>
        </header>
        <div class="section-bd">
          <!--经历:当前工作-->
          <div class="item" v-for="item in nowWorkInfo" :key="item.time">
            <header class="item-hd">
              <h3 class="item-name">{{item.name}}</h3>
              <span class="item-time">{{item.time}}</span>
            </header>
            <div class="item-bd">
              <MInfo v-for="info in item.infoList" :key="info.toString()" :info="info"></MInfo>
            </div>
          </div>

        </div>
      </section>
    </div>

    <div class="content-right">
      <section class="practice">
        <header class="section-hd">
          <span class="section-title-l"></span>
          <h2 class="section-title">以往工作</h2>
          <span class="section-title-r"></span>
        </header>
        <div class="section-bd">
          <!--经历:以往工作-->
          <div class="item" v-for="item in historyWorks" :key="item.time">
            <header class="item-hd">
              <h3 class="item-name">{{item.name}}</h3>
              <span class="item-time">{{item.time}}</span>
            </header>
            <div class="item-bd">
              <MInfo v-for="info in item.infoList" :key="info.toString()" :info="info"></MInfo>
            </div>
          </div>
        </div>
      </section>
    </div>
    <section class="skill">
      <header class="section-hd work2-title">
        <span class="section-title-l"></span>
        <h2 class="section-title">以往工作</h2>
        <span class="section-title-r"></span>
      </header>
      <div class="content-left">
        <section class="section-bd">
          <div class="item" v-for="work in historyWorks2Obj.left" :key="work.name">
            <header class="item-hd">
              <h3 class="item-name">{{work.name}}</h3>
              <span class="item-time">{{work.time}}</span>
            </header>
            <div class="item-bd">
              <MInfo :info="work.infoList"></MInfo>
            </div>
          </div>
        </section>
      </div>
      <div class="content-right">
        <section class="section-bd">
          <div class="item" v-for="work in historyWorks2Obj.right" :key="work.name">
            <header class="item-hd">
              <h3 class="item-name">{{work.name}}</h3>
              <span class="item-time">{{work.time}}</span>
            </header>
            <div class="item-bd">
              <MInfo :info="work.infoList"></MInfo>
            </div>
          </div>
        </section>
      </div>
    </section>
    <section class="skill">
      <header class="section-hd">
        <span class="section-title-l"></span>
        <h2 class="section-title">掌握技能</h2>
        <span class="section-title-r"></span>
      </header>
      <div class="content-left">
        <section class="section-bd">
          <div class="item" v-for="skill in skillObj.left" :key="skill.name">
            <header class="item-hd">
              <span class="item-name">{{skill.name}}</span>
            </header>
            <div class="item-bd">
              <MInfo :info="skill.infoList"></MInfo>
            </div>
          </div>
        </section>
      </div>
      <div class="content-right">
        <section class="section-bd">
          <div class="item" v-for="skill in skillObj.right" :key="skill.name">
            <header class="item-hd">
              <span class="item-name">{{skill.name}}</span>
            </header>
            <div class="item-bd">
              <MInfo :info="skill.infoList"></MInfo>
            </div>
          </div>
        </section>
      </div>
    </section>
  </div>
</main>

<MFooter />
</template>

<script>
import MTop from './components/MTop.vue'
import MFooter from './components/MFooter.vue'
import MInfo from './components/MInfo.vue'
import { defineComponent, reactive } from 'vue'
import mailSvg from './assets/svg/mail.svg'
import telSvg from './assets/svg/tel.svg'
export default defineComponent({
  components:{
    MTop,
    MFooter,
    MInfo,
    mailSvg,
    telSvg,
  },
  setup(){
    const baseInfo = reactive({
      name: '孟宪邦',
      job: 'Web前端工程师',
      infoLeft: [
        '男 / 1995.02',
        '天津师范大学 / 软件工程',
        '本科 / 统招 / 全日制 / 学信网可查 / 2018年毕业'
      ],
      infoRight:[
        {
          title: 'manny.mengxb@gmail.com',
          href:'mailto:manny.mengxb@gmail.com',
          svg: 'mailSvg'
        },
        {
          title: '17602208145',
          href:'tel:17602208145',
          svg: 'telSvg'
        },
      ]
    })
    const nowWorkInfo = reactive([{
      name:'零氪科技（天津）有限公司',
      time: '2021.3 - 至今',
      infoList:[
        '前端工程师（大数据技术部）',
        '部门主要业务是医疗大数据，专注于肿瘤等重大疾病领域，为患者和生命科学公司、医疗机构、保险机构、行政监管部门等产业各方，提供大数据一站式解决方案',
        '主要负责日常项目迭代，公司Lego组件库维护',
        [

          '基础架构 Vue3 + Less + @vue/cli + typescript + eslint',
          'UI框架使用的是ant-design-vue@2.X',
          '录入页重构',
          [
            '根据CRF模型动态生成表单',
            '优化点位数据结构，以提升点位的查询效率',
            '对录入整体流程进行梳理，从代码级别对组件间的关系进行解耦',
            '开发点位自动计算功能',
            [
              '根据配置的公式动态计算相关点位的结果',
              '支持跨表单自动计算'
            ]
          ],
          'Lego组件库维护',
          [
            'v-loading指令开发',
            [
              '提供类似a-spin组件的功能',
            ],
            'EventPublisher工具类开发',
            [
              '用于整体项目的解耦而开发的事件订阅工具',
              '支持跨页广播'
            ],
          ],
          '登陆服务接入',
          [
            '根据部署环境需要切换不同的登录服务',
            '优化docker启动脚本',
          ],
          '商业化项目维护',
          [
            '维护金赛项目日常的迭代需求',
            '迁移技术栈，由React迁移至Vue',
          ],
          'Docker',
          [
            '掌握Docker基本操作',
            '公司使用docker部署研发测试等环境',
          ],
          '涉及技术栈:',
          [
            'Vue3',
            '@vue/cli',
            'webpack',
            'Echarts',
            'antv',
            'antdv'
          ]
        ],
      ]
    }])
    const historyWorks = reactive([
      {
        name:'旅悦（北京）信息技术有限公司',
        time:'2019.11 - 2021.03',
        infoList:[
          '前端开发工程师',
          '从0到1搭建公司内部的BI平台，维护PMS、悦盟及业务组件库',
          [
            'BI-Matrix（可视化报表平台）',
            [
              '负责开发环境的构建和优化,整体开发流程的优化、项目底层逻辑的编写、难点功能的预研和初稿实现。',
              '从需求调研、参与设计到进行项目开发、可视效果优化的全流程跟进，实现了可视化平台从0到1的过程',
              '项目特色:',
              [
                '将权限映射为资源树，可将权限精细到按钮级，且易于维护。',
                '以百分比的形式对组件进行渲染，根据不同尺寸和分辨率的设备做了展示优化',
              ],
              'Dva Bug排查，解决了Dva在重新挂在model时state未被初始化的问题',
              '涉及技术栈:',
              [
                'Dva', 'React', 'TypeScript', 'Es-Lint', 'Sass'
              ]
            ],
            '业务组件库',
            [
              '该组件库封装了集团各系统内常⽤组件，并抽象了相应的业务逻辑。以缩短各系统的开发时间，减少开发成本。',
              'Slider Menu组件',
              [
                '⽤于厂字型布局的左侧菜单，绑定了集团各平台通⽤用的权限校验逻辑',
                '实现⽬标节点路径查找，根据URL匹配相应资源节点等方法，并抽象为工具类',
              ],
              'Switch Hotel组件',
              [
                '用于PMS各系统内搜索相关门店并进行切换，且对⽤户历史选择的门店做了缓存优化。',
                '⽀持在多⽤用户的场景下缓存各用户历史选择的门店，并在展示时默认将历史选择过的门店在列列表中优先展示。'
              ]
            ],
          ]
        ]
      },
    ])
    const historyWorks2 = reactive([
      {
        name:'天津泰凡科技有限公司',
        time:'2017.12 - 2019.11',
        infoList:[
          '前端工程师',
          '主要负责数据可视化研发及MES系统的前端开发',
          [
            '生产制造智能管理与追溯分析系统',
            [
              '负责工单、采购⼊库、成品出库等模块，在项目中期承担起了项目经理的职责',
              '制定异常处理机制:在成品出库模块中，由于涉及到多个系统之间的数据流转，在前期设计异常情况处理时遇到了很⼤大的阻碍。后来经过与多方的沟通，制定相应的异常处理机制，该⽅案在实施后赢得了项⽬组和客户的⼀致认可',
              '编写软著4篇、外观专利1篇、技术专利1篇',
              '涉及技术栈:',
              [
                'Vue2',
                'VueX',
                'webpack',
                'Echarts'
              ],
            ],

            '气象数据可视化项⽬',
            [
              '使用原生WebGL在二维平⾯上展示风、温、湿、压、雨和污染六要素等常见的气象数据，使用粒⼦动画和⾊斑图作为展示方式，可对接气象领域常见的GRIB数据源。',
              '调研格点数据解析方法，并将GRIB数据转换为结构化数据',
              '优化气象数据加载速度，将结构化数据生成为纹理，相比加载JSON数据体积减小8～10倍左右',
              '涉及技术栈:',
              [
                'WebGL',
                'Vue2',
                'webpack',
                'python'
              ],
            ],

            'DataMag 2.0数据可视化平台',
            [
              '使用Vue2+E-Charts开发报表展示模块',
              '抽象各个图表的维度、度量、指标，编写相应的转换函数用于不同类型图表之间的转换',
              '涉及技术栈:',
              [
                'Vue2',
                'VueX',
                'E-Charts',
                'webpack',
                'ElementUI'
              ],
            ]
          ],
        ]
      },
      {
        name:'其它项目经验',
        infoList:[
          'Magic Code少儿编程平台',
          '线上地址: https://www.coding4fun.com.cn',
          [
            '工作内容:',
            [
              '负责该项目的官网平台和Scratch与Minecraft联动部分的开发',
              '优化ScratchMC功能(Scratch与Minecraft联动的开源项目)时，解决了ScratchMC⽆法建造汉字积木块的问题',
              '扩展ScratchMC积⽊块的功能'
            ],
            '涉及技术栈:',
            [
              'Vue2',
              'nodejs',
              'css',
              'html',
            ]
          ],
        ]
      }
    ])
    const historyWorks2Obj = {
      left:[],
      right:[]
    }
    let splitIndex = 1
    for(let i = 0; i < historyWorks2.length; i++){
      if(i < splitIndex){
        historyWorks2Obj.left.push(historyWorks2[i]) 
      }else{
        historyWorks2Obj.right.push(historyWorks2[i]) 
      }
    }
    const skillList = [
      {
        name:'Web',
        infoList:[
          '熟悉JS基础语法和知识',
          '掌握最新的ES6+语法',
          '有TypeScript研发经验',
          '掌握CSS以及预编译语言SCSS,Less',
        ]
      },
      {
        name:'TypeScript',
        infoList:[
          '熟练掌握TypeScript语法',
          '有过多个TypeScript项目的实战经验'
        ]
      },
      {
        name:'WebGL',
        infoList:[
          '了解WebGL的基本概念',
          '使用原生WebGL开发过气象可视化项目',
        ]
      },
      {
        name:'git',
        infoList:[
          '公司由gitLab作为仓库',
          '熟练掌握git工作流'
        ]
      },
      {
        name:'Docker',
        infoList:[
          '了解基本的Docker命令',
          '有使用Docker部署前端微服务的实战经验',
        ]
      },
      {
        name: 'React',
        infoList:[
          '熟练使用React全家桶',
          '有过多个React+TypeScript项目的实战经验'
        ]
      },
      {
        name: 'Vue2/3',
        infoList:[
          '熟练使用vue2/3及其全家桶',
          '使用过elementUI和Ant-design-vue两个框架'
        ]
      },
      {
        name:'数据库',
        infoList:[
          '使用过mysql，写过简单的增删改查',
        ]
      },
      {
        name:'Echarts/AntV-G2',
        infoList:[
          '熟悉相关结构和基本概念',
          '能够尽量还原设计图内容'
        ]
      },
    ]
    const skillObj = {
      left:[],
      right:[]
    }
    splitIndex = 6
    for(let i = 0; i < skillList.length; i++){
      if(i < splitIndex){
        skillObj.left.push(skillList[i]) 
      }else{
        skillObj.right.push(skillList[i]) 
      }
    }

    return {
      baseInfo,
      nowWorkInfo,
      historyWorks,
      historyWorks2Obj,
      skillObj,
    }
  }
})
</script>
