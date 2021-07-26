
动画特效
^^^^^^^^^^^^^^^
什么是css动画
-------------------
动画就是使元素从一种样式逐渐转变为另一种样式，使用css动画可实现元素的动画效果而不使用JavaScript和Flash，可以随意更改任意数量的css属性，
很容易的就能够实现各种炫酷的动画效果，虽然刚开始接触只是看到别人的成果图会觉得很难，但要是了解动画原理、掌握了各种的动画属性，
那么您就会对这些炫酷的效果有了更清晰的视野，还会感受到css动画的乐趣所在。
动画无非不就是在使用多张静态的“图片”顺序播放形成的。
有过Flash动画基础的同学肯定会对"关键帧"这一概念有所耳闻，无论是处理视频还是音频，在特定的地方合适的插入关键帧进行操作可以得到较好的符合预期的效果。
而css动画也离不开关键帧，假如您想做出一些简单的动画，必须首先为动画指定一些关键帧（keyframe），关键帧包含元素在特定时间所拥有的样式


@keyframe
--------------
既然说到了关键帧（keyframe），那就来简单讲讲关键帧的使用方法。如果在@keyframe的规则中指定了css样式，则该动画将在某一特定时间从当前样式更改为新样式。
让我们回忆一下js中构造函数，创建的方法需要被调用才能发挥它的作用，否则就仅仅是占用内存的字符。同理，我们也需要为某一元素”调用“我们所创建的关键帧才能让其展现出相应的效果。

关键帧的使用
>>>>>>>>>>>>>>

:定义:
@keyframe (你为keyframe命名的名字)

:使用:
animation-name：(你为keyframe命名的名字)

.. code-block::  css
    :linenos:

    //创建
	@keyframe example{
		from{
			/**原样式*/
			}
		to{
			/**新样式*/
			}
	}
	
	//调用
	div{
			animation-name:example
		}


与from to相似的是，我们可以使用0% 100%来替代它。那有人就会有疑问，是不是可以用0%～100%之中某一个值来定义过程中的某个关键帧呢？答案是肯定的。
我们可以使用25%、50%、75%等等来表示动画某个过程帧的css样式。

.. note::
    如果省略某个状态，浏览器会自动推算中间状态，而为了获取浏览器最佳支持，应该始终定义0%和100%的选择器。

与css相似，可以将多个状态写在同一行。

