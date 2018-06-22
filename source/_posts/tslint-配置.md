---
title: tslint 配置整理
date: 2018-06-14 15:39:57
tags: [tslint]
---
## adjacent-overload-signatures
### 说明：强制重载方法必须连续

### 示例：
```
"adjacent-overload-signatures": true
```
## align
### 说明：强制垂直对齐
- `"parameters"`:检查函数参数对齐
- `"arguments"`:检查函数调用参数对齐
- `"statements"`:检查声明
- `"members"`:检查类、接口、类型字面量、对象字面量和对象解构的成员对齐
- `"elements"`:检查数组迭代元素、数据结构和元祖类型对齐

### 示例：
```
"align": [true, "parameters", "statements"] 
```

## array-type
### 说明：强制数组使用‘T[]’或‘Array’方式声明
必须使用以下参数之一
- `"array"`:强制使用T[]
- `"generic"`:强制使用Array<T>
- `"array-simple"`:如果T是简单类型（基元或类型引用）,则强制使用T[]

### 示例:

```
"array-type": [true,"array"] 
```
```
"array-type": [true,"generic"] 
```
```
"array-type": [true,"array-simple"]
```

## arrow-parens
### 说明：箭头函数定义的参数需要括号
如果指定 `ban-single-arg-parens`强制只有一个参数的箭头函数不允许带括号

### 示例：
```
"arrow-parens": true 
```
```
"arrow-parens": [true,"ban-single-arg-parens"] 
```

## arrow-return-shorthand
### 说明：建议将`() =>{ return x;}`转换成`() => x`
如果指定了`multiline`，则如果函数跨越多行会发出警告

### 示例：
```
"arrow-return-shorthand": true
```
```
"arrow-return-shorthand": [true,"multiline"]
```

## await-promise
### 说明：不允许没有Promise情况下使用await
### 示例：
```
"await-promise": true
```

## ban-comma-operator
### 说明：禁止使用逗号运算符
### 示例：
```
"ban-comma-operator": true
```

## ban-types
### 说明：禁止使用特定类型
["类型","说明"]
### 示例：
```
"ban-types": [true,["Object","使用{}代替"],["String"]]
```

## ban
### 说明：禁止使用特定函数或全局方法
### 示例：

## binary-expression-operand-order
### 说明：表达式中，字面量应始终位于右侧
例如：'x + 1'优于'1 + x'
### 示例：
```
"binary-expression-operand-order":true
```

## callable-types
### 说明：

## class-name
### 说明：类和接口强制使用帕斯卡命名方法（大驼峰）
### 示例：
```
"class-name":true
```

## comment-format
### 说明：定义单行注释格式
- `"check-space"`:要求所有单行注释必须以空格开始
- `"check-lowercase"`:要求注释的第一个非空格字符为小写
- `"check-lowercase"`:要求注释的第一个非空格字符为大写
- 使用ignore-words和ignore-pattern处理例外情况

### 示例：
```
"comment-format":[true,"check-space","check-uppercase"]
```
```
"comment-format":[true,"check-lowercase",{"ignore-words":["TODO","HACK"]}]
```
```
"comment-format":[true,"check-lowercase",{"ignore-pattern":"STD\\w{2,3}\\b"}]
```

## completed-docs
### 说明：
### 示例：
```
"completed-docs":true 
```

## curly
### 说明：if/for/do/while强制使用花括号
- `"as-needed"`:禁止任何不必要的大括号
- `"ignore-same-link"`:检查大括号的控制流语句在同一行

### 示例：
```
"curly":true 
```
```
"curly":[true,"ignore-same-line"] 
```
```
"curly":[true,"as-needed"] 
```

## cyclomatic-complexity
### 说明：设置循环复杂程度
指定复杂度上线，为指定则默认为20

### 示例：
```
"cyclomatic-complexity":true 
```
```
"cyclomatic-complexity":[true,20] 
```

## deprecation
### 说明：使用已废弃的API时发出警告
### 示例：
```
"deprecation":true 
```

## encoding
### 说明：强制使用UTF-8文件编码
### 示例：
```
"encoding":true 
```

## encoding
### 说明：强制使用UTF-8文件编码
### 示例：
```
"encoding":true 
```

