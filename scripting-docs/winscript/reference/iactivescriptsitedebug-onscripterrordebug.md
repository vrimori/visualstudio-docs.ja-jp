---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
スマート ホストがランタイム エラーの処理方法を決定できるようにします。  
  
## 構文  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### パラメーター  
 `pErrorDebug`  
 \[入力\]実行時エラー発生した  
  
 `pfEnterDebugger`  
 \[入力\]示すことをデバッガーにエラーを JIT デバッグを行うに渡すかフラグを設定します。  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[入力\]デバッグを続行できなくなります。ユーザーにすると表示を `IActiveScriptSite::OnScriptError` を呼び出すするかどうかを示すフラグを設定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  有効な値は、次の表の値に含まれますが、はありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 スマート ホストは、ランタイム エラーの処理方法を決定するために、このメソッドを使用できます。  
  
## 参照  
 [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)