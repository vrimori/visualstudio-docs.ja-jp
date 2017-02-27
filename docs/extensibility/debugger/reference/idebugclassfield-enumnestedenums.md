---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedEnums メソッド"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このクラスの入れ子になった列挙子の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### パラメーター  
 `ppEnum`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) の入れ子になったオブジェクトを表す列挙型のリストを返します。  入れ子になった列挙型が存在しない場合は null を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功した場合入れ子になった列挙子を返します。  それ以外の場合はエラー コード。  
  
## 解説  
 列挙体の各要素は入れ子になった列挙型を記述する [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) のオブジェクトです。  
  
 クラス内で宣言された列挙型は入れ子になった列挙型と見なされます。  次に例を示します。  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums` のメソッドは `NestedEnum` の列挙型を表す [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) の 1 個のオブジェクトを含む [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) のオブジェクトを返します。  
  
## 参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)