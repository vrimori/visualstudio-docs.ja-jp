---
title: '&lt;スケジュール&gt;要素 (ブートス トラップ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2b3cba1fcb5ac2d38b08383c8906adb2037e9651
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
 `Schedule` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 スケジュール アイテムの名前。 これに対応して、`ScheduleName`のプロパティ、`Command`要素。 ときに、`Command`名前付きのスケジュールを参照しているによって示される時にのみ実行されます`Schedule`要素。 また関連付けられるスケジュール、`FailIf`と`BypassIf`要素で、指定したスケジュールで実行中にこれらの条件付きのテストを制限します。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)です。|  
  
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