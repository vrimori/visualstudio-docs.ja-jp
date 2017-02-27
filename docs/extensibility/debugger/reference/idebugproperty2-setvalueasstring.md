---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定された文字列からプロパティの値を設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### パラメーター  
 `pszValue`  
 \[入力\] 文字列設定する値。  
  
 `nRadix`  
 \[入力\] 数値情報を解釈で使用される A の基数。  これは基数を自動的に決定する 0 です。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機するミリ秒単位の最大時間を指定します。  無期限に待機するために `INFINITE` を使用します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  次の表は他の値を示します。  
  
|値|Description|  
|-------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|文字列はプロパティ値に変換できないかプロパティ値が設定されていることができませんでした。|  
|`E_SETVALUE_VALUE_IS_READONLY`|プロパティは読み取り専用です。|  
  
## 参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)