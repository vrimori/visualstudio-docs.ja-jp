---
title: "ISetNextStatement インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement インターフェイス
このインターフェイスは、インタープリターによってプロセス デバッグ マネージャーが現在のステートメントを更新できるように実行されます。  この範囲は、スタック フレーム オブジェクトから実行され、PDM QueryInterface には、このインターフェイスを取得します。  
  
 インターフェイスは、次に実行されるステートメントを決定し、実行ポイントの設定に役立つメソッドを提供します。  
  
 `IUnknown` から継承するメソッドに加え、`ISetNextStatement` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|指定した位置までの実行ポイントが設定できるかどうかを判定します。|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|指定した位置までの実行ポイントを設定します。|