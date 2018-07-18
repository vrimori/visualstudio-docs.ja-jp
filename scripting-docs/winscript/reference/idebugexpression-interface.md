---
title: IDebugExpression インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727792"
---
# <a name="idebugexpression-interface"></a>IDebugExpression インターフェイス
非同期的に評価される式を表します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 通常、デバッガーの IDE は、即時実行ウィンドウを有効にするか、[ウォッチ] ウィンドウにこのインターフェイスを使用します。  
  
> [!NOTE]
>  `IDebugExpression`インターフェイスはスタック フレームからのみ使用できます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugExpression`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|式の評価を開始します。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|式を中止します。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|操作が完了を決定します。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|文字列および操作の戻り値として式の評価の結果を返します。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|デバッグ プロパティおよび操作の戻り値として式の評価の結果を返します。|