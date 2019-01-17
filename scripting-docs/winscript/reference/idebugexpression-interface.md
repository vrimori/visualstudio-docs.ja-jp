---
title: IDebugExpression インターフェイス |Microsoft Docs
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
ms.openlocfilehash: 9684253343aa83cf95f7d816781705eab7fbc327
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345519"
---
# <a name="idebugexpression-interface"></a>IDebugExpression インターフェイス
非同期に評価される式を表します。 スクリプト エンジンは、通常、このインターフェイスを実装します。 デバッガー IDE は、通常、即時実行ウィンドウを有効にするか、[ウォッチ] ウィンドウにこのインターフェイスを使用します。  
  
> [!NOTE]
>  `IDebugExpression`インターフェイスはスタック フレームからのみ使用できます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugExpression`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|式の評価を開始します。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|式を中止します。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|操作の完了が決定します。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|文字列と操作の戻り値として式の評価の結果を返します。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|デバッグ プロパティと操作の戻り値として式の評価の結果を返します。|