---
title: "IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs"
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
  - "IDebugPortSupplier3::EnumPersistedPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3::EnumPersistedPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはオブジェクトを永続化されたポートのリストの列挙体を取得します。  
  
## 構文  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### パラメーター  
 `PortNames`  
 \[入力\] 永続化されたポート間にある戻るにはポート名の一覧を含む [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) の構造体。  これらはポートの名前で保持します。  
  
 `ppEnum`  
 \[入力\] [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) のインターフェイスを実装するオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 永続化されたポートはポートのサプライヤーがインスタンス化される読み込まれポートのサプライヤーがいつ破棄されるときに格納されます。  
  
## 参照  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)