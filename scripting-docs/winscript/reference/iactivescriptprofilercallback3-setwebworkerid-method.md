---
title: "IActiveScriptProfilerCallback3::SetWebWorkerId メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerCallback3::SetWebWorkerId メソッド
ワーカー スレッドの ID についてプロファイラーにこのプロファイル セッションで使用する通知します。  関数がページのコンテキストで実行しない場合、このメソッドは呼び出されません。  `webWorkerId` の値は、ワーカーごとに 1 を乗算し、と 1.で開始されます。  ID の値はセッションを超えて安定することを目的としていないしてワーカー スレッドが作成された順にのみ対応します。  
  
## 構文  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
  
```  
  
#### パラメーター  
 `webWorkerId`  
 Web ワーカー スレッド ID  
  
## 戻り値  
 このメソッドの戻り値は、スクリプト エンジンでは無視されます。