---
title: "IDebugApplicationNode100::GetExcludedDocuments | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100::GetExcludedDocuments"
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100::GetExcludedDocuments
指定したフィルターによって非表示になっているテキスト ドキュメントを取得します。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 インターフェイス](../../winscript/reference/idebugapplicationnode100-interface.md) は PDM v10.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
HRESULT GetExcludedDocuments(  
        [in] APPLICATION_NODE_EVENT_FILTER filter,  
        [out] TEXT_DOCUMENT_ARRAY* pDocuments  
        );  
```  
  
#### パラメーター  
 `filter`  
 フィルターです。  
  
 `pDocuments`  
 ドキュメント セット。  
  
## 参照  
 [IDebugApplicationNode100 インターフェイス](../../winscript/reference/idebugapplicationnode100-interface.md)