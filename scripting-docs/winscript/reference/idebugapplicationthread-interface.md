---
title: "IDebugApplicationThread インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread インターフェイス
言語エンジンとホストのスレッドの同期を行うと、スレッド固有のデバッグ状態情報を維持するために使用できます。 このインターフェイスは、`IRemoteDebugApplicationThread`スレッドへの非リモート アクセスを提供するインターフェイスです。  
  
 継承されたメソッドだけでなく`IRemoteDebugApplicationThread`、`IDebugApplicationThread`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|呼び出し元アプリケーションのスレッドでコードを実行するためのメカニズムを提供します。|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|このスレッドが現在実行中のスレッドであるかどうかを判断します。|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|このスレッドが、デバッガー スレッドであるかどうかを判断します。|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|このスレッドの説明を設定します。|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|スレッドの状態の説明を設定します。|