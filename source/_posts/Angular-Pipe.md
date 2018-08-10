---
title: Angular Pipe
date: 2018-08-07 13:22:30
tags: [Angular]
---

# Angular 6 内置管道

## AsyncPipe - 异步管道

### 说明
AsyncPipe 订阅一个 Observable 或 Promise 对象，并返回它发出的最新值

### 语法
` obj_expression | async`

### 示例
```
@Component({
  selector: 'async-observable-pipe',
  template: '<div><code>observable|async</code>: Time: {{ time | async }}</div>'
})
export class AsyncObservablePipeComponent {
  time = new Observable<string>((observer: Observer<string>) => {
    setInterval(() => observer.next(new Date().toString()), 1000);
  });
}
```

## CurrencyPipe - 货币管道

### 说明
将数值进行货币格式化处理

### 语法
` value_expression | currency [ : currencyCode [ : display [ : digitsInfo [ : locale ] ] ] ]`
- currencyCode: ISO 4217货币码，目标货币格式。如CNY人民币、USD美元、EUR欧元等
- display: 设置该类型货币以哪种格式显示，可选，默认值为`symbol`
  - 'code': 使用货币码，如CNY
  - 'symbol': 使用货币符号，如￥
  - 'symbol-narrow': 针对有两个货币规则的区域，选择使用简单符号，例如加元`symbol`为`CA$`,`symbol-narrow`为`$`
  - string: 使用指定字符串
  - boolean: true表示`symbol`,false表示`symbol-narrow`
- digitsInfo: `{minIntegerDigits}.{minFractionDigits}-{maxFractionDigits}`，可选
  - minIntegerDigits:小数点之前最少显示几位，默认为1
  - minFractionDigits:小数点之后最少显示几位，默认为0
  - maxFractionDigits:小数点之后最多显示几位，默认为3
  - locale:区域代码，如果未提供，则使用LOCALE_ID的值，默认情况下为en-US。可选

### 示例

```
<p>{{0.259 | currency}}</p> <!-- 输出 "$0.26" --> 
<p>{{0.259 | currency:'CAD'}}</p> <!-- 输出 "CA$0.26" --> 
<p>{{0.259 | currency:'CAD':'code'}}</p> <!-- 输出 "CAD0.26" --> 
<p>{{1.3495 | currency:'CAD':'symbol':'4.2-2'}}</p> <!-- 输出 "CA$0,001.35" -->
<p>{{1.3495 | currency:'CAD':'symbol-narrow':'4.2-2'}}</p> <!-- 输出 "$0,001.35" -->
<p>{{1.3495 | currency:'CAD':'symbol':'4.2-2':'fr'}}</p> <!-- 输出 "0 001,35 CA$" -->
<p>{{1.3495 | currency:'CLP'}}</p> <!-- 输出 "CLP1" 智利比索没有分单位货币-->
```

## DatePipe - 时间管道

### 说明
日期格式化

### 语法
` value_expression | date [ : format [ : timezone [ : locale ] ] ]`
- format: 预定义日期格式，可选，默认为`mediumDate`
- timezone: 时区偏移量，可选，默认为用户计算机本地系统时区
- locale: 区域代码，如果未提供，则使用LOCALE_ID的值，默认情况下为en-US。可选


## DecimalPipe - 数值管道

### 说明
依据地区设置规则格式化数字

### 语法
` value_expression | number [ : digitsInfo [ : locale ] ]`
- digitsInfo:`{minIntegerDigits}.{minFractionDigits}-{maxFractionDigits}`，可选
  - minIntegerDigits:小数点之前最少显示几位，默认为1
  - minFractionDigits:小数点之后最少显示几位，默认为0
  - maxFractionDigits:小数点之后最多显示几位，默认为3
  - locale:区域代码，如果未提供，则使用LOCALE_ID的值，默认情况下为en-US。可选
### 示例

```
<p>{{2.718281828459045 | number}}</p> <!-- 输出 "2.718" --> 
<p>{{2.718281828459045 | number:'3.1-5'}}</p> <!-- 输出 "002.71828" --> 
<p>{{2.718281828459045 | number:'4.5-5'}}</p> <!-- 输出 "0,002.71828" --> 
<p>{{2.718281828459045 | number:'4.5-5':'fr'}}</p> <!-- 输出 "0 002,71828" --> 
```

## PercentPipe - 百分比管道

### 说明
将数字转换为百分比字符串，根据分组大小，分隔符，小数点字符以及其他特定于语言环境的配置的区域设置规则进行格式化。

### 语法
`  value_expression | percent [ : digitsInfo [ : locale ] ]  `
- digitsInfo:`{minIntegerDigits}.{minFractionDigits}-{maxFractionDigits}`，可选
  - minIntegerDigits:小数点之前最少显示几位，默认为1
  - minFractionDigits:小数点之后最少显示几位，默认为0
  - maxFractionDigits:小数点之后最多显示几位，默认为3
  - locale:区域代码，如果未提供，则使用LOCALE_ID的值，默认情况下为en-US。可选

### 示例

