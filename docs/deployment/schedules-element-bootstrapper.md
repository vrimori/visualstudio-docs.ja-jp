---
title: "&lt;Schedules&gt; 要素 (ブートストラップ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> 要素 [ブートストラップ]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# &lt;Schedules&gt; 要素 (ブートストラップ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Schedules` 要素には、`Schedule` 要素が含まれます。この要素には、`Command` 要素で定義されたコマンドを実行する、具体的な時刻を定義します。  
  
## 構文  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## 要素と属性  
 `Schedules` 要素は、`Product` 要素に必須の子です。  各 `Product` 要素は、最大で 1 つの `Schedules` 要素を持つことができます。  `Schedules` 要素に属性はありません。  
  
## Schedule  
 `Schedule` 要素は、`Schedules` 要素に必須の子です。  1 つの `Schedules` 要素には、少なくとも 1 つの `Schedule` 要素が必要です。  
  
 `Schedule` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Name`|必ず指定します。  スケジュール項目の名前です。  この値は、`Command` 要素の `ScheduleName` プロパティに対応します。  `Command` が名前付きスケジュールを参照している場合、`Schedule` 要素で指定された時間にのみ実行されます。  スケジュールは、`FailIf` 要素および `BypassIf` 要素と関連付けることもできます。この場合、これらの条件テストは、指定したスケジュールに対してのみ行われます。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
  
 指定した `Schedule` 要素には、次の子のうち 1 つだけを指定できます。  
  
## BuildList  
 `BuildList` 要素は、ブートストラップ アプリケーションが起動した直後にコマンドを実行するように、インストーラーに指示します。  
  
## BeforePackage  
 `BeforePackage` 要素は、指定したパッケージをインストールする前にコマンドを実行するように、インストーラーに指示します。  
  
## AfterPackage  
 `AfterPackage` 要素は、指定したパッケージをインストールした後でコマンドを実行するように、インストーラーに指示します。  
  
## 参照  
 [\<Product\> 要素](../deployment/product-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)