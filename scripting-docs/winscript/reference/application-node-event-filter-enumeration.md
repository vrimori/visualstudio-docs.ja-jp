---
title: "APPLICATION_NODE_EVENT_FILTER 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "APPLICATION_NODE_EVENT_FILTER 定数"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# APPLICATION_NODE_EVENT_FILTER 列挙型
ノードの型をコード ドキュメントをフィルター処理しないように指定します。  [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) およびで使用される [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  これらの定数は PDM v10.0 を超えるによって実装されます。  activdbg100.h.である。  
  
## 構文  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|すべてのイベントを送信します。|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|匿名コード ノードを除外します。  これらのノードは `new Function([args,] <code>)'`のように、JScript のランタイムが使用されます。|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|eval コード ノードを除外します。  これらのノードは eval サポートする JScript のランタイムが使用されます。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)