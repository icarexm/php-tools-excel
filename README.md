使用`Composer`安装`icarexm`的excel处理类库：

~~~
composer require icarexm/excel:dev-master

~~~
## 从数据库中导出excel数据
> 在导出数据前，请自己准备好数据，本文以写死数据作为示例，实际导出时需要通过数据库查询

我们在控制器中添加如下代码：
~~~
//需要导出的数据
$data = [
    ['nickname' => 'MrYe', 'age' => 18],
    ['nickname' => 'MrYe2', 'age' => 19],
    ['nickname' => 'MrYe3', 'age' => 20],
];
//和数据字段对应，在导出的表头中我们可以看到自定义的名称
$fields = [
    'nickname'  => '用户昵称',
    'age'       => '用户年龄',
];
//执行导出
$excelTool = new icarexm\excel\Excel();
$excelTool->export($data, $fields);

~~~
实际效果：

![](https://img.kancloud.cn/88/68/88686a987a56c608375558d09dd39085_393x201.png)

## 导出多个sheet
控制器中添加如下代码：
~~~
//需要导出的数据
$data = [
    [
        ['nickname' => 'MrYe', 'age' => 18],
        ['nickname' => 'MrYe2', 'age' => 19],
        ['nickname' => 'MrYe3', 'age' => 20],
    ],

    [
        ['nickname' => 'xin', 'sex' => '女'],
        ['nickname' => 'xin2', 'sex' => '女'],
        ['nickname' => 'xin3', 'sex' => '女'],
    ]
];
//和数据字段对应，在导出的表头中我们可以看到自定义的名称
$fields = [
        [
            'nickname'  => '用户昵称',
            'age'       => '用户年龄',
        ],
        [
            'nickname'  => '用户昵称',
            'sex'       => '用户性别',
        ],
];

$excelTool = new icarexm\excel\Excel();
$excelTool->export($data, $fields);

~~~
**sheet1：**

![](https://img.kancloud.cn/98/30/98305836c1ef7bdcb8a2efce9c86e773_531x184.png)
**sheet2：**

![](https://img.kancloud.cn/5c/91/5c910a1edb76723728fa4e8351515159_541x234.png)

## 读取excel数据
我们在控制器中添加如下代码：
~~~
//读取的excel文件地址
$path = '数据.xlsx';
//读取数据
$excelTool = new icarexm\excel\Excel();
$excelTool->read($path, 'all', true);

~~~
` $data`就是读取后的数据
