---
title: APPLICATION_NODE_EVENT_FILTER 列挙 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0446265d40fb6277fd155f3ed5822c506ae30bc7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641122"
---
# <a name="applicationnodeeventfilter-enumeration"></a>APPLICATION_NODE_EVENT_FILTER 列挙型
コードのドキュメントをフィルター処理するときに除外するノードの型を指定します。 使用される[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)と[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  これらの定数は、PDM v10.0 によって実装されます。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|値|説明|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|すべてのイベントを送信します。|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|匿名コード ノードを除外します。 これらのノードは、ランタイムで使用される、JScript の`new Function([args,] <code>)'`します。|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Eval コード ノードを除外します。 これらのノードは、評価版のサポートについては、JScript ランタイムによって使用されます。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)