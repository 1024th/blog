+++
title = "启明13班去向图"
date = "2021-08-03T12:50:17.138Z"
description = "启明13班去向图"
draft = false
+++

<style>
    * {
        margin: 0;
        padding: 0;

    }

    h1 {
        text-align: center;
    }

    h3,
    h4,
    h5,
    h6 {
        font-weight: normal;
    }

    .clear {
        clear: both;
    }

    body {
        font-family: "微软雅黑";
    }

    a {
        text-decoration: none;
        color: #333;
    }

    #charts {
        width: 800px;
        height: 600px;
        margin: 0 auto;
    }

    .market_map_title {
        font-size: 32px;
        text-align: left;
        padding-left: 50px;
    }
</style>

<body>
    <h1>启明13班去向图</h1>
    <div id="charts"></div>
    <div style="text-align:center;"><div style="width:auto; display:inline-block !important; display:inline;border: 1px solid #000; padding: .5em;margin-bottom: 1em;">马来西亚 吉隆坡：谢谨翔</div></div>
    
</body>

<!-- <script src="echarts-all2.js"></script> -->
<!-- <script src="https://blog-static.cnblogs.com/files/1024th/echarts-all2.min.js"></script> -->
<script>
    var mycharts = echarts.init(document.getElementById('charts'))
    option = {
        dataRange: {
            show: false,
            x: 'left',
            y: 'bottom',
            splitList: [
                { start: 5, end: 5, color: 'orange' },//当值为5时，区域背景
                { start: 10, end: 10, color: '#ff6300' },//当值为10时，区域背景
                { start: 15, end: 15, color: '#ccc' },//当值为15时，区域背景
            ],
        },
        tooltip: {
            alwaysShowContent: true,
            enterable: true,
            formatter: function (params) {
                var name = params.name;
                var goaltext = "none";
                if (name == "福建") {
                    goaltext = "福州：洪朗晨、王嘉翰、汪子悦、郑砾禹、林瑾宁、卢翔玥、陈恺翔、林雨佳、张书萁、张文佳<br>厦门：饶铭鑫、林雨桐、叶敬一";
                } else if (name == "北京") {
                    goaltext = "北京：万乐天、薛煌铠、张伟健";
                }
                else if (name == "天津") {
                    goaltext = "天津：王良涛";
                }
                else if (name == "重庆") {
                    goaltext = "重庆：林子函、勾洁";
                }
                else if (name == "浙江") {
                    goaltext = "杭州：刘晓君、卢奕成<br>宁波：翁隽恺";
                }
                else if (name == "四川") {
                    goaltext = "成都：林铄峻、王子蕤<br>德阳：陈亮迪";
                }
                else if (name == "上海") {
                    goaltext = "上海：郭珉萱、吴凰、陈墨函、林田川";
                }
                else if (name == "安徽") {
                    goaltext = "合肥：郑子旸";
                }
                else if (name == "湖南") {
                    goaltext = "长沙：严嘉豪、陆正鑫";
                }
                else if (name == "江西") {
                    goaltext = "南昌：石翰林";
                }
                else if (name == "江苏") {
                    goaltext = "南京：许欣运、郑珩芊、林梓杭<br>无锡：林子烜";
                }
                else if (name == "辽宁") {
                    goaltext = "沈阳：周祺浩";
                }
                else if (name == "陕西") {
                    goaltext = "西安：江启键";
                }
                else if (name == "山西") {
                    goaltext = "太原：江齐政、李尤哲锐";
                }
                else if (name == "吉林") {
                    goaltext = "长春：林城";
                }
                else if (name == "广东") {
                    goaltext = "珠海：郭修晨";
                }
                else if (name == "山东") {
                    goaltext = "威海：严謇";
                }
                else if (name == "广西") {
                    goaltext = "南宁：郑文菁";
                }
                else {
                    goaltext = "none";
                }

                return goaltext;
            }
        },
        series: [
            {
                name: '',
                type: 'map',
                mapType: 'china',
                //hoverable: false,
                roam: false,
                itemStyle: {
                    normal: { label: { show: true } },
                    emphasis: { label: { show: false } }
                },
                data: [],
            }
        ],
        animation: false

    };
    var ini_data = [];//初始化省份数组



    /*要那些省就在这儿改*/
    var provArr = ["福建", "北京", "天津", "重庆", "浙江", "四川", "上海", "安徽", "湖南", "江西", "江苏", "辽宁", "陕西", "山西", "吉林", "广东", "山东", "广西"];//获取的省份，有可能是从后台获取


    //正则省份，将省与市的字眼去掉，框架不识别
    for (var i = 0; i < provArr.length; i++) {
        var str = provArr[i];
        var re = /省|市/g;  //全局匹配
        var str2 = { name: str.replace(re, ''), value: 5 };//拼接对象数组
        ini_data.push(str2);
    }
    option.series[0].data = ini_data;//将拼接好的数组赋给参数集合
    mycharts.setOption(option);//跟新图表
    //鼠标滑过事件
    var testStr = ',' + provArr.join(",") + ",";
    mycharts.on('hover', function (param) {
        // console.log(param);
        if (testStr.indexOf("," + param.name + ",") != -1) {
            return false;
        } else {
            param.value = 15;
            mycharts.setOption(option);
        }
    });
    //初始化省颜色
    function ini_province() {
        var ini_len = option.series[0].data.length;
        for (var i = 0; i < ini_len; i++) {
            //初始化颜色
            option.series[0].data[i].value = 5;
            mycharts.setOption(option);
        }
    }
</script>