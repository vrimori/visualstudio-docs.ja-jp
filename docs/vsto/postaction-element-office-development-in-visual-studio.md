---
title: "&lt;postAction&gt; 要素 (Visual Studio での Office 開発)"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<postAction> 要素"
  - "<postAction> 要素"
  - "postAction 要素"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# &lt;postAction&gt; 要素 (Visual Studio での Office 開発)
  `vstav3`  名前空間の `postAction` 要素には、配置後アクションに関連付ける `entrypoint` 要素とすべての `postActionData` 要素を格納します。これらの要素は、Office ソリューションのインストール後に実行されます。  
  
## 構文  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## 要素と属性  
 `postAction` 要素は省略可能であり、`vstav3`  名前空間にあります。 アプリケーション マニフェストには、配置後アクションごとに `postAction` 要素を 1 つ定義します。  
  
 `postAction` 要素に属性はありません。  
  
 `postAction` には、次の要素があります。  
  
### entryPoint  
 省略可能です。`vstav3`  名前空間の `entryPoint` 要素の役割については、「[&#60;entryPoints&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)」に定義しています。  
  
### postActionData  
 省略可能です。`vstav3`  名前空間の `postActionData` 要素の役割については、「[&#60;postActionData&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)」に定義しています。  
  
## 配置後アクションの例  
  
### 説明  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置する Office ソリューションに対するアプリケーション マニフェストの `postAction` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### コード  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  