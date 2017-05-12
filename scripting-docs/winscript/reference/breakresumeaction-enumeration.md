---
title: "BREAKRESUMEACTION 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION 列挙型"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION 列挙型
ブレークポイントから継続する方法について説明します。  
  
## 構文  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|BREAKRESUMEACTION\_ABORT|アプリケーションを中止します。|  
|BREAKRESUMEACTION\_CONTINUE|実行が継続します。|  
|BREAKRESUMEACTION\_STEP\_INTO|プロシージャにステップ インします。|  
|BREAKRESUMEACTION\_STEP\_OVER|プロシージャをステップ オーバーします。|  
|BREAKRESUMEACTION\_STEP\_OUT|現在のプロシージャからステップ アウトします。|  
|BREAKRESUMEACTION\_IGNORE|現在の状態での実行を継続します。|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|次のドキュメントに移動します。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)