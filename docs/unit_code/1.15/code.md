

# 

# Page 1
<!-- tabs:start -->

## **[core]组**
!> 以下的代码为`通用代码`,多半是必要的代码，如果不包括这些，可能在`绝大多数情况下导致错误`。
### name
#### name-代码简介
?> 代码:name 中文释义:名字 类型:字符型 隶属于:通用代码组
#### name-要点指示

> [!NOTE] name代码的要点指示：  

<!-- chat:start -->
#### **JDSALing**
定义单位原始名称，可以是中文。<br>
游戏使用它区分其它单位。<br>
如果没有在[displayText或者语言文件设置显示名称]，<br>
那么它也将作为单位的显示名称。  <br>
具体描述文件位置(内部):    <br>
1.assets/translationsStrings_zh.properties <br>
格式:units.单位名称.name=写单位显示的名称   <br>
units.单位名称.description= [[填单位显示的描述]]   <br> 
#### **tobby3600**

ini文件的单独定义(外部-推荐):  <br>
2.displayText: 单位的标题  <br>
&nbsp;&nbsp;&nbsp;displayDescription: -单位的描述  <br>

<!-- chat:end -->

特别提醒:`displayText支持本地化`，例如如果要写一个`多语言的单位描述`，可以通过以下例子：

#### name-演示例子

```ini
演示例子
[core]
name: Ling
displayText: English Title Text
displayText_zh:中文标题

displayDescription: -English Description
displayDescription_zh:-中文描述

```

### price
#### price-代码简介
?> 代码:price 中文释义:价格 类型:整数 隶属于:通用代码组
#### price-要点指示
!> price代码要点指示:
定义单位的价格，显示在单位信息中，建造时也以此价格为准。
<!-- chat:start -->
#### **tobby3600**
默认情况下，price只需要填写一个整数，此时使用的是游戏内自带的资金credit；
想要更改资源类型，可以使用 `price:资源1=数值1,资源2=数值2,...` 的格式（前提是此资源要在使用的单位进行定义）。
<!-- chat:end -->

#### price-演示例子
```ini
[core]
price:120,石油=80,铁=60
```

### radius
#### radius-代码简介
?> 代码:radius 中文释义:半径 类型:整数 隶属于:通用代码组
#### radius-要点指示
!> radius代码要点指示:
半径定义单位的`实际碰撞体积和显示范围`，在未设置`选择框大小`时，半径决定是单位选择框的大小。
半径的单位是像素(px)。
#### radius-演示例子
```ini
[core]
radius:20
```

### mass
#### mass-代码简介
?> 代码:mass 中文释义:质量 类型:整数 隶属于:通用代码组
#### mass-要点指示
!> mass代码要点指示:
质量决定单位在各种碰撞时的效果。`质量越大，其他单位越难推动`。
#### mass-演示例子
```ini
[core]
mass:2000
```

### maxHp
#### maxHp-代码简介
?> 代码:maxHp 中文释义:最大生命值 类型:整数 隶属于:通用代码组
#### maxHp-要点指示
!> maxHp代码要点指示:

<!-- chat:start -->
#### **tobby3600**
最大生命值定义单位在不修改它时最多能够有多少血量，单位默认生成时即是这个血量。<br>
maxHp可以通过<font color=orange>单位参考.maxHp()</font>来获取，也可以通过<font color=orange>[action]setUnitStatus</font>进行修改。

<!-- chat:end -->

#### maxHp-演示例子
```ini
[core]
maxHp:600
```

### altNames
#### altNames-代码简介
?> 代码:altNames 中文释义:别名 类型:字符型 隶属于:通用代码组
#### altNames-要点指示

!> altNames代码要点指示:
<!-- chat:start -->
#### **JDSALing**
主要在<font color=orange>启用多个自定义Mod</font>进行优先级定义<br>
以逗号分隔的名称列表。像<font color=orange>名称一样，但优先级较低</font>，对于<font color=orange>启用多个自定义mod</font>有用。
<!-- chat:end -->

#### altNames-演示例子:
```ini
[core]
altNames:ling,tobby3600,coldmint
```
### class
#### class-代码简介

?> 代码:class 中文释义:类 类型:字符型 隶属于:通用代码组

