---
title: "IDebugSettingsCallback2::GetEEMetricDword | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEEMetricDword"
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

式エバリュエーターの指定に対応する値を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```c#  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### パラメーター  
 `guidLang`  
 \[入力\] プログラミング言語の一意の識別子。  
  
 `guidVendor`  
 \[入力\] 販売元の一意の識別子。  
  
 `pszMetric`  
 \[入力\] メトリックスの名前。  
  
 `pdwValue`  
 \[入力\] メトリック文字列に対応する値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)