---
title: ISetNextStatement インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac2d6dd0da14be5a624cff0b55985770b8d70fdf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344058"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement インターフェイス
このインターフェイスは、現在のステートメントを更新するプロセス デバッグ マネージャーを許可する、インタープリターによって実装されます。 これは、スタック フレーム オブジェクトから実装され、PDM は QueryInterface を使用して、このインターフェイスを取得します。  
  
 インターフェイスは、次に実行するステートメントを決定する実行ポイントを設定するために役立つメソッドを提供します。  
  
 継承されたメソッドだけでなく`IUnknown`、`ISetNextStatement`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|実行ポイントを指定した場所に設定できるかどうかを判断します。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|指定した場所に実行ポイントを設定します。|