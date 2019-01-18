---
title: IDebugSyncOperation インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724ad50771ca49460e130bf93ebc244681bd782
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349606"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation インターフェイス
特定のブロックされたスレッドで入れ子になったときに実行する必要がある (式の評価) などの操作を抽象化するためのスクリプト エンジンを許可します。 インターフェイスには、応答していない操作をキャンセルするためのメカニズムも提供します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugSyncOperation`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|この同期操作を行う対象のアプリケーションのスレッドを返します。|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|同期的に、操作を実行し、返します。|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|別のスレッドで実行中の操作をキャンセルします。|