> [!ATTENTION] 无实际用处，可以删除。<br>
Luke：保留供将来使用，默认情况下必须为CustomUnitMetadata。由于该代码无实际用途，可以忽略该代码<br>
该代码后面什么都可以输，但没有实际用途。或许在未来会有用。

#### class-演示例子:
```ini
[core]
class:CustomUnitMetadata
```

### strictLevel
#### strictLevel-代码简介

?> 代码:strictLevel 中文释义:严格级别 类型:数字固定型 隶属于:通用代码组

> [!TIP] 建议添加到"all-units.template"以应用于所有单位,进行统一查错。<br>
默认值为0，忽略代码重复。设为1时如果当前单位内有重复代码，则报错。

#### strictLevel-演示例子:
```all-units.template & ini
[core]
strictLevel:1
```

### techLevel
#### techLevel-代码简介:
?> 代码:techLevel 中文释义:科技等级 类型:数字固定型 隶属于:通用代码组

> [!TIP] 早期是用于在<font color=orange>builtFrom</font>的代码,并结合科技等级使用。如果工厂的等级低于单位的目标科技等级，则会在工厂里面隐藏该单位。<br>自铁锈1.09后出现<font color=orange>overrideAndReplace</font>后，该方法则不建议使用。有关于新策略，请参考<font color=orange>overrideAndReplace</font>代码文档指南。<br>
设置单位的科技等级，共有3个级别，1级GUI显示为绿色，2、3级显示为黄色。超过3报错。

#### techLevel-演示例子:
```ini
[core]
techLevel:2
```

### buildSpeed
#### buildSpeed-代码简介

?> 代码:buildSpeed 中文释义:建造速度 类型:浮点/秒型 隶属于:通用代码组

> [!TIP] 建造此单位需要的时间，填秒。<br>
以前的计算方式为：此处所填时间=1÷(60x你需要的秒)如果定义了工厂速率则需要乘以建造乘数。

#### buildSpeed-演示例子:
```ini
[core]
buildSpeed:30s
#或者：
## 下方可能有误差
buildSpeed:0.0006
```

### isBio
#### isBio-代码简介


?> 代码:isBio 中文释义:是生物 类型:布尔型 隶属于:通用代码组

> [!TIP] 若设置成true,则会在单位死亡时产生血迹,  
图像在drawable/blood_mark.png，hideScorchMark：true时可以隐藏）非生物则为黑色爆炸效果。
#### isBio-演示例子:
```ini
[core]
isBio:true
```

### isBug
#### isBug-代码简介

?> 代码:isBug 中文释义:是虫子 类型:布尔型 隶属于:通用代码组

> [!TIP] 若设置成true,则会认定为虫子，用于沙盒中的单独分类。
#### isBio-演示例子:
```ini
[core]
isBug:true
```

### isBuilder
#### isBuilder-代码简介

?> 代码:isBuilder 中文释义:是建造者 类型:布尔型 隶属于:通用代码组

> [!TIP] 若设置成true,则会需要此单位建造建筑物，则通常需要此代码。
并且默认设为[ai] useAsBuilder。
#### isBuilder-演示例子:
```ini
[core]
isBuilder:true
```

### streamingCost
#### streamingCost-代码简介

?> 代码:streamingCost 中文释义:流式资金 类型:整数型 隶属于:通用代码组

> [!TIP] 和价格一样，但在建造时逐渐消耗资金，如果在构建过程中资源耗尽，  
建造或生产队列将暂停。就像是红警中那样。铁锈默认是预先扣除资金。  
若使用该代码，则玩家的每秒资金将会根据流式资金的算法进行扣减。
#### streamingCost-演示例子:
```ini
[core]
streamingCost:1145
```

### switchPriceWithStreamingCost

#### switchPriceWithStreamingCost-代码简介

?> 代码:switchPriceWithStreamingCost 中文释义:流式资金模式全局切换 类型:布尔型 隶属于:通用代码组

> [!TIP] 快捷设置为默认资金消耗方式或为流式建造方式。
建议使用模板快速将一个模组为所有单位切换流资源。
例如all-units.template.
#### switchPriceWithStreamingCost-演示例子:
```ini,all-units.template
[core]
switchPriceWithStreamingCost:true
```

