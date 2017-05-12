---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
アクティブ スクリプトのホストは、ガベージ コレクションを開始するには、このメソッドを呼び出します。  
  
## 構文  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### パラメーター  
 `scriptgctype`  
 \[入力\] [SCRIPTGCTYPE 列挙型](../../winscript/reference/scriptgctype-enumeration.md) 正常またはプローブ ガベージ コレクションを実行するかどうかを指定します。  
  
## 戻り値  
 HRESULT を返します。  
  
## 参照  
 [IActiveScriptGarbageCollector インターフェイス](../../winscript/reference/iactivescriptgarbagecollector-interface.md)