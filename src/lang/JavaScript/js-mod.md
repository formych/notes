# js模块

## JS模块

### CommonJS

思想: javascript not just for browsers any more
使用: Node.js, webpacp和Apache的CouchDB
演变:
    1.Modules/1.x 流派
    2.Modules/Async 流派(AMD)
    3.Modules/2.0 流派(CMD)

模块标识(module)、模块定义(exports) 、模块引用(require)
exports 和 module.exports用来导出一个module
require用来导入一个module

### AMD

    模块异步加载，回调执行
    使用: RequireJS

### CMD

   使用: SeaJS

### SeaJS和RequireJS异同

    同: 异步加载所有依赖的模块（加载顺序）
    异:
        SeaJS只会在真正需要时执行依赖模块，懒执行.
        RequireJS会先尽早地执行依赖模块, 预执行.

### ES模块

export 和 export default

+ export与export default均可用于导出常量、函数、文件、模块等
+ 在一个文件或模块中，export、import可以有多个，export default仅有一个
+ 通过export方式导出，在导入时要加{ }，export default则不需要
+ export能直接导出变量表达式，export default不行

import * from a
import * as x from a

[参考1](https://github.com/seajs/seajs/issues/588)
[参考2](https://segmentfault.com/a/1190000010426778)