!> 以下的代码为`单位统计代码组`,非必须存在的代码，请根据情况自行使用

### selfRegenRate
#### selfRegenRate-代码简介

?> 代码:selfRegenRate 中文释义:生命恢复速度 类型:浮点型 隶属于:单位统计代码组

> [!TIP] 此数值决定每帧增加血量。游戏内默认速度下，一秒为60逻辑帧，而你看到的FPS帧数为渲染帧，所以电脑上几百帧和手机上60帧和省电模式下30帧并不影响计算。所以不要写太大。可以写负值用于自毁。
#### selfRegenRate-演示例子:
```ini
[core]
maxHp:500
selfRegenRate:0.5
```

### maxShield
#### maxShield-代码简介

?> 代码:maxShield 中文释义:护盾值 类型:整型 隶属于:单位统计代码组

> [!TIP] 单位最大护盾值，默认生成时即为此值。如果设置了startShieldAtZero:true，则初始为0.
#### maxShield-演示例子:
```ini
[core]
maxShield:3000
```

### startShieldAtZero
#### startShieldAtZero-代码简介

?> 代码:startShieldAtZero 中文释义:护盾初始值为0 类型:布尔型 隶属于:单位统计代码组

> [!TIP] 如果为true，则单位护盾值从0开始增加。
#### startShieldAtZero-演示例子:
```ini
[core]
maxShield:3000
startShieldAtZero:true
```

### shieldRegen
#### shieldRegen-代码简介

?> 代码:shieldRegen 中文释义:护盾恢复速度 类型:浮点型 隶属于:单位统计代码组

> [!TIP] 此数值决定每帧增加护盾值，游戏内一秒为60帧，所以不要写太大。可以写负值。
#### shieldRegen-演示例子:
```ini
[core]
maxShield:3000
shieldRegen:0.5
```

### energyMax
#### energyMax-代码简介

?> 代码:energyMax 中文释义:能量值 类型:浮点型 隶属于:单位统计代码组

> [!TIP] 默认值为0。可以用作炮塔，激光防御和行动的弹药的能量。
#### energyMax-演示例子:
```ini
[core]
energyMax:5
```

### energyRegen
#### energyRegen-代码简介

?> 代码:energyRegen 中文释义:能量恢复速度 类型:浮点型 隶属于:单位统计代码组

> [!TIP] 能量每帧恢复速度，游戏内一秒为60帧，所以不要写太大。可以写负值。
#### energyRegen-演示例子:
```ini
[core]
energyRegen:0.4
```

### energyRegenWhenRecharging

#### energyRegenWhenRecharging-代码简介

?> 代码:energyRegenWhenRecharging
 中文释义:充能时能量恢复速度 类型:浮点型 隶属于:单位统计代码组

> [!TIP] 能量恢复是持续的，如果你设置了energyNeedsToRechargeToFull，那么攻击时按energyRegen恢复，耗尽时的灰条按此处设定值恢复。
#### energyRegenWhenRecharging-演示例子:
```ini
[core]
energyMax:1
energyRegenWhenRecharging:0.4
```

### energyNeedsToRechargeToFull

#### energyNeedsToRechargeToFull-代码简介

?> 代码:energyNeedsToRechargeToFull
 中文释义:能量需要充满 类型:布尔型 隶属于:单位统计代码组

> [!TIP] 如果能量耗尽，则需要完全充能才能进行攻击。
#### energyRegenWhenRecharging-演示例子:
```ini
[core]
energyMax:4
energyNeedsToRechargeToFull:true
```

### armour
#### armour-代码简介

?> 代码:armour
 中文释义:装甲 类型:整型 隶属于:单位统计代码组

> [!TIP] 抵消敌方攻击所造成的伤害。
#### armour-演示例子:
```ini
[core]
armour:40
#如果受到40以上的常规攻击，则进行抵消，反之返回1伤害点。
#例如45伤害，40护甲，那么将获得5点伤害。
```

### armourMinDamageToKeep
#### armourMinDamageToKeep-代码简介

?> 代码:armour
 中文释义:装甲最低伤害 类型:整型 隶属于:单位统计代码组

