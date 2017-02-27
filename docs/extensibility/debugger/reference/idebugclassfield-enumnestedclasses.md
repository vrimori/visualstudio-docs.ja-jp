---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses メソッド"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このクラスに入れ子になったクラスの列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) を表すオブジェクトを入れ子になったクラスのリストを返します。  入れ子になったクラスが存在しない場合は null を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK を返します。正常または入れ子になったクラスがあります。  それ以外の場合はエラー コード。  
  
## 解説  
 列挙体の各要素は入れ子になったクラスを記述する [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) のオブジェクトです。  
  
 入れ子になったクラスが他のクラス内で定義されるクラスです。  次に例を示します。  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) の列挙型は1 `NestedClass` を表すオブジェクトのクラスが含まれています。  
  
## 参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)