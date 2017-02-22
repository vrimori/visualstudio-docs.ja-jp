---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker インターフェイス"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートを選択するためのカスタマイズした UI を表します。  
  
## 構文  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはポートの仕入先によって実装されます。  ポートの業者はCLSID とそれを公開し公開された CLSID を `metricPortPickerCLSID` メトリックをポイントしてポートの指定を定義します。  
  
## メソッド  
 次の表は `IDebugPortPicker` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|ポートをユーザーが選択できるように指定するダイアログ ボックスが表示されます。|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|サービス プロバイダーを設定します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll