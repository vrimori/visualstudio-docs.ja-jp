---
title: ISimpleConnectionPoint インターフェイス |Microsoft Docs
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
ms.openlocfilehash: 4a756fa3f933f4adff56c41a86aee19a0a2a93aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346411"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint インターフェイス
記述すると、特定の接続ポイントで発生したイベントを列挙する簡単な方法を提供します。 このインターフェイスも簡単にフックするため、`IDispatch`それらのイベント オブジェクト。 このインターフェイスは実装によって、プロセス デバッグ マネージャー (PDM) と、スクリプト エンジンによって消費されます。  
  
 このインターフェイスはから利用可能な`IDebugHelper::CreateSimpleConnectionPoint`します。  
  
 継承されたメソッドだけでなく`IUnknown`、`ISimpleConnectionPoint`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|単純な接続ポイント オブジェクトとクライアントのシンクの間の接続を確立します。|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|イベントの指定した範囲内で、DISPID と各イベントの名前を返します。|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|このインターフェイスで公開されているイベントの数を返します。|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|以前に確立したアドバイザリ コネクションを終了`ISimpleConnectionPoint::Advise`します。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)