---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スタック フレームに関連付けられた物理アドレス範囲のコンピューターに依存しない表現を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### パラメーター  
 `paddrMin`  
 \[出力\] このスタック フレームに関連付けられている最小の物理アドレスを返します。  
  
 `paddrMax`  
 \[出力\] このスタック フレームに関連付けられている最上位の物理アドレスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッグ セッションのマネージャー \(SDM\) によって返される情報がこのメソッドによりスタック フレームの並べ替えに使用されます。  
  
 新しいスタック フレームがます。下位メモリ アドレスに追加されることつまり呼び出し履歴を越えることを前提としています。  ランタイム アーキテクチャではこの前提条件に一致する物理的なスタック範囲を指定する必要があります。  
  
## 参照  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)