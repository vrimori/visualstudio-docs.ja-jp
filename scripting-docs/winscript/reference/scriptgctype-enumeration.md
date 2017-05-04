---
title: "SCRIPTGCTYPE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE 列挙型
実行するガベージ コレクションの種類。  [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) メソッドで使用されます。  
  
## 構文  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|通常のガベージ コレクションを実行します。  整数値は 0 です。|  
|SCRIPTGCTYPE\_EXHAUSTIVE|プローブ ガベージ コレクションを実行します。  整数値は 1.です。|  
  
## 参照  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)