```
<p>{{0.259 | percent}}</p> <!-- 输出 "26%" --> 
<p>{{1.3495 | percent:'4.3-5'}}</p> <!-- 输出 "0,134.950%" --> 
<p>{{1.3495 | percent:'4.3-5':'fr'}}</p> <!-- 输出 "0 134,950 %" --> 
```

## I18nPluralPipe - I18N复数管道

### 说明
将值映射到字符串，该字符串根据区域设置规则对值进行复数化。

### 语法
` value_expression | i18nPlural : pluralMap [ : locale ] `
- pluralMap:模仿IUC格式的对象
- locale:可选

### 示例
```
@Component({
  selector: 'i18n-plural-pipe',
  template: `<div>{{ messages.length | i18nPlural: messageMapping }}</div>`
})
export class I18nPluralPipeComponent {
  messages: any[] = ['Message 1'];
  messageMapping:
      {[k: string]: string} = {'=0': 'No messages.', '=1': 'One message.', 'other': '# messages.'};
}
```

## I18nSelectPipe - I18n选择管道

### 说明
显示与当前值匹配的字符串的通用选择器。

### 语法
` value_expression | i18nSelect : mapping`
- mapping:表示不同值对应相应文本的一个对象

### 示例
```
@Component(
    {selector: 'i18n-select-pipe', template: `<div>{{gender | i18nSelect: inviteMap}} </div>`})
export class I18nSelectPipeComponent {
  gender: string = 'male';
  inviteMap: any = {'male': 'Invite him.', 'female': 'Invite her.', 'other': 'Invite them.'};
}
//other关键字用于处理其它条件都不成立的情况
```

## JsonPipe - Json管道

### 说明
将值转换为JSON字符串

### 语法
` value_expression | json`

## KeyValuePipe - 键值管道

### 说明
将Object或Map转换为键值对数组,使用keyvalue管道。对象或Map解构可在ngFor中遍历

### 语法

` input_expression | keyvalue [ : compareFn ]`

### 示例

```
@Component({
  selector: 'keyvalue-pipe',
  template: `<span>
    <p>Object</p>
    <div *ngFor="let item of object | keyvalue">
      {{item.key}}:{{item.value}}
    </div>
    <p>Map</p>
    <div *ngFor="let item of map | keyvalue">
      {{item.key}}:{{item.value}}
    </div>
  </span>`
})
export class KeyValuePipeComponent {
  object: {[key: number]: string} = {2: 'foo', 1: 'bar'};
  map = new Map([[2, 'foo'], [1, 'bar']]);
}
```

## LowerCasePipe && UpperCasePipe - 大小写管道

### 说明
将文本全部转换为小写或者大写

### 语法
`  value_expression | lowercase `
`  value_expression | lowercase `

### 示例

```
<p>{{'sOme!&sTring' | lowercase}}</p> <!-- 输出 "some!&string" --> 
<p>{{'sOme!&sTring' | lowercase}}</p> <!-- 输出 "SOME!&STRING" -->
```

## SlicePipe - 截取管道

### 说明
创建一个包含元素自己的新数组或者字符串

### 语法
`  value_expression | slice : start [ : end ]  `
- start:以0为基数，若为负值，则length + start
- end:以0为基数，若为负值，则length + start,若省略则到字符串结尾

### 示例

```
<p>{{'abcdefghij' | slice:0:4}} - 输出 'abcd'</p>
<p>{{'abcdefghij' | slice:4:0}} - 输出 ''</p>
<p>{{'abcdefghij' | slice:-4}} - 输出 'ghij'</p>
<p>{{'abcdefghij' | slice:-4:-2}} - 输出 'gh'</p>
<p>{{'abcdefghij' | slice:-100}} - 输出 'abcdefghij'</p>
<p>{{'abcdefghij' | slice:100}} - 输出 ''</p>
```

## TitleCasePipe - 标题管道

### 说明

将文本转换为标题大小写，将每个单词第一个字母大写，其余字母小写，以空白字符分隔的视为一个单词，如空格，制表符，换行符

### 语法
` value_expression | titlecase `

### 示例

```
<p>{{'some string' | titlecase}}</p> <!-- 输出 "Some String" --> 
<p>{{'tHIs is mIXeD CaSe' | titlecase}}</p> <!-- 输出 "This Is Mixed Case" --> 
<p>{{'it\\'s non-trivial question' | titlecase}}</p> <!-- 输出 "It's Non-trivial Question" --> 
<p>{{'one,two,three' | titlecase}}</p> <!-- 输出 "One,two,three" -->
<p>{{'true|false' | titlecase}}</p> <!-- 输出 "True|false" -->
<p>{{'foo-vs-bar' | titlecase}}</p> <!-- 输出 "Foo-vs-bar" -->
```

# 自定义管道

- 使用`ng g p hello`命令创建管道文件

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'hello',
  pure: true // 如果管道不受外界影响，只受参数的影响请遵守FP原则，设置为纯管道
})
export class HelloPipe implements PipeTransform {

  transform(value: string): string {
    if(!value) return value;
    if(typeof value !== 'string') {
      throw new Error('Invalid pipe argument for HelloPipe');
    }
    return "Hello " + value;
  }
}
```

-----------END-----------