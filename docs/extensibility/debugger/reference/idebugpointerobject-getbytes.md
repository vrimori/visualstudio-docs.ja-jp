---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes メソッド"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

一連の連続として参照される値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### パラメーター  
 `dwStart`  
 \[入力\] オフセット指すオブジェクトのサイズ \(バイト単位\) として表示されます。  
  
 `dwCount`  
 \[入力\] 取得するバイト数。  
  
 `pBytes`  
 \[入力出力\] 文字の連続として値が格納されたオブジェクトの指定したオフセット位置で開始する配列もをポイントします。  
  
 `pdwBytes`  
 \[出力\] 実際に取得されるバイト数を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはプリミティブ型 \(単純なバイト シーケンスを表すことができる\) のプリミティブ型または単純な配列へのポインター [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) の配列を使用します。このによって表されるようにポインター。  
  
## 参照  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)