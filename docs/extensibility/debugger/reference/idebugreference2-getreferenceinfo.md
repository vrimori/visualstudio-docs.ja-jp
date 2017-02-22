---
title: "IDebugReference2::GetReferenceInfo | Microsoft Docs"
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
  - "IDebugReference2::GetReferenceInfo"
helpviewer_keywords: 
  - "IDebugReference2::GetReferenceInfo"
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

参照を記述する [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体を取得します。  将来使用するために予約されています。  
  
## 構文  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```c#  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### パラメーター  
 `dwFields`  
 \[入力\] [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体に格納するフィールドを決定 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) の列挙体のフラグの組み合わせ。  
  
 `nRadix`  
 \[入力\] 情報を数値書式で使用する小数点。  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機する最大時間 \(ミリ秒単位\)。  無期限に待機するために `INFINITE` を使用します。  
  
 `rgpArgs`  
 \[入力\] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) の配列を取得します。  将来使用するために予約されています ; null 値に設定します。  
  
 `dwArgCount`  
 \[入力\] 配列の `rgpArgs` の参照引数の数。  将来使用するために予約されています ; 0 に設定します。  
  
 `pReferenceInfo`  
 \[入力\] プロパティの説明が格納されます [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造体。  
  
## 戻り値  
 常に `E_NOTIMPL` を返します。  
  
## 参照  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)