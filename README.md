# 【RunAnyCtrl】一劳永逸的规则启动控制器 v1.0 @2018.02.28

只要能设定足够灵活的规则，就可以在不同的场景和需求下智能启动不同的软件和应用，这是我开发这个软件的初衷😁

---

## 启动项 - 基本功能（主界面新建）

- 启动名：自由命名
- 启动路径：文件软件路径、网址等等
- 自动启动：随RunAnyCtrl启动而自动启动
- 自动关闭：随RunAnyCtrl关闭而自动关闭
- 隐藏启动：如果该软件支持，可以在后台隐藏启动
- 最多启动次数：RunAnyCtrl运行期间，该软件最多启动次数
- 不重复启动：先判断软件是否正在运行，不会重复启动（网址等无法判断，请用最多启动次数限制）

## 启动规则项（强大灵活）

+ 使用规则自动启动：使用规则的总开关，不勾选该运行项的规则均不生效
+ 与(全部匹配)：该启动项所有规则项都通过全部为真(true)时，规则才通过
+ 或(部分匹配)：该启动项只需要有一项规则为真(true)时，规则就通过
+ 规则循环最大次数：规则循环判断的最大次数（24为规则循环24次）
+ 规则循环间隔时间(毫秒)：规则循环每次判断中间间隔的时间，以毫秒为单位（1000为1秒、60000为1分、3600000为1小时）
+ 增加、修改、减少规则：
  + 规则名：默认添加了“网络连接、电脑名、时间点、星期几”4个规则，在规则管理中添加
  + 自定义条件：只判断规则真假，不用填写（多个参数每行为一个参数，最多支持10个），保存用|来分隔参数

## 规则ahk配置（主界面规则按钮）

* 增加、编辑、减少：
* 规则名：自由命名，中文更易理解
* 规则函数：可手动填写（需要与ahk中函数名一致），推荐使用右边选择框自动填写
* 规则路径：点击按钮，选择要引用的ahk规则脚本，右上方选择框会自动显示该脚本中的所有函数名，选择需要使用的函数
  * 规则ahk脚本中建议只添加函数，不要添加子程序和return，引入到RunAnyCtrl后会造成脚本运行中断，建议格式如下：
```AutoHotkey
/*
验证当前电脑名称 @hui-Zz
*/
rule_computer_name(name){
	return A_ComputerName=name ? true : false
}
```

