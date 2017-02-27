---
title: "IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::IsCustomAttributeDefined"
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCustomAttributeQuery2::IsCustomAttributeDefined
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

カスタム属性を名前であるかどうかを判定します。  
  
## 構文  
  
```cpp#  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```c#  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### パラメーター  
 `pszCustomAttributeName`  
 \[入力\] 文字列検索するカスタム属性の名前。  
  
## 戻り値  
 カスタム属性がこのフィールドで定義されている場合は S\_OK を返します。それ以外の場合は S\_FALSE を返します。  
  
## 解説  
 カスタム属性に関連付けられた属性のバイトを取得するには [GetCustomAttributeByName](../Topic/IDebugCustomAttributeQuery2::GetCustomAttributeByName.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)