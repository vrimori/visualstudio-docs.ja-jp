---
title: IDebugApplicationNodeEvents インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0396ed90437a98c8ee398f3c3acb0aeb5ddc77e2
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348413"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents インターフェイス
`IDebugApplicationNode` インターフェイスに対するイベント インターフェイスを提供します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugApplicationNodeEvents`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|デバッグのアプリケーション ノード オブジェクトに子ノードが追加されたときにイベントを処理します。|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|デバッグのアプリケーション ノード オブジェクトから子ノードが削除されたときにイベントを処理します。|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|アプリケーションのデバッグ ノード オブジェクトが親ノードからデタッチされたことを示すイベントを処理します。|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|アプリケーションのデバッグ ノード オブジェクトが親ノードに接続されていることを示すイベントを処理します。|  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationNode インターフェイス](../../winscript/reference/idebugapplicationnode-interface.md)