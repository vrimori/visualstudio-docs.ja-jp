---
title: "&lt;スケジュール&gt;要素 (ブートス トラップ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: "5"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 104c187d373113e8e5dafe589af3995bef5c8cdc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;スケジュール&gt;要素 (ブートス トラップ)
`Schedules`要素が含まれます`Schedule`要素で、によって定義されたコマンドで特定の時間を定義する、`Command`要素を実行する必要があります。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `Schedules`要素の子では、`Product`要素。 各`Product`要素が 1 つだけあります`Schedules`要素。 `Schedules`要素に属性がありません。  
  
## <a name="schedule"></a>スケジュール  
 `Schedule`要素の子では、`Schedules`要素。 A`Schedules`要素が少なくとも 1 つあります`Schedule`要素。  
  
 `Schedule`次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須です。 スケジュール アイテムの名前。 これに対応して、`ScheduleName`のプロパティ、`Command`要素。 ときに、`Command`名前付きのスケジュールを参照しているによって示される時にのみ実行されます`Schedule`要素。 また関連付けられるスケジュール、`FailIf`と`BypassIf`要素で、指定したスケジュールで実行中にこれらの条件付きのテストを制限します。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
  
 指定された`Schedule`要素には、次の子の 1 つだけ必要があります。  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`要素が、インストーラーはブートス トラップ アプリケーションの起動後にすぐにコマンドを実行するように指示します。  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`要素は、指定したパッケージをインストールする前に、コマンドを実行するインストーラーを指示します。  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`要素は、指定したパッケージをインストールした後にコマンドを実行するインストーラーを指示します。  
  
## <a name="see-also"></a>関連項目  
 [\<Product > 要素](../deployment/product-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)