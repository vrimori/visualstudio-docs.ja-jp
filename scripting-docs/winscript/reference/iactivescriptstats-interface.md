---
title: "IActiveScriptStats インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptStats インターフェイス"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats インターフェイス
ホストが実行中のスクリプトの統計情報を照会できます。  ホストは、スクリプトが完了するには大きすぎる時間がかかっているかどうかを判断するために、この情報を使用できます。  
  
 `IUnknown` から継承するメソッドに加え、`IActiveScriptStats` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|標準的なスクリプトの統計情報は 1 を返します。|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|カスタム スクリプトの統計情報を返します。|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|このスクリプトの統計をリセットします。|