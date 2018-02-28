---
title: "IDebugSyncOperation インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation インターフェイス
により、特定のブロックされたスレッドで入れ子になったときに実行する必要がある (式の評価) などの操作を抽象化するスクリプト エンジンです。 インターフェイスには、応答しない状態の操作を取り消すための機構も用意されています。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugSyncOperation`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|この同期操作の対象アプリケーションのスレッドを返します。|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|同期的に、操作を実行し、返します。|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|別のスレッドで実行中の操作をキャンセルします。|