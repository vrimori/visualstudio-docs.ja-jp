---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
`IDebugDocumentContext::EnumCodeContexts`のメソッドに代行させるには、スマート ホストによって使用されます。  
  
## 構文  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### パラメーター  
 `dwSourceContext`  
 \[入力\] `IActiveScriptParse::ParseScriptText` または `IActiveScriptParse::AddScriptlet`へのソースのコンテキストそのまま。  
  
 `uCharacterOffset`  
 \[入力\]スクリプトのテキスト文字のオフセットの相対的な開始。  
  
 `uNumChars`  
 \[出力\]このコンテキストの文字数。  
  
 `ppescc`  
 \[出力\]指定した範囲コードのコンテキストの列挙子。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 スマート ホストは `IDebugDocumentContext::EnumCodeContexts` のメソッドをデリゲートにこのメソッドを使用します。  
  
## 参照  
 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)