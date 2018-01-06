---
title: "要素のツールをカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 2571fd137875a0971b7a9e4364849a3105ca220a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-element-tools"></a>要素ツールのカスタマイズ
一部の DSL 定義では、要素のグループとして 1 つの概念を表します。 たとえば、コンポーネントが固定ポートのセットを含むでモデルを作成すると、常に場合、親コンポーネントと同時に作成するポートします。 そのため、1 つだけではなく要素のグループを作成する、要素の作成ツールをカスタマイズする必要があります。 これを実現するには、要素の作成ツールを初期化する方法をカスタマイズできます。  
  
 ツールが、図または要素にドラッグされたときの動作を上書きすることもできます。  
  
## <a name="customizing-the-content-of-an-element-tool"></a>要素ツールの内容をカスタマイズします。  
 各要素のツールのインスタンスを格納する、 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) を含むモデル要素とリンクの 1 つまたは複数のシリアル化されたバージョンです。 既定では、要素ツールの EGP には、このツールの指定したクラスの 1 つのインスタンスが含まれています。 これを変更するにはオーバーライドすることで*YourLanguage*`ToolboxHelper.CreateElementToolPrototype`です。 DSL パッケージが読み込まれるときに、このメソッドが呼び出されます。  
  
 メソッドのパラメーターは、DSL 定義で指定したクラスの ID です。 興味のあるクラスにメソッドが呼び出されると、EGP に余分な要素を追加できます。  
  
 EGP では、1 つの主な要素から下位の要素へのリンクの埋め込みを含める必要があります。 参照先のリンクを含めることもできます。  
  
 次の例では、主な要素と埋め込みの 2 つの要素を作成します。 ターミナルをという名前の要素を 2 つの埋め込みリレーションシップがあるし、メイン クラスを抵抗と呼びます。 埋め込みのロールのプロパティの名前は Terminal1 Terminal2、いて両方 1..1 の多重度。  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>参照  
 [要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)