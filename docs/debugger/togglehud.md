---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グラフィックス診断の *HUD* \(ヘッドアップ ディスプレイ\) オーバーレイのオンとオフを切り替えます。  
  
## 構文  
  
```cpp  
void ToggleHUD();  
```  
  
## 解説  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。  これには、アプリケーションとグラフィックス情報キャプチャのランタイム情報、および [AddMessage](../debugger/addmessage.md) メンバー関数の呼び出しによって追加されたメッセージが表示されます。  
  
 HUD を切り替えるには、アクティブにグラフィックス情報をキャプチャする必要はありません。これは、`VsgDbg` クラスのインスタンスを通じて切り替えられますが、[Init](../debugger/init.md) メンバー関数は最初に呼び出される必要はありません。