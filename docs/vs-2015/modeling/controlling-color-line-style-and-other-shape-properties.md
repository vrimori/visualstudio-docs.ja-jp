---
title: 色、線のスタイル、およびその他のシェイプのプロパティを制御する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1722a3f8a5ff05589cfad987fff6448d44e96ec8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533876"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>色、線のスタイル、およびその他のシェイプのプロパティの管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を制御する色、線のスタイル、およびその他のシェイプのプロパティ](https://docs.microsoft.com/visualstudio/modeling/controlling-color-line-style-and-other-shape-properties)します。  
  
いくつかのシェイプのプロパティとなど、色 '公開できる' – は、図形のドメイン プロパティ リンク。 他のユーザーは、直接制御する必要があります。  
  
## <a name="exposing-a-property"></a>プロパティを公開します。  
 いくつかの色などのシェイプのプロパティは、ドメイン プロパティの値にリンクできます。  
  
 DSL 定義では、図形、コネクタ、または図クラスを選択します。 そのコンテキスト メニューで、次のように選択します。**公開されている追加**、塗りつぶしの色など、目的のプロパティをクリックしてします。  
  
 図形は、ドメイン プロパティまたはユーザーとしてプログラム コードで設定できるようになりました。  
  
## <a name="dynamically-updating-an-exposed-property"></a>公開されたプロパティを動的に更新  
 一般公開されているプロパティを別のプロパティに依存しないようにします。 たとえば、特定のドメイン プロパティが赤色にするための図形が 0 未満たい場合があります。 この依存関係を作成、[ルール](../modeling/rules-propagate-changes-within-the-model.md)します。 例えば:  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with class:  
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class CarShapeAddRule : AddRule  
 {  
 // Override the abstract method:  
 public override void ElementAdded(ElementAddedEventArgs e)  
 {  
 base.ElementAdded(e);  
 CarShape shape = e.ModelElement as CarShape;  
 Store store = shape.Store;  
 // Ignore this call if we're currently loading a model:  
 if (store.TransactionManager.CurrentTransaction.IsSerializing)   
  return;  
 Car car = shape.ModelElement as Car;  
 // Code here propagates change as required - for example:  
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;   
 }  
}  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
 protected override Type[] GetCustomDomainModelTypes()  
 {  
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
  types.Add(typeof(CarShapeAddRule));  
  // If you add more rules, list them here.   
  return types.ToArray();  
 }  
 }  
}  
```