> [!TIP] 至少造成多少点伤害，默认为1.防止护甲太高完全打不动。
#### armourMinDamageToKeep-演示例子:
```ini
[core]
armour:40
armourMinDamageToKeep:2
#如果受到40以下的常规攻击，则进行最低伤害判定
```

### borrowResourcesWhileAlive
#### borrowResourcesWhileAlive-代码简介

?> 代码:armour
 中文释义:资源活着时借用 类型:Price型 隶属于:单位统计代码组

> [!TIP] 创建时获取这些资源，删除或销毁时将其返回。例如用于电力逻辑，负数供电和正数耗电。
#### borrowResourcesWhileAlive-演示例子:
```ini
[core]
borrowResourcesWhileAlive:5000
#单位活着的时候给予5000金币，死亡扣除5000金币
#一个小型贷款系统，
```

<!-- tabs:start -->

<!-- 换行两个空格 或者 <br> -->
#### **动动脑考考你**
如果这里要通过这个代码做一个小的贷款系统，并经过一段时间让单位死亡。  
只需要4行代码即可实现，试试看。

提示：dieOnZeroEnergy:true---(无能量时死亡|如果能量值为零，该单位死亡)
#### **显示答案-#1**
```txt
#参考答案为：
[core]
borrowResourcesWhileAlive:5000
energyMax:1
energyRegen:-0.4
dieOnZeroEnergy:true
#原理是通过能量为0单位死亡并通过这个代码还钱，
是很简陋的贷款思路，当然，在后续会有更加高级的思路。
```

<!-- tabs:end -->


## **[canBuild_Name]组**



## **[canBuild_Name]组**

## **[graphics]组**

### image
#### image-代码简介
?> 代码:image 中文释义:主体图像 类型:文件(图像文件) 隶属于:通用代码组
#### image-要点指示
!> image代码要点指示:
<!-- chat:start -->
#### **tobby3600**
主体图像定义单位的图像。<br>
在不进行额外修改的情况下，主体图像会显示在<font color=orange>单位</font>、<font color=orange>单位列表</font>、<font color=orange>单位信息</font>处。
#### **JDSALing**
填写的值可以包含路径，若只包含文件名，则会在和当前ini相同文件夹内寻找图片文件。<br>
可以通过<font color=orange>`ROOT:路径\文件`</font>的形式来访问在模组目录下的任何文件。
#### **tobby3600**
上述方法还可以在路径中添加`..`来访问外部文件
<!-- chat:end -->

#### image-演示例子
```ini
[graphics]
image:main.png
```

### image_wreak
#### image_wreak-代码简介
?> 代码:image_wreak 中文释义:死亡图像 类型:文件(图像文件) 隶属于:通用代码组
#### image_wreak-要点指示
!> image_wreak代码要点指示:
<!-- chat:start -->
#### **tobby3600**
死亡图像定义单位死亡后产生的图像。<br>
文件定义方式与image相同。
#### **JDSALing**
填写`NONE`可以让单位死亡后不产生死亡图像。
<!-- chat:end -->

#### image_wreak-演示例子
```ini
[graphics]
image_wreak:dead.png
或者
image_wreak:NONE
```

### imageScale
#### imageScale-代码简介
?> 代码:imageScale 中文释义:图像缩放比例 类型:文件(图像文件) 隶属于:通用代码组
#### imageScale-要点指示
!> imageScale代码要点指示:
<!-- chat:start -->
#### **tobby3600**
填写后，铁锈会将图像大小乘以缩放比例。<br>
默认值为1。
<!-- chat:end -->

#### imageScale-演示例子
```ini
[graphics]
imageScale:1.2
```

## **折叠第1页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->


# Page 2
<!-- tabs:start -->
# **[attack]组**

# **[turret_Name]组**

# **[projectile_Name]组**
## **折叠第2页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->
# Page 3
<!-- tabs:start -->
# **[movement]组**

# **[ai]组**

# **[leg_#]/[arm_#]集合组**
## **折叠第3页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->
# Page 4
<!-- tabs:start -->
# **[attachment_Name]组**

# **[effect_Name]组**

# **[animation_Name]组**
## **折叠第4页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->
# Page 5
<!-- tabs:start -->
# **[action_Name]/[hiddenAction_Name]集合组**

