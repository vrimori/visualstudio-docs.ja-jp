---
title: "IDebugMethodField::EnumStaticLocals | Microsoft Docs"
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
  - "IDebugMethodField::EnumStaticLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumStaticLocals メソッド"
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドの静的ローカル変数の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### パラメーター  
 `ppLocals`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) のオブジェクトを表す静的ローカルのリストを返します。  静的ローカルでない場合は null 値を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功した場合静的なローカルする必要があります。  それ以外の場合はエラー コード。  
  
## 解説  
 各要素は静的なローカルの [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) を表すオブジェクトの種類です。  どのような静的ローカル変数のオブジェクトが表すかを確認するには各オブジェクトの [GetKind](../Topic/IDebugField::GetKind.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)