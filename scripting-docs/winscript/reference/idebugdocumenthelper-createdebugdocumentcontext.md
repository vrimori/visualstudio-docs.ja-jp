---
title: "IDebugDocumentHelper::CreateDebugDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.CreateDebugDocumentContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::CreateDebugDocumentContext"
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::CreateDebugDocumentContext
新しいデバッグのドキュメントのコンテキストを作成します。  
  
## 構文  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### パラメーター  
 `iCharPos`  
 \[入力\]デバッグのドキュメントのコンテンツの先頭の位置。  
  
 `cChars`  
 \[入力\]コンテキストの文字数。  
  
 `ppddc`  
 \[入力\]新しいデバッグのドキュメントのコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、ホストが新しいデバッグのドキュメントのコンテキストを作成できるようにします。  
  
## 参照  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)