# **[spawn unit] 刷兵序列组**

# **[placementRule_Name] 放置规则组**
## **折叠第5页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->
# Page 6
<!-- tabs:start -->
# **[LogicBoolean] 逻辑序列组**
> [!ATTENTION] 由于这个组的特殊性，格式不标准，请勿参考这个组的写法。

### 前置知识

#### 布尔值
<font color=orange>布尔值</font>表达“真(true)”或“假(false)”的一个状态。在铁锈中，布尔值(`boolean`)被运用于逻辑判断。

#### 数据类型
数据类型指数据的种类，在铁锈中，不同的数据有不同的类型，不同的数据类型之间通常不能直接进行运算。

|常见数据类型英文 |存储的值类型 |
| -------- | ------------ |
| string   | 字符串       |
| number   | 整数         |
| float    | 浮点数(小数) |
| boolean  | 布尔值       |
| unit     | 单位         |
<!-- MarkDown表格必须有上方的分割线以告诉浏览器是表格 -->

#### 算数优先级
与数学中计算符一样，铁锈中算数运算符有优先级区别。`%`和`*`和`/`的优先级大于`+`和`-`。

### 比较运算符

#### 如果
?> 代码:if 中文释义:如果
`if`是大部分逻辑运算的开头(select等不需要if)，用于在支持逻辑的键引入逻辑判断。

<!-- 若要连续嵌套，请直接使用Html原生代码 -->
<div class="alert callout tip">
<p>演示例子:</p>
</div>

```ini
[action]
autoTrigger:if self.maxHp() > memory.emx_hp
```

#### 小于
?> 代码:< 中文释义:小于<br>
小于用于在逻辑布尔值中比较两个数的大小，格式为`数据a < 数据b`，若`a<b`则整个式子的值为`true`，否则为`false`。

<!-- 自定义的提示框请使用原生Html进行套入 -->
<div class="alert callout note">
  <p class="title">
  <span class="icon icon-note"></span>要点指示:</p>
</div>


```ini
[action]
autoTrigger:if memory.a < memory.b
```

#### 大于
?> 代码:> 中文释义:大于<br>
同上，格式为`数据a > 数据b`，若`a>b`则整个式子的值为`true`，否则为`false`。

#### 小于等于
?> 代码:<= 中文释义:小于等于<br>
同上，若`a<=b`则整个式子的值为`true`，否则为`false`。

#### 大于等于
?> 代码:>= 中文释义:大于等于<br>
同上，若`a>=b`则整个式子的值为`true`，否则为`false`。

#### 等于
?> 代码:== 中文释义:等于<br>
> [!TIP] 请注意，铁锈中等于的符号为<font color=orange>==</font>，<font color=orange>=</font>在铁锈中用于赋值或参数。
> 
同上，若`a=b`则整个式子的值为`true`，否则为`false`。

#### 不等于
?> 代码:!= 中文释义:不等于<br>
同上，若`a!=b`则整个式子的值为`true`，否则为`false`。

### 逻辑运算符

#### 且
?> 代码:and 中文释义:且<br>
> [!TIP] <font color=orange>and</font>用于连接两个逻辑判断，只有在这两个逻辑判断的值都为<font color=orange>true</font>时，<font color=orange>and</font>的值才为true。
<br>

<!-- 自定义的提示框请使用原生Html进行套入 -->
<div class="alert callout note">
  <p class="title">
  <span class="icon icon-note"></span>要点指示:</p>
</div>
<!-- 并保证首尾留有一行换行以便Markdown正确解析 -->

```ini
[action]
autoTrigger:if memory.a < memory.b and memory.a > memory.c
# 在这个例子中，只有a小于b且a大于c时，自动触发才会被触发
```

#### 或
?> 代码:or 中文释义:或<br>
> [!TIP] <font color=orange>or</font>用于连接两个逻辑判断，只要这两个逻辑判断的值有一个为<font color=orange>true</font>时，<font color=orange>or</font>的值就为true。

#### 非
?> 代码:not 中文释义:非<br>
> [!TIP] <font color=orange>not</font>用于将某个逻辑判断的值取反，即`true`变`false`，`false`变`true`。

