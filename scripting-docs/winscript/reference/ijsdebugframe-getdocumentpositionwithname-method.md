---
title: "IJsDebugFrame::GetDocumentPositionWithName メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName メソッド
ユーザー レベルのドキュメント内でのこのスタック フレームの現在の位置を返します。  
  
## 構文  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### パラメーター  
 `pDocumentName`  
 \[出力\] 静的なスクリプト場合は、ドキュメントへの URL。  動的なスクリプトの場合は、スクリプトの種類を含む名前 \(eval code、function code など\) が返されます。  
  
 `pLine`  
 \[出力\] ドキュメント内の 1 から始まる行の位置。  
  
 `pColumn`  
 \[out\] 1\-based line position within the document.  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IJsDebugFrame インターフェイス](../../winscript/reference/ijsdebugframe-interface.md)