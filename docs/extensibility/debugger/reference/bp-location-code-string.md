---
title: "BP_LOCATION_CODE_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_STRING"
helpviewer_keywords: 
  - "BP_LOCATION_CODE_STRING 構造体"
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コード ブレークポイントをユーザーが統合開発環境から入力できる文字列に基づいて設定するために使用 \(IDE\) されます。  
  
## 構文  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## メンバー  
 `bstrContext`  
 コード内のブレークポイントのコンテキスト \(通常は呼び出し履歴に表示されるメソッドまたは関数名。  
  
 `bstrCodeExpr`  
 この文字列ブレークポイント コードを記述したユーザー タイプ。  
  
## 解説  
 この構造体共用体の一部として [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) の構造体のメンバーです。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)