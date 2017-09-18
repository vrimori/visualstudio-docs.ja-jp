---
title: "IDebugSettingsCallback2::GetEELocalObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSettingsCallback2::GetEELocalObject"
ms.assetid: e69a3469-a049-420c-b918-c48a1e7b9baf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugSettingsCallback2::GetEELocalObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

非常名前を持つ式エバリュエーターのローカル オブジェクトを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetEELocalObject(  
   REFGUID     guidLang,  
   REFGUID     guidVendor,  
   LPCWSTR     pszMetric,  
   IUnknown ** ppUnk  
);  
```  
  
```c#  
private int GetEELocalObject(  
   ref Guid          guidLang,  
   ref Guid          guidVendor,  
   string            pszMetric,  
   out System.Object ppUnk  
);  
```  
  
#### パラメーター  
 `guidLang`  
 \[入力\] プログラミング言語の一意の識別子。  
  
 `guidVendor`  
 \[入力\] 販売元の一意の識別子。  
  
 `pszMetric`  
 \[入力\] メトリックスの名前。  
  
 `ppUnk`  
 \[入力\] 式エバリュエーターのローカル オブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)