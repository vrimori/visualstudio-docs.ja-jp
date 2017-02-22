---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
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
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt メソッド"
  - "ReadAt メソッド"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定された位置から開始してバイト シーケンスを読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### パラメーター  
 `pStartContext`  
 \[入力\] 読み取るバイトの場所で起動するかを指定する [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) のオブジェクト。  
  
 `dwCount`  
 \[入力\] 読み取るバイト数。  または `rgbMemory` の配列の長さを指定します。  
  
 `rgbMemory`  
 \[入力出力\] 実際にに読み取られたバイト数が格納された配列。  
  
 `pdwRead`  
 \[出力\] 実際に読み込まれる連続的なバイト数を返します。  
  
 `pdwUnreadable`  
 \[入力出力\] 不可能なバイト数を返します。  クライアントが不可能なバイト数で無関心の場合は null 値を指定できます。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 100 バイトが必要となり最初の 50 が読み取ることができる場合は次の 20 は不可能であり30 はわかりやすくこのメソッドはを返します。:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 この場合呼び出し元 `*pdwRead + *pdwUnreadable < dwCount` 呼び出しを追加する必要があるため要求された 70 によって元の 100 の残りの 30 バイトと `pStartContext` のパラメーターで渡される [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) のオブジェクトを読み取るために進まなければ必要があります。  
  
## 参照  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)