.. code-block:: css
    :linenos:
	
	@keyframe example{
		0%{color:red}
		20%{color:yellow}
		50%{color:green}
		100%{color:blue}
	}
	
	@keyframe exampleI{
		0%,50%{
        /**css*/
		}
		100%{
        /**css*/
		}	

对于这种定义帧的方法，我们可以更加直观地看出动画何时变化，同时也感觉更加丰富了动画的多样性。

动画持续时间
----------------
有意思的是动画属性几乎都是以
**animation-**
开头，再加上一个相关意义的后缀结尾。相信聪明的你依旧猜到这一小节要说的属性为animation-duration。
该属性定义了要多长时间才能完成动画，您可以定义动画持续时间单位为秒，也可以定义成毫秒，当然为了不产生歧义以及保证代码的可读性，我们需要在设置参数时写明单位。


.. note::
    必须定义动画持续时间，否则动画效果将无从谈起


一些其他的动画属性
------------------

animation-timing-function
>>>>>>>>>>>>>>>>>>>>>>>>>>>>

这个属性是指定动画将如何完成一个周期的，对如何完成动画没有概念？先来看看下表该属性的合法值及其相关意义。


.. list-table:: 
    :widths: 25 75
    :header-rows: 1


    * - 值
      - 说明

    * - linear
      - 动画从头到尾速度相同

    * - ease
      - 默认，动画以低速开始，然后加快，在结束前变慢

    * - ease-in
      - 动画以低速开始

    * - ease-out
      - 动画以低速结束

    * - ease-in-out
      - 动画以低速开始和结束

    * - cubic-bezier(n，n，n，n)
      - 三次贝塞尔曲线/速度曲线，在该函数中自定义0～1的值

    * - step-start
      - 在变化过程中，以下一帧的显示效果来填充间隔动画

    * - step-end
      - 在变化过程中，以上一帧的显示效果来填充动画

    * - steps()
      - 可传入两个参数，第一个是大于零的整数，将动画分成指定数目的小间隔动画，根据第二个参数来决定显示效果。第二个参数接受start和end，设置后和step-start、step-end同义，分成的小间隔动画中判断显示效果。“通俗”来讲，steps()定义了一个阶跃函数，在每个间隔起点或者终点发生阶跃变化，默认为end。


看了上表，应该对如何完成动画有了新的理解。

animation-delay
>>>>>>>>>>>>>>>>>>>>>

该属性定义的是动画延迟播放。既然如此，也应该和- duration属性一样指明延迟的时间单位，但该属性和- duration属性很大不同的是，该属性不是一定的；还有一点比较神奇，就是该属性接受负数为参数。想象下延迟负的n秒是什么概念？——提前播放嘛。也就是说在显示在我们面前的时候，动画已经被向前拉动了n秒的“进度条”

animation-iteration-count
>>>>>>>>>>>>>>>>>>>>>>>>>>>
该属性定义动画播放次数，接受正整数n/infinite，对于的效果循环播放n次/动画无限循环播放。对于一些样式完善，不需要再更改的动画便可以向该参数传递infinite。

animation-direction
>>>>>>>>>>>>>>>>>>>>>>>>>>>

该属性定义是否循环交替反向播放动画，接受的值以及意义如下表所示


.. list-table:: 
	:width: 25 75
	:header-rows: 1
	
	* - normal
	  - 默认值，按正常播放
	
	* - reverse
	  - 动画反向播放
	
	* - alternative
	  - 动画在奇数次正向播放，在偶数次反向播放
	
	* - alternative-reverse
	  - 动画在奇数次反向播放，在偶数次正向播放
	
	* - initial
	  - 设置该属性为它的默认值
	
	* - inherit
	  - 从父元素继承该属性


不过需要注意的是，如果动画播放次数只有一次的话，该属性将不会起作用。而且动画循环播放是，每次都是从结束状态跳回到起始状态再开始播放，但该属性可以重写该行为。

animation-fill-mode
>>>>>>>>>>>>>>>>>>>>>>>>>>>

该属性规定当动画不播放（当动画完成时，或者当动画延迟未开始播放时）应用的元素样式

.. list-table::
	:width: 25 75
	:header-rows: 1
	
	* - none	
	  - 默认值。动画在动画执行之前和之后不会应用任何样式到目标元素。
	
	* - forwards
	  - 在动画结束后（由 animation-iteration-count 决定），动画将应用该属性值。
	
	* - backwards
	  - 动画将应用在 animation-delay 定义期间启动动画的第一次迭代的关键帧中定义的属性值。这些都是 from 关键帧中的值（当 animation-direction 为 “normal” 或 “alternate” 时）或 to 关键帧中的值（当 animation-direction 为 “reverse” 或 “alternate-reverse” 时）。

	* - both
	  - 动画遵循 forwards 和 backwards 的规则。也就是说，动画会在两个方向上扩展动画属性。
	
	* - initial
	  - 设置该属性为它的默认值
	
	* - inherit
	  - 从父元素继承该属性


值得一提的是默认情况下，CSS 动画在第一个关键帧播放完之前不会影响元素，在最后一个关键帧完成后停止影响元素。animation-fill-mode 属性可重写该行为。

:forwads:
表示让动画停留在结束状态，即停留在最后一帧。

:backwords:
当 animation-direction 为 “normal” 或 “alternate” 时，回到第一帧。
当 animation-direction 为 “reverse” 或 “alternate-reverse” 时，停留在最后一帧。


animation-play-state
>>>>>>>>>>>>>>>>>>>>>>>>>>>>

该属性指定动画是否正在运行或者已经暂停，接受的值为paused和running，分别对应的状态为暂停、运行动画。
这是一个网页上比较常见的功能，当我们把鼠标移至某一元素时，原本移动的元素会触发鼠标经过事件从而改变该元素的css类名，而通过对特定的类名绑定不同的动画规则，可实现让原本移动的元素暂停或是移动的效果。


浏览器前缀
------------------

IE 10和Firefox（>= 16）支持没有前缀的animation，firefox（<16）使用-moz-前缀，因为现在firefox的版本也都不低，所以firefox都直接使用没有前缀的animation。而chrome，safari，opera不支持，所以必须使用webkit前缀。示例代码如下所示。

.. code-block:: css
	:linenos:
	
	div{
    	animation:myAnim 1s;
    	-webkit-animation:myAnim 1s;
	}

	@keyframes myAnim{
  		0% { background: #f00; }
  		50% { background: #0f0; }
  		100% { background: yellowgreen; }
	}

	@-webkit-keyframes myAnim{
    	0% { background: #f00; }
    	50% { background: #0f0; }
    	100% { background: yellowgreen; }
	}


