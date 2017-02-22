---
title: "&lt;customErrorReporting&gt; 要素 (ClickOnce 配置) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> 要素 [ClickOnce 配置マニフェスト]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;customErrorReporting&gt; 要素 (ClickOnce 配置)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エラー発生時に表示する URI を指定します。  
  
## 構文  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## 解説  
 この要素は省略可能です。  指定しない場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] はエラー ダイアログ ボックスを開き、例外のスタックを表示します。  `customErrorReporting` 要素が指定されていると、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は `uri` パラメーターで指定されている URI を表示します。  対象の URI には、パラメーターとして外部の例外クラス、内部の例外クラス、および内部の例外メッセージが含まれます。  
  
 アプリケーションにエラー レポート機能を追加するには、この要素を使用します。  生成される URI にはエラーの種類に関する情報が含まれているため、Web サイトでその情報を解析し、適切なトラブルシューティング画面などを表示できます。  
  
## 使用例  
 `customErrorReporting` 要素と、生成される可能性のある URI を示すスニペットを次に例示します。  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## 参照  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)