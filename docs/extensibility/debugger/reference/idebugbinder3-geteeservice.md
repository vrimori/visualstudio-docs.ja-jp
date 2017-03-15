---
title: "IDebugBinder3::GetEEService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetEEService"
helpviewer_keywords: 
  - "IDebugBinder3::GetEEService メソッド"
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは要求したサービス。  
  
## 構文  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```c#  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### パラメーター  
 `vendor`  
 \[入力\] `GUID` の販売元 \(null 値が許容範囲内です\)。  
  
 `language`  
 \[出力\] 言語の `GUID` \(null 値が許容範囲内です\)。  
  
 `iid`  
 \[入力\] 取得するサービス `IID`。  
  
 `ppService`  
 \[入力\] 要求したサービスへのインターフェイス。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 型のビジュアライザーのサービスを使用できるかどうかを確認するに [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) インターフェイス \(`IID_IEEVisualizerServiceProvider`\) の `IID` を渡します。  その場合は式エバリュエーターは型のビジュアライザーをサポートするために [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) のインターフェイスを取得できます。  詳細については、「[視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)」を参照してください。  
  
## 参照  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [視覚化して、データを表示します。](../../../extensibility/debugger/visualizing-and-viewing-data.md)