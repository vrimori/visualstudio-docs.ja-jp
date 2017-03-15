---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

グラフィックス診断の *HUD* \(ヘッドアップ ディスプレイ\) にカスタム メッセージを追加します。  
  
## 構文  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### パラメーター  
 `szMessage`  
 HUD に追加するメッセージ。  
  
## 解説  
 グラフィックス診断の HUD は、グラフィック診断で実行されているアプリケーションの左上隅に表示されます。  これには、アプリケーションとグラフィックス情報キャプチャのランタイム情報、およびこの関数の呼び出しによって追加されたメッセージが表示されます。  
  
 HUD に情報メッセージを追加するには、アクティブにグラフィックス情報をキャプチャする必要はありません。メッセージは、`VsgDbg` クラスのインスタンスを使用して追加できますが、[Init](../debugger/init.md) メンバー関数は最初に呼び出されません。  メッセージは HUD に表示されるだけで、グラフィックのログ ファイルには記録されません。