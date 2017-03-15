---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierDescription2 インターフェイス"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI を ENT1ENT \[出力\] ダイアログ ボックスの \[ENT0ENT\] セクション内のテキストを表示できます。  
  
## 構文  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## 実装についてのメモ  
 このインターフェイスはポートの仕入先によって実装されます。  
  
## メソッド  
 次の表は `IDebugPortSupplierDescription2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|ポートのサプライヤーの説明と説明のメタデータを取得します。|  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll