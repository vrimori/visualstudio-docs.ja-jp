---
title: '&lt;スケジュール&gt;要素 (ブートス トラップ) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccba6de5795dd461c2a68f6aeeb593314ceede09
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962483"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;スケジュール&gt;要素 (ブートス トラップ)
`Schedules`要素が含まれます`Schedule`によって定義されたコマンドで特定の時間を定義するには、要素、`Command`要素を実行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```xml
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
 `Schedules`要素の子である、`Product`要素。 各`Product`要素が 1 つだけあります`Schedules`要素。 `Schedules` 要素に属性はありません。  
  
## <a name="schedule"></a>スケジュール  
 `Schedule`要素の子である、`Schedules`要素。 A`Schedules`要素が少なくとも 1 つあります`Schedule`要素。  
  
 `Schedule` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須です。 スケジュール アイテムの名前。 これに対応して、`ScheduleName`のプロパティ、`Command`要素。 ときに、`Command`名前付きのスケジュールを参照するによって示される時にのみ実行されます`Schedule`要素。 また関連付けられるスケジュール、`FailIf`と`BypassIf`要素を指定したスケジュールで実行中にこれらの条件付きテストを制限します。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
  
 指定された`Schedule`要素には、次の子の 1 つだけ必要があります。  
  
## <a name="buildlist"></a>BuildList  
 `BuildList`要素が、インストーラーのブートス トラップ アプリケーションの開始後にすぐにコマンドを実行するように指示します。  
  
## <a name="beforepackage"></a>BeforePackage  
 `BeforePackage`要素が指定したパッケージをインストールする前にコマンドを実行するインストーラーを指示します。  
  
## <a name="afterpackage"></a>AfterPackage  
 `AfterPackage`要素が指定したパッケージをインストールした後にコマンドを実行するインストーラーを指示します。  
  
## <a name="see-also"></a>関連項目  
 [\<製品 > 要素](../deployment/product-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)