---
title: AngularJs+Bootstrap Table $compile动态生成html
date: 2017-11-12 09:40:36
tags: [AngularJs,BootStrap]
description: '>>>整理最近AngularJs动态文档编译遇到问题的解决方案...'
---
# AngularJs+Bootstrap Table $compile动态生成html

关于angular+bootstrap table 使用的一些问题
- **①table中动态添加元素并绑定事件，js事件（eg:'ng-click...'）未被监听**
- **②使用jQuery方式绑定事件，造成数据动态绑定响应延时**

-------------------

关于ng-click未响应问题，由于事件监听在静态HTML页面生成时已经完成，因此对动态生成的元素绑定事件并实现监听，需要通过angularJs中的**compile**服务将动态添加的元素进行编译。
**bootstraptable相关参数设置  ([参考文档(中)](http://blog.csdn.net/rickiyeat/article/details/56483577)|[参考文档(英)](http://bootstrap-table.wenzhixin.net.cn/documentation/))**
```
angular.module("myApp",[]).controller('demoController',['$scope','$compile',
  function($scope,$compile){
    $scope.options=new Array();
    $scope.events=new Array();
    $("#myTable").bootstrapTable({//参数设置参考上文文档
      url:'demo.json',
      method:'get',
      pagination:true,
      pageNumber:1,
      pageSize:5,
      pageList:[5,10,15,20],
      queryParams:function queryParams(params){
        var param = {
          "pageNo": params.offset / params.limit + 1,
          "pageSize": params.limit
        };
      },
      columns:[
        {
          field:"id",
          title:"序号"
        },{
          field:"name",
          title:"名称"
        }, {
          field:"email",
          title:"邮箱"
        }, {
          field:"age",
          title:"年龄"
        },{
          field:"status",
          title:"状态"
        },{
          title:"操作",
          formatter:function(value,row,index){
            var rtn="<div id='option_"+row.id+"'></div>";//在格式化操作栏的过程中添加一个id唯一的空div，供后续编译使用
            //event可依据当前记录创建不同的元素内容
            var event=
              "<a class='btn btn-xs green' title='编辑' ng-click='$scope.edit('+row.id+')'>"+
              "<span class='glyphicon glyphicon-pencil'></span></a>"+
              "<a class='btn btn-xs green' title='删除' ng-click='$scope.edit('+row.id+')'>"+
              "<span class='glyphicon glyphicon-trash'></span></a>";
            $scope.options.push("option_"+row.id);//将id push至options数组
            $scope.events.push(event);//将待创建的htmlpush到events数组
            return rtn;
          }
        }
      ],
      onLoadSuccess:function(){//调用bootstrap加载完成方法
        for(var i=0;i<$scope.options.length;i++){//通过循环所创建的数据，将元素逐个进行compile
          var _option=$scope.options[i];
          var _event=$scope.events[i];
          var $el=$(_event).appendTo("#"+_option);
          $compile($el)($scope);//compile完成后，页面即可响应ng事件
        }
      }
    })
  }]
);
```

---------
实现效果：
![这里写图片描述](http://img.blog.csdn.net/20171128175231761?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzMyMTM2ODM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
