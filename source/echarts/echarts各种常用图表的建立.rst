echarts各种常用图表的建立
^^^^^^^^^^^^^^^^^^^^^^^^^^

通过上一节的介绍，我们简单了解了echarts的功能和使用方法，这一节我们就来使用echarts创建出各种常见的图表，废话不多说，直接上代码。

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
    <head>
        <title></title>
        <link rel="stylesheet" type="text/css" href="./css/bootstrap.min.css">
        <script type="text/javascript" src="./js/jquery-1.9.1.min.js"></script>
        <script type="text/javascript" src="./js/bootstrap.min.js"></script>
        <script type="text/javascript" src="./js/echarts.js"></script>
    </head>
    <body>
        <div class="col-xs-4">
                <h3>条形图</h3>
                <div id="main" style="width: 500px;height: 400px;"></div>
                <script type="text/javascript">
                var myChart = echarts.init(document.getElementById("main"));
                var option = {
                    title:{
                        text:"第一个图标演示示例"
                    },
                    tooltip:{
                        text:"this is tool tip"
                    },
                    legend:{
                        data:['销量']
                    },
                    xAxis:{
                        data:["寸衫","羊毛衫","裤子","袜子","皮鞋","帽子"]
                    },
                    yAxis:{},
                    series:[{
                                name:["销量"],
                                type:"bar",
                                data:[5,20,36,6,43,67]
                            }]
                };

                // myChart.setOption(option);

                myChart.setOption({
                    title:{
                        text:"第一个图标演示示例"
                    },
                    tooltip:{
                        text:"this is tool tip"
                    },
                    legend:{
                        data:['销量']
                    },
                    xAxis:{
                        data:["寸衫","羊毛衫","裤子","袜子","皮鞋","帽子"]
                    },
                    yAxis:{},
                    series:[{
                                name:["销量"],
                                type:"bar",
                                data:[5,20,36,6,43,67]
                            }]
                });

            </script>
        </div>
        <div class="col-xs-4">
            <h3>饼状图</h3>
            <div id="tbSecond" style="width: 500px;height: 400px;"></div>
            <script type="text/javascript">
                var tbSecond = echarts.init(document.getElementById("tbSecond"));
                // alert(tbSecond);
                var pieOption = {
                        title:{
                            text:"饼状图"
                        },
                        series : [
                            {
                                name: '访问来源',
                                type: 'pie',
                                radius: '55%',
                                data:[
                                    {value:235, name:'视频广告'},
                                    {value:274, name:'联盟广告'},
                                    {value:310, name:'邮件营销'},
                                    {value:335, name:'直接访问'},
                                    {value:400, name:'搜索引擎'}
                                ]
                            }
                        ]
                    };
                // alert(pieOption);
                tbSecond.setOption(pieOption);

            </script>
        </div>
        <div class="col-xs-4">
            <h3>饼状图加阴影</h3>
            <div id="bzt2" style="width: 500px;height: 400px;"></div>
            <script type="text/javascript">
                var bzt2 = echarts.init(document.getElementById("bzt2"));
                bzt2.setOption({
                    title:{
                            text:"饼状图"
                        },
                    itemStyle:{
                        emphasis:{
                            shadowBlur:200,
                            shadowColor:"rgba(0,0,0,0.8)"
                        }
                    },
                    series:[
                            {
                                name: '访问来源',
                                type: 'pie',
                                radius: '55%',
                                data:[
                                    {value:235, name:'视频广告'},
                                    {value:274, name:'联盟广告'},
                                    {value:310, name:'邮件营销'},
                                    {value:335, name:'直接访问'},
                                    {value:400, name:'搜索引擎'}
                                ]
                            }
                        ]       
                });
            </script>
        </div>
        <div class="col-xs-4">
            <h3>饼状图加背景</h3>
            <div id="bzt3" style="width: 500px;height: 400px;"></div>
            <script type="text/javascript">
                var bzt3 = echarts.init(document.getElementById("bzt3"));
                bzt3.setOption({
                    title:{
                            text:"饼状图"
                        },
                    backgroundColor:"#EEEFF4",
                    itemStyle:{
                        emphasis:{
                            shadowBlur:200,
                            shadowColor:"rgba(0,0,0,0.8)"
                        }
                    },
                    series:[
                            {
                                name: '访问来源',
                                type: 'pie',
                                radius: '55%',
                                data:[
                                    {value:235, name:'视频广告'},
                                    {value:274, name:'联盟广告'},
                                    {value:310, name:'邮件营销'},
                                    {value:335, name:'直接访问'},
                                    {value:400, name:'搜索引擎'}
                                ]
                            }
                        ]
                });
            </script>
        </div>
    </body>
    </html>

