---
title: "IDebugEvent2::GetAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2::GetAttributes"
helpviewer_keywords: 
  - "IDebugEvent2::GetAttributes"
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEvent2::GetAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このデバッグ イベントの属性を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```c#  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### パラメーター  
 `pdwAttrib`  
 \[入力\] [複数](../../../extensibility/debugger/reference/eventattributes.md) の列挙体のフラグの組み合わせ。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはすべてのイベントが一般的です。  このメソッドはイベントの種類を記述します ; たとえばイベントの同期または非同期であり停止のイベントがあります。  
  
## 参照  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [複数](../../../extensibility/debugger/reference/eventattributes.md)