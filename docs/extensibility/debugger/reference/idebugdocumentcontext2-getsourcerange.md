---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このドキュメントのコンテキストのソース・コードの範囲を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### パラメーター  
 `pBegPosition`  
 \[入力出力\] 開始位置が格納されます [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) の構造体。  この情報が不要な場合はこの引数に null 値を設定します。  
  
 `pEndPosition`  
 \[入力出力\] 終了位置が格納されます [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) の構造体。  この情報が不要な場合はこの引数に null 値を設定します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 ソース範囲内にコードを提供する前のステートメントの直後に現在のステートメントからソース・コードの範囲です。  参照元の範囲 \[逆アセンブル\] ウィンドウでに対して複数のソース ステートメントはコードのコメントが使用されます。  
  
 このドキュメントのコンテキスト内に含まれているコードだけステートメントのスコープを取得するには [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)