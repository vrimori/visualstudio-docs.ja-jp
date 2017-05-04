---
title: "&lt;postActions&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<postActions> 要素"
  - "postActions 要素"
  - "<postActions> 要素"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActions&gt; 要素 (Visual Studio での Office 開発)
  `vstav3`  名前空間の `postActions` の要素には、Office ソリューションのインストール後に実行する配置後アクションを説明する `postAction` 要素がすべて含まれています。  
  
## 構文  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## 要素と属性  
 `postActions` 要素は省略可能であり、`vstav3`  名前空間にあります。 アプリケーション マニフェストで定義される `postActions` 要素が 1 つだけあります。  
  
 `postActions` 要素に属性はありません。  
  
 `postActions` には次の要素があります。  
  
### postAction  
 省略可能です。`vstav3`  名前空間の `postAction` 要素のロールは [&#60;postAction&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/postaction-element-office-development-in-visual-studio.md) で定義されます。  
  
## 配置後アクションの例  
  
### 説明  
 次のコード例では、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して展開した Office ソリューションのアプリケーション マニフェストにある `postActions` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  