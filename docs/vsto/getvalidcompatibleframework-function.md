---
title: "GetValidCompatibleFramework 関数 | Microsoft Docs"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework 関数
  この API は、Office のインフラストラクチャをサポートします。コードから直接使用するためのものではありません。  
  
## 構文  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*lpwszCompatibleFrameworksXML*|使用しないでください。|  
|*pbstrValidFrameworkTag*|使用しないでください。|  
  
## 戻り値  
 関数が正常終了すると、**S\_OK**を返します。  関数が失敗した場合はエラー コードを返します。  
  
  