> [!NOTE] 多个逻辑运算符同时使用时，优先级为`not>and>or`，同时<font color=orange>支持使用括号改变运算优先级</font>。
<br>推荐<font color=orange>在不确定优先级时打括号</font>。

<div class="alert callout tip">
<p>演示例子:</p>
</div>

```ini
[action]
autoTrigger:if (memory.a < memory.b or memory.a > memory.c) and not memory.a < memory.d
```

<!-- tabs:start -->
<!-- 换行两个空格 或者 <br> -->
#### **动动脑考考你**
#### 考考你，在上述这个例子中，满足什么条件才会触发？
#### **显示答案-#2**
#### 答案：a必须满足小于b和大于c中的一个，且a必须小于c，自动触发才会被触发。
<!-- tabs:end -->



### 算数运算符

#### 加
?> 代码:+ 中文释义:加<br>

加用于将两个逻辑值相加，得到结果，格式为`数据a + 数据b`。

> [!NOTE] 不同数据类型通常<font color=orange>不能直接进行算数运算</font>，但在部分情况下，<font color=orange>number</font>和<font color=orange>float</font>类型可以混用（建议<font color=orange>所有数值全部使用float</font>来避免混淆）。

<div class="alert callout tip">
<p>演示例子:</p>
</div>

```ini
[action]
autoTrigger:if (memory.a + memory.c) < memory.b
```

#### 减
?> 代码:- 中文释义:减<br>

减用于将两个逻辑值相减，得到结果，格式为`数据a - 数据b`。

> [!NOTE] 对于<font color=orange>不满足交换律的运算符</font>，需要注意<font color=orange>运算优先级</font>是否正确。由于铁锈本身bug，<font color=orange>在数学上正确的优先级不一定在铁锈中正确</font>，因此可能出现减法顺序混乱等问题。
<br>为了避免可能的问题，请尽量在任何<font color=orange>不满足交换律的运算符</font>两边打上括号。

#### 乘
?> 代码:* 中文释义:乘<br>

乘用于将两个逻辑值相乘，得到结果，格式为`数据a * 数据b`。

#### 除
?> 代码:/ 中文释义:除<br>

除用于将两个逻辑值相除，得到结果，格式为`数据a / 数据b`。

#### 求余
?> 代码:% 中文释义:求余(取模)<br>

求余用于获取两个逻辑值中，第一个除第二个的余数，格式为`数据a % 数据b`。
例如`7%3=1(7除3余1)`

### 单位统计

#### 通用统计关键字
单位统计中部分通用的关键字：
1. `greaterThan` 大于
2. `lessThan` 小于
3. `empty` 空
4. `full` 满
5. `equalTo` 等于

#### 内置参数
单位统计中部分内置参数返回代码（由于过于简单不单独列出）：
1. `self.hp()` 生命值
2. `self.maxHp()` 最大生命值
3. `self.energy()` 能量
4. `self.shield()` 护盾
5. `self.kills()` 击杀数
6. `self.maxEnergy()` 最大能量
7. `self.maxShield()` 最大护盾
8. `self.height()/self.x()` 高度
9. `self.ammo()` 弹药
10. `self.isAmmoEmpty()` 弹药为空(快捷方式:`self.ammo(empty=true)`)
11. `self.ammoIncludingQueued()` 包括队列中的弹药
12. `self.energyIncludingQueued()` 包括队列中的能量
13. `self.isEnergyFull()` 能量满(快捷方式:`self.energy(full=true)`)
14. `self.isEnergyEmpty()` 能量空(快捷方式:`self.energy(empty=true)`)
15. `self.isEnergyRecharing()` 能量充能中
16. `self.playerName()` 玩家名称
17. `self.teamName()` 队伍名称
18. `self.x(),self.y()` x,y坐标
19. `self.dir()` 方向
20. `self.priceCredits()` 金钱价格
21. `self.speed()` 当前速度
22. `self.maxMoveSpeed()` 最大速度
23. `self.id()` 单位id(每个单位的序号)
24. `self.builtAmount()` 建造数量
25. `self.complate()` 自身建造完成
26. `self.teamDefeatedTech()` 队伍失败
27. `self.teamWipedOut()` 队伍全部死亡
28. `self.teamVictory()` 队伍获胜
29. `self.queueSize()` 自身队列大小

