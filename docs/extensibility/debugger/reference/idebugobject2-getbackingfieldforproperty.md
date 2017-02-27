---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty メソッド"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このオブジェクトによって表されるプロパティをサポートする必要がある変数を取得します \(存在する場合\) またはフィールドを示します。  
  
## 構文  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### パラメーター  
 `ppObject`  
 \[入力\] バッキング フィールドを説明する [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) のオブジェクト。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) のオブジェクトはget または set アクセサーとマネージ コードのクラスプロパティメソッドを表します。  このようなプロパティは一般に変数がプロパティによって処理される値を含める必要があります。  この変数はバッキング フィールドと呼ばれます。  オブジェクトのバッキング フィールドがない場合はNULL 値が返されることを確認する : 一部の呼び出し元は戻り値に注意を払わないこともありますがnull 値が `ppObject` に返されたかどうかを確認するには" " を参照してください。  
  
## 参照  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)