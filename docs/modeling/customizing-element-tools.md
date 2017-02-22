---
title: "要素ツールのカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
caps.handback.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 要素ツールのカスタマイズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

一部の DSL 定義では、要素のグループとして 1 つの概念を表します。 たとえば、コンポーネントが固定ポートのセットを持つモデルを作成する場合する場合に、親コンポーネントと同時に作成するポート。 そのため、1 つだけでなく、要素のグループが作成されるように要素の作成ツールをカスタマイズする必要があります。 これを実現するのには、要素の作成ツールを初期化する方法をカスタマイズできます。  
  
 また、ツールは、図または要素にドラッグされるときの動作をオーバーライドすることができます。  
  
## 要素ツールの内容をカスタマイズします。  
 各要素ツールのインスタンスを格納する、 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\) を含むモデル要素およびリンクの 1 つまたは複数のシリアル化されたバージョンです。 既定では、要素ツールの EGP には、このツールの指定したクラスの 1 つのインスタンスが含まれています。 これを変更するにはオーバーライドすることで *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`します。 DSL パッケージが読み込まれるときに、このメソッドが呼び出されます。  
  
 メソッドのパラメーターは、DSL 定義で指定したクラスの ID です。 興味のあるクラスを使用して、メソッドが呼び出されると、EGP に余分な要素を追加できます。  
  
 EGP では、1 つの主要な要素に付属の要素へのリンクの埋め込みを含める必要があります。 参照リンクを含めることもできます。  
  
 次の例では、主要な要素と埋め込まれた 2 つの要素を作成します。 メイン クラスには抵抗が呼び出され、ターミナルをという名前の要素を 2 つの埋め込みリレーションシップがあります。 埋め込みのロールのプロパティの名前は Terminal1 Terminal2、いて両方 1..1 の多重度です。  
  
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
  
## 参照  
 [要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)