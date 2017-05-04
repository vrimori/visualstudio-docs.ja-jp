---
title: "&lt;update&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
helpviewer_keywords: 
  - "update 要素"
  - "<update> 要素"
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<update> 要素"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# &lt;update&gt; 要素 (Visual Studio での Office 開発)
  `update` 要素は、ソリューションが更新プログラムを確認する間隔を指定します。  
  
## 構文  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## 要素と属性  
 `update` 要素は必須です。この要素は `vstav3` 名前空間にあります。  
  
 `update` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`enabled`|必ず指定します。  enabled には、次のいずれかの値を設定します。<br /><br /> -   更新プログラムを確認する場合は **true** を設定します。<br />-   更新プログラムを確認しない場合は **false** を設定します。|  
  
 `update` 要素には、次の子要素があります。  
  
### expiration  
 `expiration` 要素は必須です。この要素は `vstav3` 名前空間にあります。  この要素は、ソリューションが更新プログラムを確認する間隔を指定します。  
  
 `expiration` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`maximumAge`|-   必ず指定します。  この値は整数に設定します。|  
|`unit`|必ず指定します。  `unit` には、次のいずれかの値を設定します。<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## 常に更新プログラムを確認する例  
  
### Description  
 次のコード例は、Office ソリューションの更新プログラムを常に確認するように設定された `update` 要素を示しています。  
  
### コード  
  
```  
<vstav3:update enabled="true" />  
```  
  
## 既定の更新間隔を設定する例  
  
### Description  
 次のコード例は、Office ソリューションのアプリケーション マニフェスト内の `update` 要素を示しています。  このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」で紹介されている大きな例の一部です。  
  
### コード  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## 参照  
 [ClickOnce を使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  