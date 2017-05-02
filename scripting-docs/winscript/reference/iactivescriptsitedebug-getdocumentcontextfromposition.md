---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
`IDebugCodeContext::GetSourceContext`に代行させるために言語エンジンによって使用されます。  
  
## 構文  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### パラメーター  
 `dwSourceContext`  
 \[入力\] `ParseScriptText` または `AddScriptlet`へのソースの内容そのまま。  
  
 `uCharacterOffset`  
 \[入力\]スクリプト ブロックまたはスクリプトレット文字のオフセットの相対的な開始。  
  
 `uNumChars`  
 \[出力\]このコンテキストの文字数。  
  
 `ppsc`  
 \[出力\]この文字位置の範囲に対応するドキュメントのコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 言語のエンジンは `IDebugCodeContext::GetSourceContext`に代行させるには、このメソッドを使用します。  
  
## 参照  
 [IActiveScriptSiteDebug インターフェイス](../../winscript/reference/iactivescriptsitedebug-interface.md)