:效果图如下:

.. image:: 001.png
   :alt:
   :width: 2.66667in
   :height: 2.75in
   :align: center


上述代码仅仅展现各种常用图表的建立方法，不难发现，其实格式都差不多，大部分的图形都是由绑定的数据来决定的，所以可以说数据来源也是建立图表不可或缺的一步。
可以看到上述图标所绑定的数据都是静态的，而实际的项目中数据往往都需要动态获取以渲染界面，反应动态的数据信息。所以采用异步数据加载更新是必要的。
说到这里，很多人脑海中都会浮现出一个词——Ajax，通过Ajax，可以实现在不重新加载整个页面的情况下，与服务器交换数据并更新部分网页等等功能，当然还有其他异步工具就不一一列举了。
那么下面就简单介绍下异步数据加载更新

异步数据加载更新
------------------

echarts实现异步数据的更新非常简单，在图表初始化后不管任何时候只要通过jQuery、Ajax等工具异步获取数据后通过
**setOption**填入数据和配置项就行。

.. code-block::
    :linenos:

    var myChart = echarts.init(document.getElementById('main'));

    $.get('data.json').done(function (data) {
        myChart.setOption({
            title: {
                text: '异步数据加载示例'
            },
            tooltip: {},
            legend: {
                data:['销量']
            },
            xAxis: {
                data: data.categories
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: data.data
            }]
        });
    });

.. note::
    上述代码为ajax回调的一种写法，（data）为请求数据成功的回调携带参数，里面带有获取到的数据等其他服务器携带的信息，我们便利用该参数实现动态赋值。


当然也可以先设置完其它的样式，显示一个空的直角坐标轴，然后获取数据后填入数据。

.. code-block::
    :linenos:

    var myChart = echarts.init(document.getElementById('main'));
    // 显示标题，图例和空的坐标轴
    myChart.setOption({
        title: {
            text: '异步数据加载示例'
        },
        tooltip: {},
        legend: {
            data:['销量']
        },
        xAxis: {
            data: []
        },
        yAxis: {},
        series: [{
            name: '销量',
            type: 'bar',
            data: []
        }]
    });

    // 异步加载数据
    $.get('data.json').done(function (data) {
        // 填入数据
        myChart.setOption({
            xAxis: {
                data: data.categories
            },
            series: [{
                // 根据名字对应到相应的系列
                name: '销量',
                data: data.data
            }]
        });
    });


数据的动态更新
---------------

echarts由数据驱动，数据的改变驱动图表展现的改变，因此动态数据的实现也变得异常简单。
所有数据的更新都通过setOption实现，你只需要定时获取数据setOption填入数据，而不用考虑数据到底产生了那些变化，echarts会找到两组数据之间的差异然后通过合适的动画去表现数据的变化。
使用该方法可实现数据动态显示，不过要注意填入数据的格式是否与官方要求的
**格式相符**，否则可能会出现动态图像不连续等意料之外的显示问题

.. note::
    echarts 3中移除了echarts 2中的addData方法。如果只需要加入单个数据，可以先data.push(value)后setOption
