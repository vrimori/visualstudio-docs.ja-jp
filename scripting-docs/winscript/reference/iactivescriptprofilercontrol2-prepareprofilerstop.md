---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
すべての適切なスクリプト エンジンでプロファイリングを止めようとしていることをプロファイラーに通知します。  このメソッドを使用して、プロファイリングを停止と [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が実行中のすべての呼び出し履歴を取得できます。  
  
## 構文  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### パラメーター  
 メソッドはパラメーターを受け取りません。  
  
## 戻り値  
 HRESULT を返します。  次の値を指定できます。  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|プロファイルを開始できませんでした。|  
|`S_FALSE`|プロファイルは、スクリプトが実行されていないときに終了しました。|  
|`ACTIVPROF_E_PROFILER_ABSENT`|プロファイルは有効になりません。|  
  
## 解説  
 `IActiveScriptProfilerControl2::PrepareProfilerStop` を呼び出すと、呼び出し履歴上の関数のイベントが送信されるようになります。  このメソッドは、現在のタブにあるスクリプト エンジンでプロファイリングを停止前に呼び出す必要があります。  メソッドは、スクリプト エンジンに呼び出すことができます。  
  
## 参照  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 インターフェイス](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)