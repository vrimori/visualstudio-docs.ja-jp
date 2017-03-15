---
title: "How to: Start Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++, starting"
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Start Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spy\+\+ は、Visual Studio から起動することも、コマンド プロンプトから起動することもできます。  
  
 Spy\+\+ を起動したときに、コンピューターに変更を加えることの許可を求めるメッセージが表示された場合は、**\[はい\]** をクリックします。  
  
> [!NOTE]
>  Spy\+\+ のインスタンスは 1 つしか実行できません。  別のインスタンスを実行しようとした場合は、現在実行中のインスタンスがフォーカスを受け取ります。  
  
### Spy\+\+ を Visual Studio から起動するには  
  
-   **\[ツール\]** メニューの **\[Spy\+\+\]** をクリックします。  
  
     Spy\+\+ は独立して動作するため、Spy\+\+ を起動した後に Visual Studio を終了できます。  
  
    > [!NOTE]
    >  Spy\+\+ でメッセージをログに記録すると、オペレーティング システムの実行速度が遅くなる場合があります。  
  
### Spy\+\+ をコマンド プロンプトから起動するには  
  
1.  コマンド プロンプト ウィンドウで、ディレクトリを spyxx.exe が格納されているフォルダーに変更します。  通常、このフォルダーのパスは   \\*Visual Studio インストール フォルダー*\\Common7\\Tools\\ です。  
  
2.  「**spyxx.exe**」と入力し、Enter キーを押します。  
  
## 参照  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)