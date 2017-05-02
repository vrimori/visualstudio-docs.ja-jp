---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
スクリプトが実行を完了したことをホストに通知します。  
  
## 構文  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### パラメーター  
 `pvarResult`  
 \[入力\]スクリプトが結果を生まなかったらスクリプトの結果を格納する変数のアドレス、または `NULL`。  
  
 `pexcepinfo`  
 \[入力\]例外情報を含む `EXCEPINFO` の構造体のアドレスは、例外が生成されなかった場合、スクリプトがいつ完了するか、`NULL` 発生させます。  
  
## 戻り値  
 正常に終了した場合は `S_OK` を返します。  
  
## 解説  
 スクリプト エンジンは [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) メソッドの呼び出しでは、SCRIPTSTATE\_INITIALIZED のフラグのセットと、完了前にこのメソッドを呼び出します。  このメソッドがホストに完了ステータスと結果を返すために使用できます。  ホストから沈降のイベントに基づいて、多くのスクリプト言語にホストで定義されている期間があることに注意してください。  この場合、このメソッドは、呼び出されることがあります。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)