## eofine
### 说明：强制文件以换行符结束
### 示例：
```
"eofine":true 
```

## file-header
### 说明：强制所有文件有特定的头文件注释，并使用正则表达式匹配
### 示例：
```
"file-header":[true,"Copyright \\d{4}","Copyright 2018"] 
```

## forin
### 说明：使用for in语句时，强制进行hasOwnProperty检查
### 示例：
```
"forin":true 
```

## import-blacklist
### 说明：禁止通过 `import`和`require`直接导入指定模块，只有子模块能从该模块导入
### 示例：
```
"import-blacklist":true 
```
```
"import-blacklist":[true,"rxjs","lodash"]
```

## import-spacing
### 说明：import关键字后加空格
### 示例：
```
"import-spacing":true 
```

## indent
### 说明：强制以tab或spaces缩进
- `spaces`:空格
- `tabs`
- `缩进参数`:2/4

### 示例：
```
"indent": [true, "spaces"] 
```
```
"indent": [true, "spaces",4] 
```
```
"indent": [true, "tabs",2] 
```

## interface-name
### 说明：要求接口命名以大写'I'为前缀
- `"always-prefix"`:要求接口命名以'I'为前缀
- `"never-prefix"`:要求接口命名不以'I'为前缀

### 示例：
```
"interface-name":[true,"always-prefix"] 
```
```
"interface-name":[true,"never-prefix"] 
```

## interface-over-type-literal
### 说明：接口声明优于类型字面量(type T = {...})
### 示例：
```
"interface-over-type-literal":true 
```

