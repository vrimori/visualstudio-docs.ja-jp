---
title: ISimpleConnectionPoint インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de40f66a9e5721b8dacac634c6fb77982017c155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733912"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint インターフェイス
記述したり、特定の接続ポイントで発生したイベントを列挙する簡単な方法を提供します。 このインターフェイスも簡単にフックする、`IDispatch`それらのイベント オブジェクトです。 このインターフェイスは実装によって、プロセスをデバッグ マネージャー (PDM) をスクリプト エンジンによって消費されています。  
  
 このインターフェイスを使用してから`IDebugHelper::CreateSimpleConnectionPoint`です。  
  
 継承されたメソッドだけでなく`IUnknown`、`ISimpleConnectionPoint`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|単純な接続ポイント オブジェクトとクライアントのシンク間の接続を確立します。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|イベントの指定された範囲内の各イベントの名前と DISPID を返します。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|このインターフェイスで公開されているイベントの数を返します。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|以前にを介して確立アドバイザリ コネクションを終了する`ISimpleConnectionPoint::Advise`です。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)