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
          <h2 class="section-title">Experience</h2>
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
          <h2 class="section-title">Experience</h2>
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
        <h2 class="section-title">Experience</h2>
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
      name: 'Xianbang Meng',
      job: 'Front-End Engineer',
      infoLeft: [
        'Male / Feb 1995',
        'Tianjin Normal University / Software Engineering',
        ' Undergraduate / Graduated in 2018'
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
      name:'LinkDoc Co., Ltd',
      time: 'Mar 2021 - Present',
      infoList:[
        'Front-End Engineer (BigData Technology Department)',
        'The main business of the department is medical big data, focusing on major diseases such as tumors, providing one-stop big data solutions for patients and life science companies, medical institutions, insurance institutions, administrative supervision departments and other industrial parties',
        "Mainly responsible for project iteration, maintenance of the company's Lego component library",
        [

          'Scientific research integration platform',
          [
            'Dynamically generate forms from CRF models',
            'Optimize point data structure to improve point query efficiency',
            'Sort out the overall input process, and decouple components from the code level',
            'Develop automatic point calculation',
            [
              'Dynamically calculate the results of related points according to the configured formula',
              'Support automatic calculation from another forms'
            ],
            'Technology Stack: Vue3, Less, @vue/cli, TypeScript, ES-Lint'
          ],
          'Lego component library maintenance',
          [
            'Develop v-loading directive',
            'Develop EventPublisher utils class',
            [
              'An event subscription tool developed for the decoupling of the overall project',
              'Supports publish event across pages'
            ],
          ],
          'Login service Maintenance',
          [
            'Switch between different login services according to the needs of the deployment environment',
            'Optimize the docker startup script',
          ],
          'Gensci project maintenance',
          [
            'Maintain the iterative requirements',
            'Migration technology stack, from React to Vue',
            'Technology Stack: React, Redux, TypeScript'
          ]
        ],
      ]
    }])
    const historyWorks = reactive([
      {
        name:'TripMod Co., Ltd',
        time:'Nov 2019 - Mar 2021',
        infoList:[
          'Front-End Engineer',
          `Build the company's internal BI platform from 0 to 1, maintain PMS, Yuemeng and business component libraries`,
          [
            'BI-Matrix (Visualization platform)',
            [
              'Responsible for the construction and optimization of the development environment, the optimization of the overall development process, the writing of the underlying logic of the project, the pre-research and first-draft implementation of difficult functions.',
              'The whole process of follow-up from demand research, participation in design to project development and visual effect optimization has realized the process of visualization platform from 0 to 1',
              'Project features:',
              [
                'Mapping permissions as a resource tree enables granular permissions down to the button level and is easy to maintain.',
                'Render components in percentage form, and optimize the display according to devices of different sizes and resolutions',
              ],
              'Solved the problem of Dva that the state is not initialized when Dva is recreate on the model',
              'Technology Stack: Dva, React, TypeScript, Es-Lint, Sass'
            ],
            'Business Component Library',
            [
              'The component library encapsulates the common components in each system of the group, and abstracts the corresponding business logic. In order to shorten the development time of each system and reduce the development cost.',
              'Slider Menu',
              [
                'The left menu for layout is bound with the permission verification logic common to all platforms of the group',
                'Realize the target node path search, match the corresponding resource nodes according to the URL and other methods, and abstract it into a tool class',
              ],
              'Switch Hotel',
              [
                'It is used to search and switch related stores in various PMS systems, and cache and optimize the stores selected by users in the history.',
                'Supports caching of historically selected stores by each user in multi-user scenarios, and displays the historically selected stores in the column list by default.'
              ]
            ],
          ]
        ]
      },
    ])
    const historyWorks2 = reactive([
      {
        name:'TechFantasy Co., Ltd',
        time:'Dec 2017 - Nov 2019',
        infoList:[
          'Front-End Engineer',
          'Mainly responsible for data visualization research and development and front-end development of MES system',
          [
            'MES System',
            [
              'Responsible for modules such as work order, procurement warehousing, finished product delivery, etc., and assumed the responsibility of project manager in the middle of the project',
              'Work with business partners to develop an exception handling mechanism, which has won unanimous approval from the project team and customers after its implementation',
              'Wrote 4 software work, 1 appearance patent, 1 technical patent',
              'Technology Stack: Vue2, VueX, Webpack, E-Charts',
            ],

            'Weather Data Visualization',
            [
              'Use native WebGL to display common meteorological data such as wind, temperature, humidity, pressure, rain, and pollution on a two-dimensional plane. Use particle animation and color pattern as a display method to connect with common GRIB data sources in the meteorological field.',
              'Investigate grid data analysis methods and convert GRIB data into structured data',
              'Optimize the loading speed of meteorological data, generate structured data into textures, and reduce the volume by about 8 to 10 times compared to loading JSON data',
              'Technology Stack: WebGL, React, Webpack, python',
            ],

            'DataMag 2.0 (Visualization platform)',
            [
              'Use Vue2 + E-Charts to develop report display module',
              'Abstract the dimensions, measures, and series of each chart, and write corresponding conversion functions for conversion between different types of charts',
            ]
          ],
        ]
      },
      {
        name:'Other Experience',
        infoList:[
          `Magic Code Children's Programming Platform`,
          'Online: https://www.coding4fun.com.cn',
          [
            'Work Content:',
            [
              `Responsible for the development of the project's official website platform and the linkage between Scratch and Minecraft`,
              'When optimizing the ScratchMC function (an open source project linked by Scratch and Minecraft), the problem that ScratchMC cannot build Chinese character blocks is solved',
              'Extend the functionality of ScratchMC blocks'
            ],
            'Technology Stack: React, Redux, Nodejs, Sass',
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
