<template>
    <div class="page-home-index">
        <H-header></H-header>
        <article>
            <section class="bike-banner">
                <h1 class="get-title">不是在写代码，就是在骑行的路上</h1>
                <p>Coding，Riding，Or Reading.</p>
            </section>
            <div class="bike-article">
                <div class="bike-list" v-for="(item, i) in listData" :key="i">
                    <div class="list-content">
                        <div class="title"><i :class="['iconfont', item.icon]"></i>{{item.title }}</div>
                        <div class="sub-title">{{item.content }}</div>
                    </div>
                </div>
            </div>
            
            <section class="bike-about">
                <div class="about-content">
                    <div class="about-col-40">
                        <el-popover
                            ref="popover"
                            placement="top"
                            width="200"
                            trigger="hover">
                            <img src="" alt="">
                        </el-popover>
                        <el-button :class="['iconfont', 'icon-iconweixin']" v-popover:popover></el-button>
                    </div>
                     
                    <div class="about-col-60">
                        <div class="title">联系微人类</div>
                        <div class="sub-title">在知识爆炸的年代，我们不愿成为知识的过客，拥抱开源，崇尚共享，乐于交流，技术碰撞，共同进步。</div>
                    </div>
                </div>
            </section>
        </article>
        <H-footer></H-footer>
	    <div class="li-common-loading" ref="loading" v-show="loading"></div>

        <!-- <div class="animated fadeInDown">
          何立军
        </div> -->
    </div>
</template>

<script>

require("@/assets/lib/bodymovin/bodymovin.min.js")

import HHeader from '@/components/Header';
import HFooter from '@/components/Footer';
export default {
    name: 'home-index',
    data () {
        return {
            activeIndex: '1',
            listData: [
                {
                title: '技术博客',
                icon: 'icon-xinwen',
                content: '技术这条路，必须走到黑，不回头。日常的总结，是点点滴滴的进步。以js为核心，java，linux为辅多元化发展，不做偏安一隅的前端，ITer，请跟随兴趣一路前行。'
                },
                {
                title: '感悟',
                icon: 'icon-idea',
                content: '放下对生活的成见，做一个不动声色的人，因为不是所有的鱼都生活在同一片海里。在躁动的青春年纪，那些总以为是迷茫的，不过是某一刻突然安静下来的不知所措而罢，面对复杂，保持欢喜，漫漫余生，满怀期盼。'
                },
                {
                title: '民谣',
                icon: 'icon-music',
                content: '我没有故事，也没有酒，可是我有民谣，虾米音乐--精选集--《民谣中毒》，一起细品民谣，让越来越快的生活节奏放慢几分。'
                },
                {
                title: '自行车',
                icon: 'icon-zixingche',
                content: '开车太快，走路太慢，自行车刚刚好。迎着风，向着朝阳，最好的时光在路上，即刻出发!'
                }
            ],
            aboutData: [
                {
                    icon: 'icon-jian',
                    type: 'link',
                    link: ''
                },
                {
                    icon: 'icon-iconweixin',
                    type: 'alert',
                    img: ''
                },
                {
                    icon: 'icon-boke3',
                    type: 'alert',
                    img: ''
                },
                {
                    icon: 'icon-github',
                    type: 'link',
                    link: ''
                }
            ],
            msg: 'home-index',
            loading: false
        }
    },
    components: {
        HHeader,
        HFooter
    },
    async created () {

    },
    mounted () {
      let animData = {
          wrapper: this.$refs.loading,
          animType: 'svg',
          loop: true,
          prerender: true,
          autoplay: true,
          //path: "/static/lib/bodymovin/loading-bike.json",
          path: "/static/lib/bodymovin/aimee.json",
      };
      this.loading = true;
      bodymovin.loadAnimation(animData);

      setTimeout(() => {
        if(this.dataReady){
          this.loading = false;
        }
      }, 5000)
    },
    methods: {

    }
}
</script>

<style lang="scss" scoped>
@import '~@/assets/css/common.css';
@import '~@/assets/css/animate/animate.css';
.common-width {
    margin: 0 auto !important;
    width: 1200px !important;
}
.page-home-index {
    box-sizing: border-box;
    overflow-x: hidden;
    overflow-y: scroll;

    .header-space {
        height: 60px;
        min-height: 60px;
    }
    article {
        position: relative;

        .bike-banner {
            background: #1E5B94;
            color: #fff;
            text-align: center;
            padding: 160px 0;

            .get-title {
                font-size: 200%;
                display: inline-block;
            }
            p {
                margin-top: 40px;
                font-weight: 600;
            }
        }
        .bike-article {
            display: flex;
            text-align: left;
            padding-bottom: 40px;
            @extend .common-width;
            .iconfont {
                font-size: 20px;
                margin-right: 10px;
            }
            .icon-idea {
                font-size: 22px;
                margin-right: 8px;
            }
            .bike-list {
                padding: 14px 16px;
                width: 25%;

                .list-content {
                    cursor: pointer;
                    padding: 0 10px 5px 10px;
                    border-radius: 6px;

                    &:hover {
                        transform: scale(1.1154);
                        transition: all 1s;
                        box-shadow: 10px 10px 10px #CCC;
                    }
                    .title {
                        margin-top: 20px;
                        font-size: 18px;
                        margin-bottom: 6px;
                        color: #1f8dd6;
                    }

                    .sub-title {
                        margin-top: 10px;
                        letter-spacing: 1px;
                        color: #7f8c8d;
                        font-size: 15px;
                        text-align: justify;
                    }
                }
            }
        }
        .bike-about {
            background-color: #0bb59b;
            min-height: 200px;

            .about-content {
                @extend .common-width;
                display: flex;
                align-items: center;
                min-height: 200px;

                .about-col-40 {
                    width: 40%;
                    text-align: right;

                    i {
                        font-size: 35px;
                        margin-right: 40px;
                        cursor: pointer;
                        transition: all 0.8s;

                        &:hover {
                            transform: scale(1.1154);
                        }
                    }
                    .icon-jian {
                        color: #e67979;
                    }
                    .icon-boke3 {
                        color: #eaeaff;
                    }
                    .icon-github {
                        color: black;
                    }
                    .icon-iconweixin {
                        color: #236f06;
                    }
                }
                .about-col-60 {
                    width: 60%;
                    text-align: left;
                    padding-left: 10%;

                    .title {
                        font-size: 140%;
                        font-weight: 600;
                    }
                    .sub-title {
                        margin-top: 1.6rem;
                        color: 666;
                        width: 68%;
                    }
                }
            }
        }
        
    }
}
.li-common-loading {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 10vw;
    box-sizing: border-box;
}
</style>
