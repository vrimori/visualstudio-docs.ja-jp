---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このドキュメントの場所の範囲を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
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
 位置ブレークポイントのドキュメントの場所で指定される範囲がデバッグ エンジン \(DE\) によって実際にコードを提供するステートメントを前方に検索するために使用されます。  次に例を示します。  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 5 行目でプログラム コードには影響しません。  5 行にブレークポイントを設定しデバッガーが de\-DE にコードを提供する最初の行を前方程度を検索する場合はブレークポイントが適切に配置する可能性のある追加の関数行を含む範囲を指定します。  DE はの行のブレークポイントを受け入れることができる行を検出するまで転送を検索します。  
  
## 参照  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)