#表单验证控件
##需求分析
- 用户完整一项目输入后经验单项验证；显示错误标示和提示文案；
- 提交表单前对需要验证的所有项进行验证；
- 验证后回调，便于处理业务逻辑；
- 验证动态插入的待验证表单；
- 提过一个判断是否所有验证都通过的方法；

##实现思路
- 使用插件时，需要在对应需要验证的表单上加验证类型的关键字（如requered,email,telphone）;
- Css文件加对应，错误、警告、成功的样式；
- 对象实例化后，检查表单是否存在；获取form中需要验证的表单；
- 对验证规则数据格式进行格式化
- 遍历出需要验证的项（即加关键字的表单）；
- 给每一项绑定事件，触法事件执行验证方法，（事件类型可以在配置文件里设置，默认是blur）;
- 验证方法完成后调用执行回调；
- 提交时先阻止默认事件，执行一遍所有验证项，全部通过执行回调然后才执行提交操作；

### 验证规则设置分三种类型：
- 定义正则表达式，取值后直接用该正则表达式来验证（如input）
- 定义验证方法，触发时调用定义好的方法来验证（如单选、多选表单的验证）
- 定义一个包含已有规则名称的数组，即可调用已有的验证方法和表达式进行组合验证

##使用流程：
1.实例化，获取form中需要验证的表单；
2.对验证规则数据格式进行格式化
3.给需要验证的元素绑定事件
4.直接点击提交按钮，对全部需要验证项目进行遍历验证
5.验证前后加回调（全部验证完成后加回调）