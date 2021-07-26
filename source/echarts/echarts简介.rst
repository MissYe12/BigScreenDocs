:echarts官网链接:
    https://echarts.apache.org/zh/index.html

echarts简介
^^^^^^^^^^^^^^^

ECharts，缩写来自Enterprise Charts，商业级数据图表，一个纯Javascript的图表库，可以流畅的运行在PC和移动设备上，
兼容当前绝大部分浏览器（IE6/7/8/9/10/11，chrome，firefox，Safari等），底层依赖轻量级的Canvas类库ZRender，提供直观，生动，可交互，可高度个性化定制的数据可视化图表。
创新的拖拽重计算、数据视图、值域漫游等特性大大增强了用户体验，赋予了用户对数据进行挖掘、整合的能力。
支持折线图（区域图）、柱状图（条状图）、散点图（气泡图）、K线图、饼图（环形图）、雷达图（填充雷达图）、和弦图、力导向布局图、地图、仪表盘、漏斗图、事件河流图等12类图表，
同时提供标题，详情气泡、图例、值域、数据区域、时间轴、工具箱等7个可交互组件，支持多图表、组件的联动和混搭展现。


环境搭建
^^^^^^^^^^^

获取ECharts
---------------

一览echarts功能的强大，是不是迫不及待想要上手体验一下呢。
这个环境搭建so easy! 其实只有一个echarts.min.js而已。可以从官网下载
http://echarts.baidu.com/download.html。
根据自己的需要可以常用、精简、安装或者源码包，甚至可以自定义下载。
在你的网页里加入这个js文件就有了echarts的开发环境，是不是so easy！

引入ECharts
-------------
通过标签方式直接引入构建好的 echarts 文件

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <!-- 引入 ECharts 文件 -->
            <script src="echarts.min.js"></script>
        </head>
    </html>


简单绘制一个图表
-----------------

在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。

.. code-block:: html
    :linenos:

    <body>
        <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
        <div id="main" style="width: 600px;height:400px;"></div>
    </body>


然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，下面是完整代码。

.. code-block:: html
    :linenos:

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>ECharts</title>
        <!-- 引入 echarts.js -->
        <script src="echarts.min.js"></script>
    </head>
    <body>
        <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
        <div id="main" style="width: 600px;height:400px;"></div>
        <script type="text/javascript">
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('main'));

            // 指定图表的配置项和数据
            var option = {
                title: {
                    text: 'ECharts 入门示例'
                },
                tooltip: {},
                legend: {
                    data:['销量']
                },
                xAxis: {
                    data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
                },
                yAxis: {},
                series: [{
                    name: '销量',
                    type: 'bar',
                    data: [5, 20, 36, 10, 10, 20]
                }]
            };

            // 使用刚指定的配置项和数据显示图表。
            myChart.setOption(option);
        </script>
    </body>
    </html>


配置项解析
-------------

其实我们可以看出来，对于echarts的使用，我们只需要在其特定的配置项中设定符合要求的相关参数就能绘制出画风简约好看的图标而不用使用较为复杂的canvas来绘图。
对于大部分开发者来讲，是比较高效且便捷的。echarts 的使用者，使用 option 来描述其对图表的各种需求，包括：有什么数据、要画什么图表、图表长什么样子、含有什么组件、组件能操作什么事情等等。
简而言之，option 表述了：数据、数据如何映射成图形、交互行为。那么下面就来简单介绍下配置项基本名词的解析

.. list-table::
    :widths: 25 50
    :header-rows: 1

    * - 名词
      - 描述
     
    * - chart
      - 是指一个完整的图表，如折线图，饼图等“基本”图表类型或由基本图表组合而成的“混搭”图表，可能包括坐标轴、图例等

    * - axis
      - 直角坐标系中的一个坐标轴，坐标轴可分为类目型、数值型或时间型

    * - xAxis
      - 直角坐标系中的横轴，通常并默认为类目型

    * - yAxis
      - 直角坐标系中的纵轴，通常并默认为数值型

    * - grid
      - 直角坐标系中除坐标轴外的绘图网格，用于定义直角系整体布局

    * - legend
      - 图例，表述数据和图形的关联

    * - dataRange
      - 值域选择，常用于展现地域数据时选择值域范围

    * - dataZoom
      - 数据区域缩放，常用于展现大量数据时选择可视范围

    * - roamController
      - 缩放漫游组件，搭配地图使用

    * - toolbox
      - 辅助工具箱，辅助功能，如添加标线，框选缩放等
      
    * - tooltip
      - 气泡提示框，常用于展现更详细的数据
      
    * - timeline
      - 时间轴，常用于展现同一系列数据在时间维度上的多份数据
      
    * - series
      - 数据系列，一个图表可能包含多个系列，每一个系列可能包含多个数据


