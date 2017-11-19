---
title: "IDebugThreadCall インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall インターフェイス
`IDebugThreadCall`インターフェイスは、通常でクロス スレッド呼び出しを行うコンポーネントによって実装、`IDebugThread`プロセス デバッグ マネージャー (PDM) によって提供される実装をマーシャ リングします。  
  
 PDM 呼び出し、`IDebugThreadCall`で目的のスレッドでは、インターフェイス、および`IDebugThreadCall`インターフェイスが必要な実装への呼び出しをディスパッチします。 `IDebugThreadCall`インターフェイスが適切なページのトップへのパラメーターに渡されたパラメーター情報をキャストします。  
  
 `IDebugThreadCall`インターフェイスは、フリー スレッドのオブジェクト。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IDebugThreadCall`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|コードを実行する別のスレッドの呼び出しを処理します。|