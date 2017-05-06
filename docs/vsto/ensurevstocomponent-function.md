---
title: "EnsureVSTOComponent 関数"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# EnsureVSTOComponent 関数
  この API は、Office のインフラストラクチャをサポートします。コードから直接使用するためのものではありません。  
  
## 構文  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*pProject*|使用しないでください。|  
  
## 戻り値  
 関数が正常終了すると、**S\_OK**を返します。  関数が失敗した場合はエラー コードを返します。  
  
  