图表名词解析
------------

除了相关属性的解释，最重要的还是要了解下echarts多样化的图表样式

.. list-table::
    :widths: 25 50
    :header-rows: 1

    * - 名词
      - 描述
       
    * - line
      - 折线图，堆积折线图，区域图，堆积区域图。
         
    * - bar
      - 柱形图（纵向），堆积柱形图，条形图（横向），堆积条形图。
      
    * - scatter
      - 散点图，气泡图。散点图至少需要横纵两个数据，更高维度数据加入时可以映射为颜色或大小，当映射到大小时则为气泡图
     
    * - k
      - K线图，蜡烛图。常用于展现股票交易数据。
        
    * - pie
      - 饼图，圆环图。饼图支持两种（半径、面积）南丁格尔玫瑰图模式。
        
    * - radar
      - 雷达图，填充雷达图。高维度数据展现的常用图表。
      
    * - chord
    * - 和弦图。常用于展现关系数据，外层为圆环图，可体现数据占比关系，内层为各个扇形间相互连接的弦，可体现关系数据
     
    * - force
      - 力导布局图。常用于展现复杂关系网络聚类布局。
        
    * - map
      - 地图。内置世界地图、中国及中国34个省市自治区地图数据、可通过标准GeoJson扩展地图类型。支持svg扩展类地图应用，如室内地图、运动场、物件构造等。
      
    * - heatmap
      - 热力图。用于展现密度分布信息，支持与地图、百度地图插件联合使用。
      
    * - gauge
      - 仪表盘。用于展现关键指标数据，常见于BI类系统。
      
    * - funnel
      - 漏斗图。用于展现数据经过筛选、过滤等流程处理后发生的数据变化，常见于BI类系统。
      
    * - evnetRiver
      - 事件河流图。常用于展示具有时间属性的多个事件，以及事件随时间的演化。
      
    * - treemap
      - 矩形式树状结构图，简称：矩形树图。用于展示树形数据结构，优势是能最大限度展示节点的尺寸特征。
      
    * - venn
      - 韦恩图。用于展示集合以及它们的交集。
     
    * - tree
      - 树图。用于展示树形数据结构各节点的层级关系
      
    * - wordCloud
      - 词云。词云是关键词的视觉化描述，用于汇总用户生成的标签或一个网站的文字内容


示例代码

.. code-block:: html
    :linenos:

    var dom = document.getElementById('dom-id');
    var chart = echarts.init(dom);

    var option = {
        
        legend: {...},
        grid: {...},
        tooltip: {...},
        toolbox: {...},
        dataZoom: {...},
        visualMap: {...},
        xAxis: [
            {type: 'category', ...},
            {type: 'category', ...},
            {type: 'value', ...}
        ],
        yAxis: [{...}, {...}],
        // 这里有多个系列，也是构成一个数组。
        series: [
            // 每个系列，也有 type 描述“子类型”，即“图表类型”。
            {type: 'line', data: [['AA', 332], ['CC', 124], ['FF', 412], ... ]},
            {type: 'line', data: [2231, 1234, 552, ... ]},
            {type: 'line', data: [[4, 51], [8, 12], ... ]}
        }]
    };

    chart.setOption(option);

.. note::
    首先1、2行创建 echarts 实例并初始化该实例对象。其次定义option，option是个大的JavaScript对象且option每个属性是一类组件。
    在定义组件时，若有多个同类组件，那么该组件设置的值为一个数组，数组每项表示一个组件实例，用type定义子组件类型。
    最后调用setOption将option输入echarts，然后echarts渲染图表。


好了，对于echarts的简介就先到这。后面章节再对echarts的各种图表的建立进行详细阐述。