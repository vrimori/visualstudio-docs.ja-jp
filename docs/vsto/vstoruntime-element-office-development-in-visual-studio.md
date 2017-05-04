---
title: "&lt;vstoRuntime&gt; 要素 (Visual Studio での Office 開発) | Microsoft Docs"
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
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]、<vstoRuntime> 要素"
  - "<vstoRuntime> 要素"
  - "vstoRuntime 要素"
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# &lt;vstoRuntime&gt; 要素 (Visual Studio での Office 開発)
  `vstav3`  名前空間の `vstoRuntime` 要素は、特定の Office ソリューション用の、Visual Studio Tools for Office ランタイムのサポートされるバージョンを格納します。  
  
## 構文  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## 要素と属性  
 `vstoRuntime` 要素は必須です。この要素は `vstav3`  名前空間にあります。 Office ソリューションが 2 つのバージョンの Visual Studio Tools for Office ランタイムをサポートする場合、アプリケーション マニフェストには 2 つの `vstoRuntime` 要素があります。  
  
 `vstoRuntime` 要素には、次の属性があります。  
  
|属性|説明|  
|--------|--------|  
|`release`|必須です。 Visual Studio Tools for Office ランタイムのリリース バージョン。|  
|`version`|必須です。 Visual Studio Tools for Office ランタイムのバージョン番号。|  
|`supportUrl`|省略可能です。 Visual Studio Tools for Office ランタイムのインストール場所へのリンク。|  
  
 `vstoRuntime` には要素がありません。  
  
## 使用例  
 次のコード例は、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] を使用して配置する Office ソリューションに対するアプリケーション マニフェストの `vstoRuntime` 要素を示しています。 このコード例は、「[Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
```  
<vstav3:vstoRuntime release="VSTOR40Beta1" version="10.0.20303" supportUrl="http://www.microsoft.com" />  
```  
  
## 参照  
 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  