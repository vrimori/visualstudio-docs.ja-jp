---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
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
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors メソッド"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このクラスのコンストラクターの列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### パラメーター  
 `cMatch`  
 \[入力\] 列挙型にコンストラクターの [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) の種類を指定する列挙体の値。  
  
 `ppEnum`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) のコンストラクターを表すオブジェクトのリストを返します。  コンストラクターがない場合は null 値を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK またはコンストラクターが成功した場合は。  それ以外の場合はエラー コード。  
  
## 解説  
 列挙体の各要素はコンストラクター メソッドを記述する [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) のオブジェクトです。  
  
 コンストラクターの一覧はコンパイラによって指定される既定のコンストラクターがありません。  
  
## 参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)