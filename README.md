## good_morning_discord

一个适用 kokkorobot 的 自用早安晚安 插件, 改造自[AZMIAO](https://github.com/azmiao)的 早安晚安 插件

## 原项目地址：

https://github.com/azmiao/good_morning
原功能仿造自[BillYang2016](https://github.com/BillYang2016)的酷Q早安晚安插件

## 功能

```
== 命令 ==
[早安] 早安喵
[晚安] 晚安喵
[我的作息] 看看自己的作息
[群友作息] 看看今天几个人睡觉或起床了
[早安晚安配置] 查看超级管理员设置的配置

== 限超级管理员的设置 ==
[早安晚安初始化] 首次使用请初始化
= 配置(详情看文档) =
[早安开启 xx] 开启某个配置
[早安关闭 xx] 关闭某个配置
[早安设置 xx x] 设置数值
[晚安开启 xx] 开启某个配置
[晚安关闭 xx] 关闭某个配置
[晚安设置 xx x] 设置数值
```

## 简单食用教程：

1. 在 kokkoroBot\kokkoro\config\ `__bot__.py` 文件的 MODULES_ON 加入 'good_morning'

    然后重启 kokkoroBot

2. 在群里发一句'早安晚安初始化'初始化一下


## 功能配置

### 手动打开文件 `config.json` (如需命令修改，请看再下面的详细说明)

=== `config.json`可随时修改，修改完无需重启kokkoro即可生效 ===

```
{
    "morning": {
        "get_up_intime": {      //是否只能在规定时间起床床
            "enable": true,     //默认开启，若关闭则下面两项无效
            "early_time": 1,    //允许的最早的起床时间
            "late_time": 18     //允许的最晚的起床时间
        },
        "multi_get_up": {       //是否允许多次起床
            "enable": false,    //默认不允许，若开启则下面一项无效
            "interval": 6       //两次起床间隔的时间，小于这个时间就不允许起床
        },
        "super_get_up": {       //是否允许超级亢奋
            "enable": false,    //默认不允许，若开启则下面一项无效
            "interval": 3       //这次起床和上一次睡觉的时间间隔，小于这个时间就不允许起床，不怕猝死？给我睡！
        }
    },
    "night": {
        "sleep_intime": {       //是否只能在规定时间睡觉觉
            "enable": true,     //默认开启，若关闭则下面两项无效
            "early_time": 18,   //允许的最早的睡觉时间，默认晚上18点
            "late_time": 6      //允许的最晚的睡觉时间，默认第二天早上6点
        },
        "multi_sleep": {        //是否允许多次睡觉
            "enable": false,    //默认不允许，若开启则下面一项无效
            "interval": 6       //两次睡觉间隔的时间，小于这个时间就不允许睡觉
        },
        "super_sleep": {        //是否允许超级睡眠
            "enable": false,    //默认不允许，若开启则下面一项无效
            "interval": 3       //这次睡觉和上一次起床的时间间隔，小于这个时间就不允许睡觉，睡个锤子，快起床！
        }
    }
}
```

### 超级管理员使用命令修改配置 (超详细的说明)

```
- 默认配置（如上）
    - 早安：
    是否要求规定时间内起床：否
    是否允许连续多次起床：是
    是否允许超级亢奋(即睡眠时长很短)：是
    - 晚安：
    是否要求规定时间内睡觉：否
    是否允许连续多次睡觉：是
    是否允许超级睡眠(即清醒时长很短)：是

- 早安部分
    [早安开启 xx] 开启某个配置选项，xx可选值目前有 [时限 | 多重起床 | 超级亢奋]
    [早安关闭 xx] 关闭某个配置选项，xx可选值目前有 [时限 | 多重起床 | 超级亢奋]
        ※ 时限：要求在规定的时间内起床，默认要求，即开启
           多重起床：允许在短时间内多次起床，默认不允许，即关闭
           超级亢奋：允许睡眠时间很短，默认不允许，即关闭
    [早安设置 xx x] 设置某个配置的参数，xx可选值目前有 [时限 | 多重起床 | 超级亢奋]，x可选值为0到24的整数
        ※ 当设置时限时需要两个参数，命令为：[早安设置 时限 x y]
           当不是时限时只需一个参数，命令为：[早安设置 xx x]

- 晚安部分 (类同早安)
    [晚安开启 xx] 开启某个配置选项，xx可选值目前有 [时限 | 多重睡觉 | 超级睡眠]
    [晚安关闭 xx] 关闭某个配置选项，xx可选值目前有 [时限 | 多重睡觉 | 超级睡眠]
        ※ 时限：要求在规定的时间内睡觉，默认要求，即开启
           多重睡觉：允许在短时间内多次睡觉，默认不允许，即关闭
           超级睡眠：允许清醒时间很短，默认不允许，即关闭
    [晚安设置 xx x] 设置某个配置的参数，xx可选值目前有 [时限 | 多重睡觉 | 超级睡眠]，x可选值为0到24的整数
        ※ 当设置时限时需要两个参数，命令为：[晚安设置 时限 x y]
           当不是时限时只需一个参数，命令为：[晚安设置 xx x]
```
