---
title: "IMachineDebugManagerEvents インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369dc8d182efe7bf9697454d0e4b1c9c1a10c027
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents インターフェイス
実行では、変更の通知は、machine デバッグ manager によって管理されるアプリケーションの一覧です。 このインターフェイスは、アプリケーションの動的な一覧を表示する、デバッガーの IDE で使用できます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IMachineDebugManagerEvents`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|アプリケーションが実行に追加されたときにイベントを処理するアプリケーションの一覧です。|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|アプリケーションが実行中から削除されたときにイベントを処理するアプリケーションの一覧です。|