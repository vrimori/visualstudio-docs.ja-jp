---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
すべての適切なスクリプト エンジンのプロファイルを開始したことをプロファイラーに通知します。  このメソッドを使用して、プロファイリングを開始すると [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が実行中のすべての呼び出し履歴を取得できます。  
  
## 構文  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### パラメーター  
 メソッドはパラメーターを受け取りません。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロファイリングを開始することはできません。|  
|`S_FALSE`|プロファイルは、スクリプトが実行されていないときに開始された場合。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイルは有効になりません。  コールバックは設定されませんでした。|  
|`E_OUTOFMEMORY`|呼び出し履歴は、メモリ不足の状態のを取得できません。|  
  
## 解説  
 `IActiveScriptProfilerControl2::CompleteProfilerStart` を呼び出すと、呼び出し履歴上の関数のイベントが既に送信されるようになります。  このメソッドは、現在のタブにあるスクリプト エンジンの開始をプロファイリング後に呼び出す必要がありました。  メソッドは、スクリプト エンジンに呼び出すことができます。  
  
## 参照  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 インターフェイス](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)