---
title: "GetVstoSolutionMetadata 関数"
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
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# GetVstoSolutionMetadata 関数
  この API は、Office のインフラストラクチャをサポートします。コードから直接使用するためのものではありません。  
  
## 構文  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*lpwszSolutionMetadataKey*|使用しないでください。|  
|*ppSolutionInfo*|使用しないでください。|  
  
## 戻り値  
 関数が正常終了すると、**S\_OK**を返します。  関数が失敗した場合はエラー コードを返します。  
  
  