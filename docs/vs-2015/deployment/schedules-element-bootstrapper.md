---
title: '&lt;スケジュール&gt;要素 (ブートス トラップ) |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c72ee64bcc174bcd11d800bbc8dd0e1b9848b746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540042"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;スケジュール&gt;要素 (ブートス トラップ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[&lt;スケジュール&gt;要素 (ブートス トラップ)](https://docs.microsoft.com/visualstudio/deployment/schedules-element-bootstrapper)します。  
  
`Schedules`要素が含まれます`Schedule`によって定義されたコマンドで特定の時間を定義するには、要素、`Command`要素を実行する必要があります。  
  
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
 `Schedules`要素の子である、`Product`要素。 各`Product`要素が 1 つだけあります`Schedules`要素。 `Schedules`要素に属性がありません。  
  
## <a name="schedule"></a>スケジュール  
 `Schedule`要素の子である、`Schedules`要素。 A`Schedules`要素が少なくとも 1 つあります`Schedule`要素。  
  
 `Schedule` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Name`|必須。 スケジュール アイテムの名前。 これに対応して、`ScheduleName`のプロパティ、`Command`要素。 ときに、`Command`名前付きのスケジュールを参照するによって示される時にのみ実行されます`Schedule`要素。 また関連付けられるスケジュール、`FailIf`と`BypassIf`要素を指定したスケジュールで実行中にこれらの条件付きテストを制限します。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
  
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



