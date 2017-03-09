---
title: "Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_EXTPROVINVALID"
ms.assetid: 77d596cd-28db-4ad5-bd4d-e451276e869c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Extender Provider doesn&#39;t support either the IExtenderProvider or the IExtenderProviderUnk interfaces.
使用中の拡張プロバイダーは、実装したインターフェイスをサポートしていません。  
  
### このエラーを解決するには  
  
1.  Extendee オブジェクトが IDispatch オートメーション インターフェイスをサポートしている場合は、IExtenderProvider を実装します。  
  
     または  
  
     Extendee オブジェクトが IUnknown を基にしている場合は、IExtenderProviderUnk を実装します。  
  
## 参照  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>