<template>
    <div>
        <el-carousel trigger="click" height="550px" @change="loadAnimate">
            <el-carousel-item v-for="(item,index) in sliderList" :key="index">
                <figure>
                    <img :src="'../../static/img/slider/'+item.img" width="100%"/>
                    <figcaption>
                        <h1 :class="{ bounceInDown:slider_index==index }">{{ item.title }}</h1><br>
                        <p :class="{ fadeInUp:slider_index==index }">{{ item.abstract }}</p><br>
                    </figcaption>
                </figure>
            </el-carousel-item>
        </el-carousel>
        <ul class="home-kind">
            <li v-for="(item,index) in kind" :key="index">
                <h3>{{ item.title }}<div></div></h3>
                <p>{{ item.info }}</p>
            </li>
        </ul>
        <div class="home-service">
            <h1>丰富的应用场景，最优的解决方案</h1>
            <p>
              XXX是一家专业从事展览展示策划设计、制作搭建服务、展厅设计装修、活动会议策划的会展公司。公司以专业化、国际化为标准，专心致力于为提升客户品牌而不懈努力。
            </p>
            <ul>
                <li v-for="(item,index) in services" :key="index">
                    <div class="service-box">
                        <img :src="`../../../static/img/services/${index+1}.png`">
                        <div class="service-info"><p>{{ item.info }}</p></div>
                    </div>
                    <br>
                    <p>{{ item.title }}</p>
                </li>
            </ul>
        </div>
        <div class="home-friends">
            <div class="friends-container">
                <h1>合作伙伴</h1>
                <ul>
                    <li v-for="item in 6" :key="item">
                        <img :src="`../../../static/img/friends/clients-logo0${item}.png`">
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>
import { home } from '../../http/home';

