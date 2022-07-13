# zTreeSelectM

#### 项目介绍

项目中需要用到下拉树多选功能，找到两个相关组件moretop-layui-select-ext和wujiawei0926-treeselect，但是moretop-layui-select-ext不支持树结构，wujiawei0926-treeselect不支持多选，于是干脆仿照moretop-layui-select-ext动手写了一个组件，选择zTree而没有选择layuiTree的主要原因是layuiTree暂不支持父子关系取消。

#### 渲染代码
```
var _zTreeSelectM = zTreeSelectM({
    elem: '#zTreeSelectM',//元素容器【必填】          
    data: './json/1.json',//候选数据【必填】
    width: 600,  //设置了长度    
    selected: [3,6,29],//默认值            
    max: 3,//最多选中个数，默认5            
    name: 'field',//input的name 不设置与选择器相同(去#.)
    delimiter: ',',//值的分隔符           
    field: { idName: 'id', titleName: 'name' },//候选项数据的键名 
    zTreeSetting: { //zTree设置
        check: {
            enable: true,
            chkboxType: { "Y": "", "N": "" }
        },
        data: {
            simpleData: {
                enable: false
            },
            key: {
                name: 'name',
                children: 'children'
            }
        }
    }
});	
```

#### 获取选中数据代码
```
form.on('submit(demo)',function(data){			 
	console.log('zTreeSelectM 当前选中的值名：',_zTreeSelectM.selected);
	console.log('zTreeSelectM 当前选中的值：',_zTreeSelectM.values);
	console.log('zTreeSelectM 当前选中的名：',_zTreeSelectM.names);      
  
  	var formData = data.field;
  	console.log('表单对象：',formData);
  	return false;
})
	
//监听重置按钮
$('form').find(':reset').click(function(){
	$('form')[0].reset();
	_zTreeSelectM.set();//默认值
	return false;
});

$("#set").on('click',function(e){			 
	_zTreeSelectM.set([4,7,13]);
	return false;
})
```


#### 效果图
![效果](http://118.25.44.164/zTreeSelectM/img1.png "效果")

#### 码云演示
[码云演示](https://zyl0151_admin.gitee.io/ztreeselectm/ "码云演示") 
