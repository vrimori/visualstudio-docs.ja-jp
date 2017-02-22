---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes メソッド"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

値を一連の連続から参照されるように設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### パラメーター  
 `dwStart`  
 \[入力\] オフセットはオブジェクトのサイズ \(バイト単位\) としてが指す。  
  
 `dwCount`  
 \[入力\] 設定するバイト数。  
  
 `pBytes`  
 \[入力\] 新しい値を表すバイトの配列。  この値は指定したオフセット位置で呼び出すオブジェクトに格納されます。  
  
 `pdwBytes`  
 \[入力\] 設定に実際のバイト数を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはプリミティブ型 \(単純なバイト シーケンスを表すことができる\) のプリミティブ型または単純な配列へのポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) の配列を使用します。このによって表されるようにポインター。  `IDebugPointerObject` でこのオブジェクトはnull 参照 \(メモリのアドレスを指す必要があります\) にすることはできません。  
  
## 参照  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)