export default {
    name: "Home",
    data(){
        return {
            slider_index: 0,
            sliderList: [
                {
                    title: '展览展商',
                    abstract: '让我们尽全力为客户创造价值更大效益',
                    img: 'slider04.jpg',
                    link: ''
                },
                {
                    title: '展览展商',
                    abstract: '让我们尽全力为客户创造价值更大效益',
                    img: 'slider05.jpg',
                    link: ''
                }
            ],
            kind:[
                {
                    title: '展台设计',
                    info: 'Stand Design'
                },
                {
                    title: '展台搭建',
                    info: 'Hutte is opgestel'
                },
                {
                    title: '展厅规划',
                    info: 'Exhibition Hall Design'
                },
                {
                    title: '展柜制作',
                    info: 'Uitstalling kabinet produksie'
                }
            ],
            services:[
                {
                    title: '一站式服务',
                    info: '为您提供全球一站式展台设计搭建服务'
                },
                {
                    title: '全程跟踪',
                    info: '前中后期都有相关工作人员跟踪，确保项目完工'
                },
                {
                    title: '专业团队',
                    info: '三十位资深设计师，你想要的风格这里都有'
                },
              {
                title: '品质保证',
                info: '以专业化、国际化为标准，专心致力于提升客户品牌'
              },
              {
                title: '资质荣誉',
                info: '发展至今、满载荣誉，是客户对我们的信任和肯定'
              }
            ]
        }
    },
    created(){
        this.$emit('headFix', ['fixed',false]);
        // home()
        // .then(data=>{
        //     console.log(data)
        // })
        // .catch(err => {
        //     this.$message.error(err.message);
        // });
    },
    methods:{
        loadAnimate(index){
            this.slider_index = index;
        }
    }
}
</script>
<style lang="scss" scoped>
    @mixin self_icon {
        &::before {
            border-left: 50px solid #DADADA;
            border-right: 50px solid #DADADA;
            bottom: 0;
            content: "";
            height: 1px;
            margin-left: -70px;
            position: absolute;
        }
        &::after {
            background: #FF8724 none repeat scroll 0 0 padding-box content-box;
            border-bottom: 1px solid #DADADA;
            border-left: 1px solid #DADADA;
            bottom: -10px;
            content: "";
            left: 50%;
            margin-left: -16px;
            padding: 0 0 8px 8px;
            position: absolute;
            transform: rotate(-45deg);
        }
    }
    figure {
        color: #ffffff;
        text-align: left;
        &::before {
            background: rgba(0, 0, 0, 0.4) none repeat scroll 0 0;
            content: "";
            height: 100%;
            position: absolute;
            width: 100%;
        }
        figcaption {
            bottom: 0;
            left: 6%;
            margin: 0 auto;
            position: absolute;
            right: 6%;
            top: 40%;
            width: 1170px;
            padding: 0 15px;
            h1 {
                font-size: 46px;
            }
            p {
                font-size: 18px;
                font-weight: 400;
            }
            .slider-button {
                background-color: #FE8724;
                border-color: #FE8724;
                color: #ffffff;
                width: 180px;
                height: 40px;
                font-size: 18px;
                transition: transform 2s;
                &:hover {
                    transform: translateY(10px);
                }
            }
        }
    }
    .home-kind {
        box-sizing: border-box;
        background-color: #EBEEF5;
        padding: 0 5%;
        display: flex;
        li {
            padding: 1%;
            text-align: left;
            position: relative;
            box-sizing: border-box;
            width: 25%;
            h3{
                display: inline-block;
                div {
                    margin-top: 1%;
                    height: 2px;
                    width: 40px;
                    background-color: #0984E3;
                }
            }
            p {
                margin-top: 1.5%;
                font-size: 14px;
                color: gray;
            }
            h3>div {
                transition: width .5s;
            }
            &:hover {
                background-color: #ffffff;
                transition: background-color .5s;
                h3>div{
                    width: 100%;
                }
            }
            &:not(:first-child)::before {
                content: '';
                position: absolute;
                width: 1px;
                height: 80%;
                left: 0;
                background-color: #D6D6D6;
            }

        }
    }
    .home-service {
        margin-top: 3%;
        h1 {
            position: relative;
            @include self_icon;
            &::before {
                left: 49.9%;
                top: 174%;
                width: 43px;
            }
            &::after {
                height: 22px;
                left: 50%;
                top: 140%;
                width: 22px;
            }
        }
        &>p {
            margin-top: 5%;
            color: gray;
        }
        ul {
            margin-top: 5%;
            padding: 0 10%;
            display: grid;
            grid-template-columns: 300px 320px 320px 320px 320px;
            li {
                .service-box {
                    margin-left: 50%;
                    transform: translateX(-50%);
                    display: flex;
                    overflow: hidden;
                    width: 120px;
                    height: 120px;
                    border-radius: 50%;
                    img, .service-info {
                        transition: all 0.4s ease-in-out 0s;
                    }
                    &:hover {
                        img, .service-info {
                            transform: translateX(-80%);
                        }
                    }
                    img {
                        width: 100%;
                        height: auto;
                    }
                    .service-info {
                        width: 80%;
                        height: 100%;
                        background: #f1f1f1;
                        padding: 20% 25% 0 5%;
                        position: absolute;
                        top: 0;
                        right: -110%;
                        p {
                            font-weight: 600;
                        }
                    }
                }
            }
        }
    }
    .home-friends {
        margin-top: 5%;
        height: 35vh;
        padding: 20px 0;
        background: url(../../../static/img/head-view/clients-bg.jpg);
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        position: relative;
        &::before {
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4);
            content: "";
            left: 0;
            top: 0;
        }
        .friends-container {
            padding-right: 15px;
            padding-left: 15px;
            position: relative;
            h1 {
                font-size: 45px;
                color: #ffffff;
                @include self_icon;
                &::before {
                    left: 50%;
                    top: 144%;
                    width: 29.5px;
                }
                &::after {
                    height: 12px;
                    left: 50%;
                    top: 130.5%;
                    width: 12px;
                }
            }
            ul {
                display: flex;
                margin-top: 5%;
                position: absolute;
                margin-left: 50%;
                transform: translateX(-50%);
            }
        }
    }
// 动画类
.bounceInDown {
    animation: bounceInDown 1s linear;
}
.fadeInUp {
    animation: fadeInUp 1s linear;
}
</style>
