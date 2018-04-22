﻿<!--
  Copyright (c) 2017, Xin YUAN, courses of Zhejiang University
  All rights reserved.

  This program is free software; you can redistribute it and/or
  modify it under the terms of the 2-Clause BSD License.

  Author contact information:
    yxxinyuan@zju.edu.cn
-->

# 阿法狗

## 前言

自2015年10月以来，谷歌的围棋机器人阿法狗 (AlphaGo) 大出风头，横扫一众世界顶尖围棋高手。
2017年5月，柯洁再次败于阿法狗。那么，阿法狗真有这么神奇吗？真的是人工智能的重大突破吗？
本文就试图为各位看官揭开它背后的秘密。

## AlphaGo的基本步骤

和双角色棋类游戏一样，人机对战围棋程序也是使用算法(1.1)。但是，围棋程序需要构建的搜索树
规模更大，远远超过中国象棋。围棋棋盘有19*19个交叉点，即361个交叉点，因而在人机对战程序
进行第一步或第二步的完整搜索树生成时，需要产生的节点总数为361*360*...*1，再去掉少量
无效局面，这还是一个天文数字，远远超过整个宇宙的粒子总数，比象棋的复杂度更高，
所以更不可能在程序中实现了。

还是要引入局面评估函数`y=f(X)`。引入它之后，就可以和象棋程序一样进行剪枝，
从而减少搜索树的大小，在可以接受的时间内求出每一步的下法。
因为棋局盘面的每个交叉点有黑子、白子、无子三种情况，因而局面总数是3^361种。这是有限的数字，
所以最直接的实现是做一个数据库，每个局面一一对应着一个评估值。
但是，表示这个自变量的局面总数是天文数字，除去无效的局面，剩下的局面总数也是天文数字，
尽管它远远小于刚才的第一步搜索树的总节点数，但也远远超过整个宇宙的粒子总数了。
所以建立这样的数据库是不可能的，还是需要从自变量本身计算出评估值才有实用价值。

在这里，读者同样可以证明围棋的局面评估函数`y=f(X)`是非线性函数。那么如何得到这个非线性函数呢？
显然，围棋的复杂性远超象棋，不可能和象棋一样通过人工经验的子力评估来获得。所以谷歌的DeepMind公司
直接选择了拟合函数的技术路线。

## AlphaGo Zero

## AlphaZero

[TXTY-20170110]: http://sports.qq.com/a/20170110/014217.htm "腾讯体育"