---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated メソッド"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはエディット コンティニュかどうか親コンテナーのこのオブジェクトの状態を引き続きまたは古い値です。  カスタムの式エバリュエーターはこのメソッドは常に実行せず`E_NOTIMPL` を返しません。  
  
## 構文  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### パラメーター  
 `pfEncOutdated`  
 \[入力\]`TRUE`\(編集\) は状態を指定して古いにゼロ以外の値を返します。`FALSE`\)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
> [!NOTE]
>  カスタムの式エバリュエーターは `E_NOTIMPL` を常に返す必要です。  
  
## 参照  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)