---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
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
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "IDebugMethodField::EnumArguments メソッド"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

メソッドを呼び出すために必要な各引数の型の列挙子を作成します。  
  
## 構文  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### パラメーター  
 `ppParams`  
 \[入力\] [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) に引数型リストを返します。  引数がない場合は null 値を返します。  
  
## 戻り値  
 S\_FALSEは S\_OK または成功した場合に引数がない場合は。  それ以外の場合はエラー コード。  
  
## 解説  
 各要素は [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) に各パラメーターの型です。  各パラメーターの型に関する情報を取得するために [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) のメソッドを呼び出します。  
  
 パラメーターの名前を型とともに応じて[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)