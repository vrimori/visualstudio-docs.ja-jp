---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
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
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass メソッド"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このクラスを囲むクラスを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### パラメーター  
 `ppClassField`  
 \[入力\] [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 外側のクラスを表すオブジェクトを返します。  外側のクラスが存在しない場合は null を返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)このオブジェクトによって表されるクラスが入れ子になったクラスで`ppClassField` のパラメーターは `IDebugClassField` 外側のクラスを表すオブジェクトを返します。  たとえばこのクラスを定義する :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 `IDebugClassField` を表すオブジェクトの `GetEnclosingClass` のメソッドを `NestedClass` クラスのという `IDebugClassField` のクラス `RootClass` 表すオブジェクトを返します。  
  
## 参照  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)