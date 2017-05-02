---
title: "IJsDebugFrame::GetDocumentPositionWithId メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithId メソッド
Returns the current position of this stack frame within the user\-level document.  
  
## 構文  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### パラメーター  
 `pDocumentId`  
 \[出力\] ソース ドキュメントの一意の ID \(IDebugDocumentText へのポインター\)。  
  
 `pCharacterOffset`  
 \[出力\] スクリプトの先頭からの 0 から始まるオフセット。  
  
 `pStatementCharCount`  
 \[出力\] \*pCharacterOffset から始まる現在のステートメントの長さ \(文字数\)。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)