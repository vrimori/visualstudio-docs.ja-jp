---
title: "IDebugApplicationNode100 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 インターフェイス
`IDebugApplicationNode100`インターフェイスの機能を拡張する、 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)です。 実装での QueryInterface を呼び出すことにより、このインターフェイスのインスタンスを取得することができます[IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)です。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v10.0 によってです。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IDebugApplicationNode100` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|指定したフィルターによって隠ぺいされているテキスト ドキュメントを取得します。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|指定されたドキュメントがこのノードの子ノードのいずれかに属するかどうかを判断します。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|特定のフィルターを設定[IDebugApplicationNodeEvents インターフェイス](../../winscript/reference/idebugapplicationnodeevents-interface.md)実装します。 それにより、スクリプト デバッガー、PDM はノードが作成または削除されたときにイベントを送信できなくなるように、コンパイラによって生成された子アプリケーション ノードをフィルターすることができます。 既定では、すべてのノードが送信されます。|