---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
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
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "IDebugObject::GetManagedDebugObject メソッド"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンのアドレス空間にマネージ オブジェクトのコピーを作成します。  
  
## 構文  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### パラメーター  
 `ppObject`  
 \[入力\] [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) を表すオブジェクトを新しく作成されたマネージ オブジェクトを返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  この [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) の値がマネージ クラスのインスタンスを表さない場合は E\_FAIL を返します。  
  
## 解説  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) でこのオブジェクトは `System.Decimal` のインスタンスの値などマネージ クラスのインスタンスをある必要があります。  ローカル コピーを追加することにより[評価します。](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) の呼び出しのオーバーヘッドは削除されます。  
  
## 参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)