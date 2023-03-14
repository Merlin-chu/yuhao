<!-- omit in toc -->
# 宇浩繁简通打输入法·CJK全汉字覆盖·三重拆分注解

朱宇浩 创作于 荷兰鹿特丹

官方QQ群: 735728797

- [1. 簡介](#1-簡介)
- [2. 规则介绍](#2-规则介绍)
  - [2.1. 字根编码](#21-字根编码)
  - [2.2. 单字编码规则](#22-单字编码规则)
  - [2.3. 简码字](#23-简码字)
  - [2.4. 词语编码](#24-词语编码)
  - [2.5. 拆字规则](#25-拆字规则)
- [3. RIME 方案](#3-rime-方案)
  - [3.1. Windows / Macos / 安卓安装方法](#31-windows--macos--安卓安装方法)
  - [3.2. 具体文件介绍](#32-具体文件介绍)
- [4. 方案特点](#4-方案特点)
  - [4.1. 提示快捷键](#41-提示快捷键)
  - [4.2. 单字拆分三重注解](#42-单字拆分三重注解)
  - [4.3. 增广常用字符集](#43-增广常用字符集)
  - [4.4. 一键切换字符集](#44-一键切换字符集)
  - [4.5. 使用 Z 键引导四叶草拼音输入和反查](#45-使用-z-键引导四叶草拼音输入和反查)
  - [4.6. 全码词语屏蔽](#46-全码词语屏蔽)

## 1. 簡介

「宇浩繁简通输入法」是由[朱宇浩](https://zhuyuhao.com)发明的形码输入法方案。具有以下特点：

- 面向大字集，全面覆盖CJK全字集98000多个汉字和部首。
- 常用繁简字通打混输。GB2312 + 国字常用字 + 大陆繁体字集下，静态重码率和动态选重率很低。同时，相似字形归并，达到打字派和检字派的平衡。
- 只使用25键，不使用Z键，手感好。Z鍵用於反查或其它自定義功能。
- 按顺序拆字，取一、二、三、未字根。
- 双编码，不分主副根，没有结构码。
- 全简一致，简码和词语编码取根同单字一致。
- 字根大码的排布按照键盘分区，字根小码使用拼音中的字母，便於上手。
- 基于**实用主义**原则，对相似字根进行合并，如「二」「冫」「飞右两点」不区分，「日」「曰」不区分。
- 最高频的汉字一简位于最容易按的键上：`E的`、`F一`、`V了`、`I没`。

[点击这里进入宇浩输入法在线拆分查询系统。](https://zhuyuhao.com/yuhao/chaifen)

这里对比一下五笔、郑码、徐码、虎码（都是我比较喜欢、有亮点的输入法）在不同汉字字符集下的单字全码的重码数量，以供参考。加粗的数字代表本行最优值。排名按发明时间顺序：

| 形码方案 | GB2312  | 国字    | 常用繁简 | GBK      | GB2312选重率 | 常用繁简选重率 |
| -------- | ------- | ------- | -------- | -------- | ------------ | -------------- |
| 五笔86   | 537     | 357     | 1741     | 6582     | 0.34%        | 2.74%          |
| 郑码     | 563     | 311     | 1809     | 6590     | 0.59%        | 2.92%          |
| 五笔98   | 515     | 329     | 1679     | 6368     | 0.38%        | 2.77%          |
| 徐码     | 318     | **127** | **488**  | **2902** | 0.11%        | 0.15%          |
| 虎码     | 532     | 238     | 2076     | 7687     | **0.05%**    | 4.00%          |
| 宇浩     | **309** | 216     | 614      | 4966     | **0.05%**    | **0.14%**      |

输入法有优点就有缺点，但我努力做到扬长避短。这里总结一下「宇浩输入法」对若干痛点的解决方法是：

- 宇浩输入法使用了和五笔一样的分键盘区域随机排布字根的方式。横区在键盘中排左侧，竖区在键盘中下排右侧，撇区在键盘上排左侧，捺区在键盘上排右侧，折区在键盘下排左侧。字根较为随机，这个考量是为了降重，同时不增加规则的复杂度。实际使用的时候，字根可以短时间内熟练，但规则的复杂度带来的痛苦是长久的。分区域分布，这是为了降低使用者上手的困难度。
- 宇浩输入法部分借鉴了徐码的首根小码后置（回头码）的特点，但徐码的副根字无论在任何情况下都要回头，这等同于在输入单字的时候一直判断取三根还是四根，容易出错。宇浩输入法只有在编码不足四码（双根字）的情况下才需要补上首根小码。
- 宇浩输入法使用了和五笔一样取一二三末根。而不是郑码和徐码那样，有时候取一、二、次末、末，有时候取一二末。这样选择，是因为倒数第二根的判断比较困难，打字的时候容易卡壳。

[点击此处详细了解我对一款具有平衡性的输入法的一些思考和分析，以及宇浩输入法的设计理念和基本考量。](discussion.md)

## 2. 规则介绍

这一章，我对宇浩输入法的基本规则进行简单介绍。如果你从未接触过形码输入法，可以从头开始一步一步学习。[点击此处阅读详细的《宇浩繁简通打输入法教程》。](learn.md)

### 2.1. 字根编码

「宇浩」使用双编码字根，即每一个字根对应两个字母。第一个字母叫做**大码**，第二个字母叫做**小码**。

字根大码，是按照字根第一笔的笔画来制定的。「宇浩」同五笔一样，字根按照笔画分区。

- ASDFGH 包含了首笔为「横」的字根，例如：`A寸` `F一`等。横区在键盘中排左侧。
- JKLNM 包含了首笔为「竖」的字根，例如：`J日` `K上`等。竖区在键盘中下排右侧。
- QWERTY 包含了首笔为「撇」的字根，例如：`P竹` `T人`等。撇区在键盘上排左侧。
- UIOP 包含了首笔为「捺」和「点」的字根，例如：`U言` `I立`等。捺区在键盘上排右侧。
- BVCX 包含了首笔为「折」的字根，例如：`B刀` `C巴`等。折区在键盘下排左侧。
- Z 键没有字根，可以用来反查拼音或做其他用途。

字根的小码，都是尽量从它汉语拼音包含的字母中随机选取。如果拼音中有`Z`或`X`，那么可以选`K`来代替。

字根表如下：

| 分區   | 大碼   | 代表字根v          | 字根                                                                                                                           |
|:-------|:-------|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------:|
| 橫     | A      | 扌(㐄キヰ)         | 寸 c  丁 d  𡗗 e  亍 i  丌 j  丅 k  七 q  耳 r  {于下} u  瓦 w  弋 y                                                           |
|        | S      | 艹(龷卌卅廾{冓上}) | 犬 a  臣 c  而 e  厂 h  馬({馬上}) m  辰 n  丂 o  二(⺀冫ㄑ) r  𠂇 u                                                           |
|        | D      | 石(丆)             | 歹 d  丰 f  古 g  十 h  未 i  走 k  來 l  尤(尢) o  其 q  豕(𧰨) s  不 u  戊 w  西(覀) x  雨(⻗) y                             |
|        | F      | 木(朩)             | 三 a  爾 e  一(㇀) i  工 o  甫 u                                                                                               |
|        | G      | 王(⺩)             | 大 d  革 e  匚({畏下}𠥓匸) f  戈 g  面 i  車({專上}) j  酉 o  夫 u                                                             |
|        | H      | 土(耂)             | 長(镸髟) a  车 e  干 g  士({穀頭}) h  世 i  至 k  龶 n  末 o  示(⺬) s  兀 w  牙 y                                             |
| 豎     | J      | 日(𫩏)             | 山 a  曰 e  田 i  黽({龜下}) m  早 o                                                                                           |
|        | K      | 虫                 | 甲 a  贝 b  电 d  申 e  水(氺) h  见 i  冂({雋下}) j  鹵 l  門 m  由 o  上(丄{丄、}) s  攴 u  禺 y                             |
|        | L      | 口({黽上})         | {亞下}({亞中}) a  非 i  㗊 j                                                                                                   |
|        | M      | 目                 | 小(𡭔⺌𣥂) a  齒 c  刂 d  骨(⾻) g  虎(虍{虍上}) h  貝 i  巾 j  見 k  皿 n  卜({龍右}⺊{乍下}) o  且({具上}) q  丨(⼁) s  罒 w |
|        | N      | 足(⻊𧾷)           | 冊(𠕁) c  鬥 d  黑 e  龰 h  止 i  〢({四竖}〣) s  尚 s  咼(冎) u  囗 w                                                         |
| 撇     | Q      | 竹({⺮右})         | 瓜 a  凡 f  殳 h  矢 i  几 j  僉 n  舟 o  丿(㇒) p  气 q  儿({荒下}) r  鱼 y                                                   |
|        | W      | 月(勹⺆{祭上}𱼀)   | 乂(𠂭) a  身 e  生 g  川 h  隹 i  牛(牜𠂒⺧) n  缶 o  千 q  鬼({卑上}) u  𧘇 y                                                 |
|        | E      | 亻                 | 白 b  长 g  夂(攵) h  斤(⺁) i  爪(⺥爫) k  壬(𡈼) n  夭 o  欠 q  烏({烏上}) u  乌 w                                           |
|        | R      | 金(釒)             | 彳 c  舌 e  風 f  向({向框}{囟框}) g  禾 h  {微上} i  匕(𠤎) i  臼 j  夕 k  毛 m  犭 n  鳥({鳥上}) o  饣 s  入 u               |
|        | T      | 片                 | 卯({卬左}{乐上}) a  八({介下}) b  人 e  彡({癶右}{两撇}) i  钅 j  自 k  用 o  手(龵) u  魚 y                                   |
|        | Y      | 心(忄)             | 鸟({鸟上}) a  合 e  {爲下} i  豸 i  𠂤 i  九 j  冖(𠂊⺈) m  食(飠) s                                                           |
| 捺     | U      | 言(訁)             | 丷(䒑ソ) a  羊(⺶) g  灬 i  礻 k  火 o  丬 q  广 u  亡({贏頭}) w                                                               |
|        | I      | 氵(ッ𠁼)           | 立 i  鹿({鹿上}) l                                                                                                             |
|        | O      | 宀                 | 讠 a  丶(⼂乀) d  方 g  户(戶) h  亥 i  之 k  亠 o  辛 x  〇(㇣) o                                                             |
|        | P      | 疒                 | 麻 a  文 e  高({高上}) g  亦 i  衤 k  米 m  门 n  辶(⻎⻍) o  穴 u                                                             |
| 折     | B      | 糸(糹)             | 刀 a  飛 e  子 i  己 j  母({互中}{母框}{毌框}) m  {鼠下} s  尸(𠃜⼫) s  又(コス龴癶ュ) u                                       |
|        | V      | 厶                 | 乃 a  了 e  弓 g  巛(巜) h  乙(𠄎乜𠃌㔾⺂⺄) i  艮 n  皮 p  纟({纟上}) s  已 y                                                 |
|        | C      | 女                 | 巴 a  也 e  阝 f  韋({五下}) i  幺 o  予 u                                                                                     |
|        | X      | 彐(⺕)             | 马 a  屮(丩凵丱) c  爿 g  乚(𡿨𠃋𠃑𠄌) i  卩 j  力 l  廴 n  矛 o  巳 s  羽(习) u                                               |

### 2.2. 单字编码规则

宇浩输入法的单字编码取一、二、三、末根。这同五笔输入法相同，和郑码、徐码不同。单字编码规则如下：

1. 依次取一、二、三、未根大码。
2. 不足四码时，补上未根小码。
3. 仍然不足四码时，补上首根小码（如果小码是v则不用补）。

### 2.3. 简码字

从A到Y排列，一级简码字分别是`过那也不的一大地没是上中小回就这我得在个着了然出`。

宇浩的字根设计，使得最高频的汉字分布在最容易按的键上，比如：「的」在`E`上，「一」在`F`上，「了」在`V`上，「没」在`I`上，「不」在`D`上，「上」在`K`上。

二级简码字共625个，是该字全码的前两个字母。宇浩输入法**全简一致**。

### 2.4. 词语编码

宇浩输入法**字词编码一致**。规则如下：

- 两字词，取每个字**全码**的前两码即可。
- 三字词，取前两字的第一码，和第三个字的前两码即可。
- 四字词及以上，取前三字的第一码，和最后一个字的第一码即可。

### 2.5. 拆字规则

「宇浩」拆字规则的按优先级排序如下：

1. 字根最少
2. 符合笔顺
3. 字根离散
4. 字根相连
5. 字根相交
6. 笔划断开
7. 拆分美观
8. 字根取大

## 3. RIME 方案

本方案挂载于RIME平台（小狼毫、鼠须管）<https://rime.im/>。其具有以下特点：

- 提供至CJK-H区、兼容区、部首区超过98000个汉字的完整拆分、编码提示、字集提示。
- 支持二级简码快速标点符号输入。
- 支持自定义字符集过滤生僻字。常用字约一万字，包括GB2312汉字、國語常用字、其它常用汉字等。支持用户自定义修改。
- 提供四码只出单字功能，适合单字派。

### 3.1. Windows / Macos / 安卓安装方法

在安装了 Rime（小狼毫、鼠须管、同文）后，将 [/schema](https://github.com/forFudan/yuhao/tree/main/schema) 文件夹下的所有文件复制到 Rime 目录下。同时在 default.custom.yaml 文件中加入以下内容：

```yaml
patch:
  schema_list:
    - schema: yuhao
    - schema: yuhao_starter
```

点击「部署」之后即可使用。

### 3.2. 具体文件介绍

文件介绍：

- yuhao.schema.yaml 方案文件
- yuhao_starter.schema.yaml 给新手使用的方案文件，默认打开拆分提示、屏蔽生僻字、开启预测、显示9个候选项。
- yuhao.dict.yaml 字典文件
- rime.lua 脚本设定
- lua/yuhao/... 各种脚本
- opencc/... 單字拆分表
- build/clover... 已编译好的四叶草拼音文件。或者自行安装。<https://github.com/fkxxyz/rime-cloverpinyin>

## 4. 方案特点

### 4.1. 提示快捷键

输入`help`或`zzzz`或`bang`可显示快捷键提示。

### 4.2. 单字拆分三重注解

提供至CJK-H区、兼容区、部首区超过98000个汉字的拆分、编码提示、字集提示。拆分提示中包括三重注解：

1. 该汉字的拆分。
2. 该汉字的全码。使用大小写字母区分大小码。
3. 该汉字所在的字符集（GB2312，GBK，CJK，CJK A 到 H 区，兼容字等）。

用户还可通过「Shift+Ctrl+C」切换拆分状态。

### 4.3. 增广常用字符集

本方案使用了自定的常用字符，将常用字一网打尽，避免了 RIME 内置字符集「GB2312字太少，GBK字太多」的问题。包括了以下一万个左右的字符：

- 《通用规范汉字表》中定义的，在 GB2312 字集内的汉字
- 台湾的「国字常用字」
- 286个大陆繁体字形
- 注音符号
- 「〇」符号

### 4.4. 一键切换字符集

在输入过程中，用户可选择两种切换字集的方式：

- 通过「Shift+Ctrl+O」在常用字符集和CJK大字符集之间进行切换（过滤）。
- 通过「Shift+Ctrl+I」将常用字符集优先显示（优先）。

用户还可通过「Shift+Ctrl+F」进行简入繁出输入。

### 4.5. 使用 Z 键引导四叶草拼音输入和反查

按下 Z 键，可以随时使用四叶草拼音输入词语，并实现反查。四叶草拼音：<https://github.com/fkxxyz/rime-cloverpinyin>

### 4.6. 全码词语屏蔽

一键屏蔽四码词语，同时保留简码词。热键为「Shift+Ctrl+D」。适合保留简码词的全码单字派。
