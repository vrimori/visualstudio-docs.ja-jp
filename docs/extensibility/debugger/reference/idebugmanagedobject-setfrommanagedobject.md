---
title: "IDebugManagedObject::SetFromManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::SetFromManagedObject"
helpviewer_keywords: 
  - "IDebugManagedObject::SetFromManagedObject メソッド"
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

パラメーターとして指定される値クラスのインスタンスの値クラスのオブジェクト インスタンスの値を設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```c#  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### パラメーター  
 `pManagedObject`  
 \[入力\] 値が設定されているマネージ オブジェクトを表すインターフェイス。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) のオブジェクトによって表されるいるマネージ オブジェクトを変更するために使用されます。  
  
## 参照  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)