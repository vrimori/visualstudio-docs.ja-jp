---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
エンジンがスクリプトの実行中に実行エラーが発生したことをホストに通知します。  
  
## 構文  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### パラメーター  
 `pase`  
 \[入力\]エラー オブジェクトの [IActiveScriptError](../../winscript/reference/iactivescripterror.md) のインターフェイスのアドレス。  ホストは実行エラーに関する情報を取得するには、このインターフェイスを使用できます。  
  
## 戻り値  
 エラーが正しく処理された場合、または OLE はエラー コードの他で定義された `S_OK` を返します。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)