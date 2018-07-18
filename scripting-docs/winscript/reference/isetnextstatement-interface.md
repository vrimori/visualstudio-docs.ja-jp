---
title: ISetNextStatement インターフェイス |Microsoft ドキュメント
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
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733622"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement インターフェイス
このインターフェイスは、現在のステートメントを更新するプロセスをデバッグ Manager を許可する、インタープリターによって実装されます。 スタック フレーム オブジェクトでは、実装されているし、PDM は QueryInterface を介して、このインターフェイスを取得します。  
  
 インターフェイスは、次に実行されるステートメントを決定する実行ポイントを設定するための便利なメソッドを提供します。  
  
 継承されたメソッドだけでなく`IUnknown`、`ISetNextStatement`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|実行ポイントを指定した場所に設定できるかどうかを決定します。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|指定した場所に、実行ポイントを設定します。|