## 规范的目的
> 规范是为了让协作更轻松，代码更容易让团队成员阅读，并且有助于程序合理的抽象并提高程序质量，降低维护难度，使程序可以长久的迭代更新。
> 遵循规范也可让自己更容易得到提高，理清思路，降低程序复杂度，从而能实现更复杂的系统。
> 能力提升之后还能涨工资！

### 基本编码风格
- 遵循[PSR-2](http://www.php-fig.org/psr/psr-2/) ([PSR-2中文版](https://segmentfault.com/a/1190000002521620))
- 使用[PhpDoc](https://zh.wikipedia.org/wiki/PHPDoc)注释所有方法和变量
- 自定义变量**统一**使用小驼峰`$someAttribute`，数据库字段使用下划线`user_id`
- 常量**必须**是大写字母单词_开头，后面允许跟中文(中文项目) `const STATUS_启用`

### 编辑器
- PhpStorm(使用`Ctrl+Alt+L`格式化代码默认PSR-2风格)
- **建议**录制宏，把`Ctrl+Alt+L`,`Ctrl+S`录制为一个宏，再把快捷键`Ctrl+S`绑定到这个宏
- **尽量**全部变量和方法做到PhpStorm识别，不能识别的加上限定或者PhpDoc注释来帮助识别
- use导入使用`Ctrl+Alt+O`优化

### 命名规范
- 使用准确的词来命名，可以查词典，尽量不要引起歧义
- **不要**使用自己发明的缩写
- **不要**使用没有明确意义的变量名：`$a, $x`，应该是`$article, $order`
- **避免**使用意义太宽泛的变量名：`$item`
- 变量内容是数组/列表的，**必须**使用复数变量名：`$articles`，或者带Array后缀：`$articleArray`
- 方法返回值是数组列表的，方法名**必须**体现出复数结果

### 代码组织
- 控制器只体现主要业务流程，不放具体实现代码
- 业务实现放在模型中实现，并提供给控制器调用，每个方法实现单一功能，做到可复用。
- 每个方法前做好注释，指明方法的用途，参数复杂的加上参数示例

### Yii2框架相关规范
- 数据库与`ActiveRecord`模型时刻对应。可以使用Gii生成，再写一个继承它
- 数据库使用`migration`来加入版本控制，`up`/`down`方法都要实现
- 已提交的`migration`不允许修改，新建一个`migration`来修改
- 数据库模型间建立好`hasOne`，`hasMany`关联，`hasOne`用get+模型名单数，`hasMany`用get+模型名复数
- 尽量使用对象而非数组，只有在数据量特别大时使用数组节省内存
- 获取数据时使用`with`而非`joinWith`，只有需要联表查询时才需要`joinWith`
- **避免**手写SQL，**建议**使用Query模型来复用查询条件
- 模型如果没有特定继承的类，都继承Yii的`\yii\base\Model`或`\yii\base\Component`
- 模型放到对应的`Application`中，共用的放到`common`中
- 共用模型但是方法不共用的，在所在的`Application`中新建模型并继承`common`中的模型

### 版本控制
- 每次提交实现单一功能或修改
- 提交的commit message第一行(20字以内)需要能准确描述提交的内容
- 更具体的描述可以放在第二行之后
- **建议**完成不影响正常运行的阶段性修改后做一个提交
- **尽量**每一次提交都是可正常运行的
- **避免**多个功能一起提交
- **不要**一天就下班提交一次
- **不要**提交空的commit message，空的修改应该也是不存在的
- **不要**好几个提交都是一样的message
- 对于旧代码的格式化，**避免**和修改内容一起提交，格式化可以单独作为一次提交
