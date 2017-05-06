---
title: "&lt;customHostSpecified&gt; 要素 (Visual Studio での Office 開発)"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<customHostSpecified> 要素"
  - "<customHostSpecified> 要素"
  - "customHostSpecified 要素"
ms.assetid: 2212b7eb-bf94-4398-b9ea-0ab00203203b
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customHostSpecified&gt; 要素 (Visual Studio での Office 開発)
  `customHostSpecified` 要素は、このソリューションがスタンドアロン アプリケーションではないことを示します。  Office ソリューションには、Microsoft Office アプリケーション内でホストされるコンポーネントが含まれています。  
  
## 構文  
  
```  
<customHostSpecified />  
```  
  
## 要素と属性  
 `customHostSpecified` 要素は、Office ソリューションでは必須です。  この要素は `co.v1` 名前空間にあり、この配置がカスタム ホストの内側に配置されるコンポーネントを含んでいてスタンドアロン アプリケーションではないことを示します。  
  
 この要素は、アプリケーション マニフェスト内の最初の `<entrypoint>` 要素の子です。  その `<entrypoint>` 要素に他の子要素を含めることはできません。他の子要素を含めると、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] によって、インストール中に妥当性確認エラーが表示されます。  
  
 この要素には、属性も子要素もありません。  
  
## 使用例  
 次のコード例は、 Office ソリューションのアプリケーション マニフェスト内の `customHostSpecified` の要素を示しています。  このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」で紹介されている大きな例の一部です。  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  