#### self.hasResources()
?> 代码:self.hasResources() 中文释义:有资源 返回类型:boolean<br>

`self.hasResources()` 用于检测自身某资源是否大于等于某数值，格式为`self.hasResources(资源名=数值)`

<div class="alert callout tip">
<p>演示例子:</p>
</div>

```ini
self.hasResources(hp=10,energy=5) 
```

#### self.resource()
?> 代码:self.resource() 中文释义:资源 返回类型:float<br>

与`self.hasResources()`不同，`self.resource()`直接返回某个资源的数值。格式为`self.resource(type="资源名")`。

> [!NOTE] 引用资源时，请确保<font color=orange>这个资源在这个单位定义过</font>，否则会报错。

#### self.resource.RESOURCE_TYPE
?> 代码:self.resource.RESOURCE_TYPE 中文释义:资源 返回类型:float<br>

`self.resource.RESOURCE_TYPE`是`self.resource()`的快捷方式。格式为`self.resource.资源名称`，引用更加方便。

#### self.isResourceLargerThan()
?> 代码:self.isResourceLargerThan() 中文释义:资源是否大于 返回类型:boolean<br>

> [!ATTENTION] 此代码为老旧解决方案，不推荐使用。

`self.isResourceLargerThan()`用于比较两种资源的大小。格式为`self.isResourceLargerThan(source=资源A,compareTarget=资源B,byMoreThan=大于资源B数量,multiplyTargetBy=资源B倍数)`

#### self.numberOfQueuedWaypoints()
?> 代码:self.numberOfQueuedWaypoints() 中文释义:队列中路径点数量 返回类型:float<br>

`self.numberOfQueuedWaypoints()`用于返回队列中路径点的数量。格式为`self.numberOfQueuedWaypoints(type="路径点类型")`。

### 单位计时

#### self.hasTakenDemage()
?> 代码:self.hasTakenDemage() 中文释义:受到伤害 返回类型:bool<br>

> [!NOTE] 单位计时部分能返回到最小时间精度为<font color=orange>0.1秒</font>。

`self.hasTakenDemage()`用于获取指定时间内是否收到伤害。使用`self.hasTakenDemage(withInSecounds=多少秒内,laterThanSecounds=多少秒后)`格式时，返回bool类型。

#### self.timeAlive()
?> 代码:self.timeAlive() 中文释义:存活时间 返回类型:float/bool<br>

`self.timeAlive()`用于获取单位存活时间。使用`self.timeAlive(withInSecounds=多少秒内,laterThanSecounds=多少秒后)`格式时，返回bool类型（是否符合此范围）；使用`self.timeAlive()`格式时，返回float类型。（更推荐使用后者）

#### self.lastConverted()
?> 代码:self.lastConverted() 中文释义:最后转换时间 返回类型:float/bool<br>

`self.timeAlive()`用于获取单位上次转换后的时间。使用`self.lastConverted(withInSecounds=多少秒内,laterThanSecounds=多少秒后)`格式时，返回bool类型（是否符合此范围）；使用`self.lastConverted()`格式时，返回float类型。

#### self.customTimer()
?> 代码:self.customTimer() 中文释义:自定义计时器 返回类型:float/bool<br>

`self.timeAlive()`用于获取自定义计时器的时间。使用`self.customTimer(withInSecounds=多少秒内,laterThanSecounds=多少秒后)`格式时，返回bool类型（是否符合此范围）；使用`self.customTimer()`格式时，返回float类型。


# **[Prices/Resources] 价格/资源序列组**

# **[global_resource_Name] 全局资源组**
## **折叠第6页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->
# Page 7
<!-- tabs:start -->

# **[resource_Name] 局部资源组**

# **[template_Name] 模板组**

# **[comment_Name] 注解组**

## **折叠第7页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->

# Page 8
<!-- tabs:start -->

# **[decal_Name] 贴花组**

# **[Dex-Code] 源码Dex扩展组**

# **[hidden-code] 隐藏代码扩展组**

## **折叠第8页**
该页已被折叠，点击其他选项卡可以再次展开。
<!-- tabs:end -->