## jsdoc-format
### 说明：基于jsdoc风格的注释
[参考文档](https://wizardforcel.gitbooks.io/google-javascript-style-guide/content/33.html)
可以使用"check-multiline-start"强制多行注释的第一行为空
### 示例：
```
"jsdoc-format":true 
```
```
"jsdoc-format":[true,"check-multiline-start"] 
```

## label-position
### 说明：仅允许在 do / for / while / switch 中使用标签
### 示例：
```
"label-position":true 
```

## linebreak-style
### 说明：换行符格式配置
- `"LF"`:要求LF(\n)换行
- `"CRLF"`:要求CRLF(\r\n)换行

### 示例：
```
"linebreak-style": [true, "LF"] 
```
```
"linebreak-style": [true, "CRLF"]
 ```

## match-default-export-name
### 说明：要求默认导入和导入声明名字相同，对匿名默认导出无效
### 示例：
```
"match-default-export-name":true 
```

## max-classes-per-file
### 说明：每个文件中可定义类的个数
必填参数：整数（表示可定义类最大数量）
可选参数："exculde-class-expressions"(排除全局类)
### 示例：
```
"max-classes-per-file":[true,1] 
```
```
"max-classes-per-file":[true,5,"exclude-class-expressions"] 
```

## max-file-line-count
### 说明：限定文件代码行数
### 示例：
```
"max-file-line-count":[true,300] 
```

## max-line-length
### 说明：限定每行代码长度
### 示例：
```
"max-file-line-count":[true,300] 
```

## member-access
### 说明：设置成员对象的访问权限
- `"no-public"`:禁止公共可访问性
- `"check-accessor"`:强制get / set可访问
- `"check-constructor"`:强制对构造函数可访问
- `"check-parameter-property"`:强制对参数属性可访问

### 示例：
```
"member-access":true 
```
```
"member-access":[true,"no-public"] 
```
```
"member-access":[true,"check-accessor"] 
```

## member-ordering
### 说明：设置修饰符顺序
必填参数：一个`order`对象，使用"fields-first / instance-sandwich / statics-first"其中之一
或者由以下字符串组成一个数组
- `public-static-field`
- `public-static-method`
- `protected-static-field`
- `protected-static-method`
- `private-static-field`
- `private-static-method`
- `public-instance-field`
- `protected-instance-field`
- `private-instance-field`
- `public-constructor`
- `protected-constructor`
- `private-constructor`
- `public-instance-method`
- `protected-instance-method`
- `private-instance-method`

### 示例：
```
"member-ordering": [true, {"order": "fields-first"}]
```
``` 
"member-ordering": [
  true,
  {
    "order": [
      "public-static-field",
      "public-instance-field",
      "public-constructor",
      "private-static-field",
      "private-instance-field",
      "private-constructor",
      "public-instance-method",
      "protected-instance-method",
      "private-instance-method"
    ]
  }
]
```
``` 
"member-ordering": [
  true,
  {
    "order": [
      {
        "name": "static non-private",
        "kinds": [
          "public-static-field",
          "protected-static-field",
          "public-static-method",
          "protected-static-method"
        ]
      },
      "constructor"
    ]
  }
]
```

## new-parens
### 说明：通过new关键字调用构造函数是需要括号
### 示例：
``` 
"new-parens":true 
```

## newline-before-return
### 说明：具有return的语句块中不止一行时，在return语句前增加空行
### 示例：
``` 
"newline-before-return":true 
```

## newline-per-chained-call
### 说明：要求将链式调用分解成单独的行
### 示例：
``` 
"newline-per-chained-call":true 
```

## no-angle-bracket-type-assertion
### 说明：使用`as Type`方式代替<Type>处理类型断言
### 示例：
``` 
"no-angle-bracket-type-assertion":true 
```

## no-any
### 说明：不允许使用 `any`声明类型
### 示例：
``` 
"no-any":true 
```

## no-arg
### 说明：不允许使用arguments.callee
### 示例：
``` 
"no-arg":true 
```

## no-bitwise
### 说明：不允许使用位操作符
禁止使用：`&`,`&=`,`|`,`|=`,`^`,`^=`,`<<`,`<<=`,`>>`,`>>=`,`>>>`,`>>>=`,`~`
不禁止`&`和`|`用于交集和联合类型
### 示例：
``` 
"no-bitwise":true 
```

## no-boolean-literal-compare
### 说明：与布尔值进行比较是发出警告，如：x===true
### 示例：
``` 
"no-boolean-literal-compare":true 
```

## no-conditional-assignment
### 说明：不允许在条件语句中进=进行任何类型的赋值
### 示例：
``` 
"no-conditional-assignment":true 
```

## no-consecutive-blank-lines
### 说明：不允许有空行
可设置最大允许空行数，不填默认为1
### 示例：
``` 
"no-consecutive-blank-lines":true 
```
``` 
"no-consecutive-blank-lines":[true,2] 
```

## no-console
### 说明：禁止使用控制台方法
可设置指定禁止方法，未设置则默认禁止全部控制台方法
### 示例：
``` 
"no-console":[true,"log","error"] 
```

## no-construct
### 说明：禁止访问`String`,`Number`,`Boolean`的构造函数
不允许使用`new Number(foo)`,但不禁止`Number(foo)`
### 示例：
``` 
"no-construct":true 
```

## no-debugger
### 说明：不允许是debugger
### 示例：
``` 
"no-debugger":true 
```

## no-default-export
### 说明：不允许ES6-style模块默认导出，使用命名导出
### 示例：
``` 
"no-default-export":true 
```

## no-duplicate-imports同一统一模块
### 示例：
``` 
"no-duplicate-imports":true 
```

## no-duplicate-super
### 说明：构造函数中出现两次super()发出警告
### 示例：
``` 
"no-duplicate-super":true 
```

## no-duplicate-switch-case
### 说明：防止switch语句中出现重复
### 示例：
``` 
"no-duplicate-switch-case":true 
```

## no-duplicate-variable
### 说明：不允许在同已作用域中重复声明变量
### 示例：
``` 
"no-duplicate-variable":true 
```

## no-duplicate-variable
### 说明：不允许在同已作用域中重复声明变量
可以使用"check-parameters"检查与参数同名的变量
### 示例：
``` 
"no-duplicate-variable":true 
```
``` 
"no-duplicate-variable":[true,"check-parameters"] 
```

## no-dynamic-delete
### 说明：禁止对动态计算key的表达式执行删除操作
### 示例：
``` 
"no-dynamic-delete":true 
```

## no-empty-interface
### 说明：不允许空接口
### 示例：
``` 
"no-empty-interface":true 
```

## no-empty
### 说明：禁止空白块
- `"allow-empty-catch"`:表示允许catch块为空
- `"allow-empty-functions"`:表示允许函数定义为空

### 示例：
``` 
"no-empty":true 
```
``` 
"no-empty":[true,"allow-empty-catch"] 
```
``` 
"no-empty":[true,"allow-empty-functions"] 
```
``` 
"no-empty":[true,"allow-empty-catch","allow-empty-functions"] 
```

## no-eval
### 说明：不允许使用eval()
### 示例：
``` 
"no-eval":true 
```

## no-floating-promises
### 说明：必须正确处理函数返回的promises
附加参数的类也作为promises处理
### 示例：
``` 
"no-floating-promises":true 
```
``` 
"no-floating-promises":[true,"JQueryPromise"] 
```

## no-for-in-array
### 说明：不允许对Array使用for in
### 示例：
``` 
"no-for-in-array":true 
```

## no-implicit-dependencies
### 说明：
不允许导入未在package.json中列为依赖项的模块
不允许导入安装在根目录上的临时依赖项和模块

默认情况下检查"dependencies"和"peerDependencies"
`"dev"`:检查"dependencies"而不是"peerDependencies"
`"optional"`会检查"optionalDependecies"
### 示例：
``` 
"no-implicit-dependencies":true 
```
``` 
"no-implicit-dependencies":[true,"dev"] 
```
``` 
"no-implicit-dependencies":[true,"optional"] 
```

## no-import-side-effect
### 说明：避免导入具有副作用的语句
参数`"ignore-module"`:允许指定一个正则表达式忽略它匹配的模块
### 示例：
``` 
"no-import-side-effect":true 
```
``` 
"no-import-side-effect": [true, {"ignore-module": "(\\.html|\\.css)$"}]
```

## no-inferrable-types
### 说明：不允许显示声明number / string / boolean类型
- `ignore-params`:允许为函数参数指定一个可推断类型
- `ignore-properties`:允许为对象属性指定一个可推断类型
### 示例：
``` 
"no-inferrable-types":true 
```
``` 
"no-inferrable-types":[true,"ignore-params"] 
```
``` 
"no-inferrable-types":[true,"ignore-params","ignore-properties"] 
```

## no-interred-empty-object-type
### 说明：不允许在函数和调用构造函数时使用{}(空对象)类型推断
### 示例：
``` 
"no-interred-empty-object-type":true 
```

## no-internal-module
### 说明：禁止内部模块
### 示例：
``` 
"no-internal-module":true 
```

## no-invalid-template-string
### 说明：只允许在模板字符串中使用`${`
### 示例：
``` 
"no-invalid-template-string":true 
```

## no-invlid-this
### 说明：不允许在class外部使用this关键字
### 示例：
``` 
"no-invlid-this":true 
```

## no-invlid-this
### 说明：不允许在class外部使用this关键字
`check-function-in-method`:不允许在类方法中的函数中使用this关键字
### 示例：
``` 
"no-invlid-this":true 
```
``` 
"no-invlid-this":[true,"check-function-in-method"] 
```

## no-irregular-whitespace
### 说明：禁止文中不规则空白，包括字符串和注释
### 示例：
``` 
"no-irregular-whitespace":true 
```

## no-magic-numbers
### 说明：不允许在变量赋值之外使用常量数值，如未指定允许值列表，默认允许-1 / 0 / 1
### 示例：
``` 
"no-magic-numbers":true 
```
``` 
"no-magic-numbers":[true,1,2,3] 
```

## no-mergeable-namespace
### 说明：同一文件中禁止可合并的命名空间
### 示例：
``` 
"no-mergeable-namespace":true 
```

## no-misused-new
### 说明：为接口或类定义新构造函数时发出警告
### 示例：
``` 
"no-misused-new":true 
```

## no-namespace
### 说明：禁止使用内部模块和命名空间，允许使用`declare module ...{}`
- `allow-declarations`:允许使用`declare namespace ...{}`描述外部API
### 示例：
``` 
"no-namespace":true 
```
``` 
"no-namespace":[true,"allow-declarations"] 
```

## no-non-null-assertion
### 说明：不允许非空断言使用`!`后缀操作符
### 示例：
``` 
"no-non-null-assertion":true 
```

## no-null-keyword
### 说明：不允许使用null关键字面量
### 示例：
``` 
"no-null-keyword":true 
```

## no-object-literal-type-assertion
### 说明：类型断言中禁止对象字面量出现
### 示例：
``` 
"no-object-literal-type-assertion":true 
```

## no-parameter-properties
### 说明：禁止在类构造函数中使用参数属性
### 示例：
``` 
"no-parameter-properties":true 
```

## no-parameter-reassignment
### 说明：不允许修改方法输入参数
### 示例：
``` 
"no-parameter-reassignment":true 
```

## no-redundant-jsdoc
### 说明：禁止复制ts功能的JSDoc
### 示例：
``` 
"no-redundant-jsdoc":true 
```

## no-reference-import
### 说明：如果导入`foo`,不要使用`<reference types="foo" />`
### 示例：
``` 
"no-reference-import":true 
```

## no-reference
### 说明：禁止使用`/// <reference path=>`导入(使用ES6-style导入代替)
### 示例：
``` 
"no-reference":true 
```

## no-require-imports
### 说明：禁止调用`require()`
### 示例：
``` 
"no-require-imports":true 
```

## no-return-await
### 说明：禁止不必要的 `return await`
### 示例：
``` 
"no-return-await":true 
```

## no-shadowed-variable
### 说明：禁止遮蔽变量声明
### 示例：

## no-sparse-arrays
### 说明：不允许Array中有空元素
### 示例：
``` 
"no-sparse-arrays":true 
```

## no-string-literal
### 说明：禁止访问不必要的字符串字面量属性
### 示例：
``` 
"no-string-literal":true 
```

## no-string-throw
### 说明：不允许throw一个字符串
### 示例：
``` 
"no-string-throw":true 
```

## no-submodule-imports
### 说明：不允许导入任何子模块，可是只白名单
### 示例：
``` 
"no-submodule-imports":true 
```
``` 
"no-submodule-imports":[true, "rxjs", "@angular/platform-browser", "@angular/core/testing"]
```

## no-switch-case-fall-through
### 说明：不允许case段落中没有break的情况下，重新开始一段case逻辑
### 示例：
``` 
"no-switch-case-fall-through":true 
```

## no-this-assignment
### 说明：禁止对this的不必要引用
- `allow-destructuring`:允许使用解构来访问this
- `allowed-names`:可指定正则表达式以匹配允许的变量名

### 示例：
``` 
"no-this-assignment":true 
```
```
"no-this-assignment": [true, {"allowed-names": ["^self$"], "allow-destructuring": true}]
```

## no-trailing-whitespace
### 说明：不允许空格结尾
- `ignore-template-strings`:模板字符串例外
- `ignore-comments`:注释例外
- `ignore-jsdoc`:JSDoc注释例外
- `ignore-blank-line`:空行例外

### 示例：
``` 
"no-trailing-whitespace":true 
```
``` 
"no-trailing-whitespace":[true,"ignore-comments"] 
```
``` 
"no-trailing-whitespace":[true,"ignore-jsdoc"] 
```

## no-unbound-method
### 说明：在方法调用之外使用方法时发出警告
使用"ignore-static"忽略静态方法
### 示例：
``` 
"no-unbound-method":true 
```
``` 
"no-unbound-method":[true,"ignore-static"] 
```

## no-unnecessary-callback-wrapper
### 说明：使用`f`代替`x => f(x)`
### 示例：
``` 
"no-unnecessary-callback-wrapper":true 
```

## no-unnecessary-class
### 说明：不允许不严格需要的类
- `allow-constructor-only`:忽略成员是构造函数的类
- `allow-empty-class`:忽略空类
- `allow-static-only`:忽略静态成员类

### 示例：
``` 
"no-unnecessary-class":true 
```
``` 
"no-unnecessary-class":["allow-empty-class","allow-constructor-only"] 
```

## no-unnecessary-initializer
### 说明：禁止 var / let 或解构初始化被初始为undefined
### 示例：
``` 
"no-unnecessary-initializer":true 
```

## no-unnecessary-qualifier
### 说明：禁止没有必要的修饰符
### 示例：
``` 
"no-unnecessary-qualifier":true 
```

## no-unnecessary-type-assertion
### 说明：禁止没有必要的类型断言
### 示例：
``` 
"no-unnecessary-type-assertion":true 
```

## no-unsafe-any
### 说明：不允许动态方式使用any类型表达式，{} / null / undefined下允许
### 示例：
``` 
"no-unsafe-any":true 
```

## no-unsafe-finally
### 说明：不允许在finally语句中使用return/continue/break/throw
### 示例：
``` 
"no-unsafe-finally":true 
```

## no-unused-expression
### 说明：禁止使用未使用的表达式语句
- `allow-fast-null-checks`:
- `allow-new`:
- `allow-tagged-template`:

### 示例：
``` 
"no-unused-expression":true 
```
``` 
"no-unused-expression":[true, "allow-fast-null-checks"] 
```

## no-unused-variable
### 说明：禁止未使用的imports / variables / functions和私有成员
- `check-parameters`:不允许使用未使用的函数和构造函数参数
- `{"ignore-pattern":"pattern"}`:与正则表达式匹配的变量和导入将被忽略

### 示例：
``` 
"no-unused-variable":true 
```
``` 
"no-unused-variable":[true, {"ignore-pattern": "^_"}] 
```

## no-use-before-declare
### 说明：在使用应用之前必须声明
### 示例：
``` 
"no-use-before-declare":true 
```

## no-var-keyword
### 说明：不允许使用var关键字
### 示例：
``` 
"no-var-keyword":true 
```

## no-var-requires
### 说明：除了在import语句中，禁止使用require
### 示例：
``` 
"no-var-requires":true 
```

## no-void-expression
### 说明：期望出现void返回类型
设置`ignore-arrow-function-shorthand`参数时，`() => returnsVoid()`被允许，否则只能写成`() =>{ returnsVoid(); }`
### 示例：
``` 
"no-void-expression":true 
```
``` 
"no-void-expression":[true,"ignore-arrow-function-shorthand"] 
```

## number-literal-format
### 说明：检查小数应该从`0.`开始，而不是从`.`开始，并且不以`0`结尾
### 示例：
``` 
"number-literal-format":true 
```

## object-literal-key-quotes
### 说明：统一对象字面量属性引号格式
- `always`:属性名始终需要引号(默认情况)
- `as-needed`:必要情况下才使用引号(例如带空格的情况)
- `consistent`:属性名应该统一使用引号或者不使用引号
- `consistent-as-needed`:如果属性名称需要引号，则必须引用所有属性。 否则，不使用。
### 示例：
``` 
"object-literal-key-quotes":[true,"always"] 
```
``` 
"object-literal-key-quotes":[true,"as-needed"] 
```

## object-literal-shorthand
### 说明：强制或者禁止使用ES6对象字面量简写，'never'参数表示禁止
### 示例：
``` 
"object-literal-shorthand":true 
```
``` 
"object-literal-shorthand":[true,"never"] 
```

## object-literal-sort-keys
### 说明：检查对象中key的排序，默认情况下以字母表顺序排列
- `ignore-case`:不区分大小写
- `match-declaration-order`:依据上下文语境，如果没有上下文则依据字母表顺序，例如：`interface I { foo: number; bar: number; } const obj: I = { foo: 1, bar: 2 };`
- `shorthand-first`:简短属性优先
### 示例：
``` 
"object-literal-sort-keys":true 
```
``` 
"object-literal-sort-keys":[true, "ignore-case", "match-declaration-order", "shorthand-first"]
```

## one-line
### 说明：要求指定的参数与上一个表达式位于同一行
- `check-catch`:紧跟try语句后
- `check-finally`:紧跟catch语句后
- `check-else`:紧跟if语句后
- `check-open-brace`:大括号紧跟上一语句
- `check-whitespace`:指定标记前增加空格

例如：
```
//正确写法
if(...){
  ...
} else { // else需要放在这一行
  ...
}
// 会发出警告
if(...){
  ...
} 
else { 
  ...
}
```

### 示例：
``` 
"one-line": [true, "check-catch", "check-finally", "check-else"]
```

## one-variable-per-declaration
### 说明：不允许在一个声明语句中定义多个变量
`ignore-for-loop`:循环语句除外
### 示例：
``` 
"one-variable-per-declaration":true 
```
``` 
"one-variable-per-declaration":[true,"ignore-for-loop"] 
```

## only-arrow-functions
### 说明：禁止使用传统函数(非箭头)表达式
- `allow-declarations`:允许独立函数声明
- `allow-named-functions`:允许`function foo() {}`但不允许`function() {}`

### 示例：
``` 
"only-arrow-functions":true 
```
``` 
"only-arrow-functions":[true,"allow-declarations","allow-named-functions"]
```

## ordered-imports(未完)
### 说明：导入语句依据字母表顺序排列分组
### 示例：
``` 
"ordered-imports":true 
```

## prefer-conditional-expression
### 说明：优先选择条件表达式代替多余的if语句
`check-else-if`:该参数会检查嵌套的if-eles-if语句
### 示例：
``` 
"prefer-conditional-expression":true 
```
``` 
"prefer-conditional-expression":[true,"check-else-if"] 
```

## prefer-const
### 说明：尽可能使用`const`代替`let / var`进行变量声明，如果变量只被赋值一次，应该使用`const`
`any`:默认参数
`all`:只有解构函数中所有的变量都为常量时发出警告
### 示例：
``` 
"prefer-const":true 
```
``` 
"prefer-const":[true,{"destructuring":"all"}] 
```

## prefer-for-of
### 说明：如果for循环中没有使用索引，建议使用for-of
### 示例：
``` 
"prefer-for-of":true 
```

## prefer-function-over-method
### 说明：警告不使用this的类方法
- `allow-public`:不检查公共方法
- `allow-protected`:不检查受保护方法
### 示例：
``` 
"prefer-function-over-method":true 
```
``` 
"prefer-function-over-method":[true,"allow-public","allow-protected"] 
```

## prefer-method-signature
### 说明：在接口和类型中，首选`foo():void`而不是`foo: () => void`
### 示例：
``` 
"prefer-method-signature":true 
```

## prefer-object-spread
### 说明：在恰当的使用ES6的对象展开运算符代替`Object.assign()`
### 示例：
``` 
"prefer-object-spread":true 
```

## prefer-readonly
### 说明：如果私有变量未在构造函数外被修改过或者只在构造函数中被赋值，应被标记为只读
- `only-inline-lambdas`:只检查立即声明的箭头函数
### 示例：
``` 
"prefer-readonly":true 
```
``` 
"prefer-readonly":[true."only-inline-lambdas"] 
```

## prefer-switch
### 说明：简单的`===`比较，优先选择`switch`
- `min-cases`:推荐使用switch的最小case个数，默认为3
### 示例：
``` 
"prefer-switch":true 
```
``` 
"prefer-switch":[true,{"min-cases":2}] 
```

## prefer-template
### 说明：优先使用模板字符串代替字符串拼接
- `allow-single-concat`:允许单个拼接(x+y),不允许多个拼接(x+y+z)
### 示例：
``` 
"prefer-template":true 
```
``` 
"prefer-template":[true,"allow-single-concat"] 
```

## prefer-while
### 说明：没有初始值和增量的循环优先选择while
### 示例：
``` 
"prefer-while":true 
```

## promise-function-async
### 说明：要求函数或方法返回一个被标记为异步的promise,默认为检查所有，以下参数可选
- `check-function-declaration`:检查函数声明
- `check-function-expression`:检查函数表达式
- `check-arrow-function`:检查箭头函数
- `check-method-declaration`:检查方法声明

### 示例：
``` 
"promise-function-async":true 
```
``` 
"promise-function-async":[true, "check-function-declaration", "check-method-declaration"]
```

## quotemark(未完)
### 说明：
### 示例：
``` 
"quotemark":true 
```

## radix
### 说明：使用parseInt时，必须输入radix精度参数
### 示例：
``` 
"radix":true 
```

## restrict-plus-operands
### 说明：两个变量相加时，操作数必须都是数字类型或者字符串类型，即不允许自动类型转换
### 示例：
``` 
"restrict-plus-operands":true 
```

## return-undefined
### 说明：在void函数中使用`return;`,有返回值的函数中使用`return undefined`
### 示例：
``` 
"return-undefined":true 
```

## semicolon
### 说明：强制语句结尾使用分号
必填参数
- `always`:语句结尾一律使用分号
- `never`:除了必要时，语句结尾一律不使用分号
选填参数
- `ignore-interfaces`:接口成员末尾跳过分号检查
- `ignore-bound-class-methods`:绑定类方法末尾跳过分号检查
- `strict-bound-class-methods`:禁止绑定类方法的特殊处理，该设置会覆盖`ignore-bound-class-methods`

### 示例：
``` 
"semicolon":[true,"always"] 
```
``` 
"semicolon":[true,"never"] 
```
``` 
"semicolon":[true,"always","ignore-interfaces"] 
```
``` 
"semicolon":[true,"always","ignore-bound-class-methods"] 
```

## space-before-function-paren
### 说明：配置函数括号前的空格
- 对象参数中key值为`anonymous / named / asyncArrow`时，需要设置值为"always"或"never"
- `anonymous`:检查匿名函数括号前空格
- `named`:检查命名函数括号前空格
- `asyncArrow`:检查异步箭头函数
- `method`:检查类方法
- `constructor`:检查构造函数

### 示例：
``` 
"space-before-function-paren":true 
```
``` 
"space-before-function-paren":[true,""always] 
```
``` 
"space-before-function-paren":[true,"never"] 
```
``` 
"space-before-function-paren":[true,{"anonymous": "always", "named": "never", "asyncArrow": "always"}] 
```

## space-within-parens
### 说明：配置括号内的空格
### 示例：
``` 
"space-within-parens":true 
```
``` 
"space-within-parens":[true,1] 
```

## strict-boolean-expressions(未完)
### 说明：配置括号内的空格
### 示例：
``` 
"strict-boolean-expressions":true 
```

## strict-type-predicates
### 说明：警告始终为真或始终为假的类型判断
### 示例：
``` 
"strict-type-predicates":true 
```

## switch-default
### 说明：要求switch语句必须有default
### 示例：
``` 
"switch-default":true 
```

## switch-final-break
### 说明：检查switch最后一个子句是否以break结束
如果没有设置参数，则最后一个子句不能以`break;`结尾
如果设置了always参数，则最后一个子句必须以`break;`结尾
### 示例：
``` 
"switch-final-break":true 
```
``` 
"switch-final-break":[true,"always"] 
```

## trailing-comma(未完)
### 说明：配置对象字面量 / 结构赋值 / function typings / 命名导入导出 / 函数参数的尾随逗号
### 示例：
``` 
"trailing-comma":true 
```

## triple-equals
### 说明：必须使用恒等号进行等于比较
- `allow-null-check`:与null进行比较是允许使用`==`和`!=`
- `allow-undefined-check`:与undefined进行比较是允许使用`==`和`!=`
### 示例：
``` 
"triple-equals":true 
```
``` 
"triple-equals":[true, "allow-null-check"]
```
``` 
"triple-equals":[true, "allow-undefined-check"]
```

## type-literal-delimiter
### 说明：检查类型字面量成员是否以分号分隔，强制多行类型字面量尾随分号
### 示例：
``` 
"type-literal-delimiter":true 
```

## typedef-whitespace(未完)
### 说明：
### 示例：
``` 
"typedef-whitespace":true 
```

## typedef(未完)
### 说明：
### 示例：
``` 
"typedef":true 
```

## typeof-compare
### 说明：确保typeof与正确的值进行比较
### 示例：
``` 
"typeof-compare":true 
```

## unified-signatures
### 说明：警告可以使用联合或者 optional/rest合并成为一个的重载
### 示例：
``` 
"unified-signatures":true 
```

## use-default-type-parameter
### 说明：警告指定参数类型是该类型的默认值
### 示例：
``` 
"use-default-type-parameter":true 
```

## use-isnan
### 说明：只允许使用isNaN方法检查数字是否有效
### 示例：
``` 
"use-isnan":true 
```

## variable-name(未完)
### 说明：
### 示例：
``` 
"variable-name":true 
```

## whitespace(未完)
### 说明：
### 示例：
``` 
"whitespace":true 
```

