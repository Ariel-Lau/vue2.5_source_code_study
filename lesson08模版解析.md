## 模版解析 v-text/{{}}

## 模版解析的基本流程
* 1）将el的所有子节点取出，添加到一个新建的documentFragment（文档碎片）对象中
* 2）对fragment中的所有层次子节点递归进行编译解析处理
  * 对大括号表达式文本节点进行解析
  * 对元素节点的指令属性进行解析
    * 事件指令解析
* 3）将解析后的fragment添加到el中显示

## 模版解析（1）：大括号表达式解析
* 1）根据正则对象得到匹配出的表达式字符串：子匹配/RegExp.$1  如：name
* 2）从data中取出表达式的属性值——>value
* 3）将属性值设置为文本节点的textContent——>textContent
  

## 模版解析（2）：事件指令解析
* 1）从指令名中取出事件名
* 2）根据指令的值（表达式）从methods中得到对应的事件处理函数对象
* 3）给当前元素节点绑定指定事件名和回调函数的dom事件监听
* 4）指令解析完后，移除此指令属性

## 模版解析（3）：一般指令解析
* 1）得到指令名和指令值（表达式）text/html/class msg/myClass
* 2）从data中根据表达式得到对应的值
* 3）根据指令名确定需要操作元素节点的什么属性
  * v-text——textContent属性
  * v-html——innerHTML属性
  * v-class——className属性
* 4）将得到的表达式的值设置到对应的属性上
* 5）移除元素的指令属性