---
title: IDebugThreadCall インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346268"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall インターフェイス
`IDebugThreadCall`インターフェイスは、通常のスレッド間の呼び出しを行うコンポーネントによって実装、`IDebugThread`プロセス デバッグ マネージャー (PDM) によって提供された実装をマーシャ リングします。  
  
 PDM 呼び出し、`IDebugThreadCall`インターフェイスで目的のスレッドと`IDebugThreadCall`インターフェイスが必要な実装への呼び出しをディスパッチします。 `IDebugThreadCall`インターフェイスが適切なページのトップへのパラメーターで渡されるパラメーター情報をキャストします。  
  
 `IDebugThreadCall`インターフェイスは、フリー スレッド オブジェクトです。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IDebugThreadCall`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|別のスレッドでコードを実行する呼び出しを処理します。|