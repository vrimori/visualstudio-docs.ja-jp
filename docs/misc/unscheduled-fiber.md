---
title: "スケジュールされていないファイバーです。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# スケジュールされていないファイバーです。
デバッガーでは、式が物理スレッド上でスケジュールされていない論理ファイバー内に存在するため、この式を評価できません。 これは、プロセスが、ファイバーを使用する SQL Server 上で実行されている場合に、発生する可能性があります。  
  
 ファイバーはスタックとレジスタのコンテキストで構成され、任意のスレッドで実行できます。 スレッドからファイバーを交換し、後で別のスレッドで再起動できます。  
  
 **エラー ID:** BC30948  
  
### このエラーを解決するには  
  
-   ファイバーが物理スレッドでスケジュールされていることを確認します。  
  
## 参照  
 [Debugging SQL](http://msdn.microsoft.com/ja-jp/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)