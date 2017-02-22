---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
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
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters メソッド"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドのパラメーターの列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### パラメーター  
 `ppParams`  
 \[入力\] メソッドの [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) のパラメーターを表すオブジェクトのリストを返します ; パラメーターが存在しない場合null 値を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功したパラメーターがあります。  それ以外の場合はエラー コード。  
  
## 解説  
 各要素はパラメーターの [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) を表すオブジェクトの種類です。  どのようなパラメーターをオブジェクトが表すかを確認するには各オブジェクトの [GetKind](../Topic/IDebugField::GetKind.md) のメソッドを呼び出します。  
  
 パラメーターは変数名と型の両方が含まれます。  クラス メソッドの最初のパラメーターは「」ポインターです。  
  
 パラメーターの型だけ [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)のメソッドを呼び出します。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)