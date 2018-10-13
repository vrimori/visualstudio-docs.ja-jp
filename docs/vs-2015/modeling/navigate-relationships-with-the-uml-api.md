---
title: UML API を使用したリレーションシップの移動 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c2d4365cefc33b81f8df3891b860e254c7dc6b8b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242503"
---
# <a name="navigate-relationships-with-the-uml-api"></a>UML API を使用して関係をナビゲートする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

モデルは、さまざまな種類のリレーションシップで相互にリンクされた要素で構成されます。 このトピックでは、プログラム コードでモデルを移動する方法について説明します。  
  
## <a name="traversing-relationships"></a>リレーションシップの走査  
  
### <a name="any-relationship"></a>任意のリレーションシップ  
 `GetRelatedElements<T>()` を使用して、指定された要素に接続されたすべての要素を見つけます。 `T` を `IRelationship` に設定してあらゆる種類のリレーションシップを走査するか、`IAssociation` など具体的な種類を使用してその型だけを走査します。  
  
```  
IElement anElement;  
// Select all elements related to anElement.  
Context.CurrentDiagram.SelectShapes (  
   anElement.GetRelatedElements<IRelationship>()  
    .SelectMany(e=>e.Shapes()).ToArray());  
  
```  
  
 要素に接続されたすべてのリレーションシップを見つけるには `GetRelatedLinks<T>()` を使用します。  
  
```  
// Process all relationships connected to an element.  
foreach (IRelationship relationship in   
   anElement.GetRelatedLinks<IRelationship>())  
{  
  Debug.Assert(relationship.SourceElement == anElement  
      || relationship.TargetElement == anElement);  
}  
  
```  
  
### <a name="association"></a>関連付け  
 関連付けとは、それぞれが分類子に属している 2 つのプロパティ間のリレーションシップのことです。  
  
```  
IClassifier classifier; // class, interface, component, actor, ...  
// Get all the associations sourced from this classifier  
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())  
{  
  // p represents the end further end of an association.  
  IType oppositeElement = p.Type;   
    // The type to which this association connects classifier  
  
  IProperty oppositeProperty = p.Opposite;  
    // The nearer end of the association.  
  Debug.Assert(oppositeProperty.Type == classifier);  
  IAssociation association = p.Association;  
  Debug.Assert(association.MemberEnds.Contains(p)  
     && association.MemberEnds.Contains(oppositeProperty));  
}  
```  
  
### <a name="generalization-and-realization"></a>汎化および実現  
 汎化の両端：  
  
```  
foreach (IClassifier supertype in classifier.Generals) {…}  
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}  
Access the relationship itself:  
foreach (IGeneralization gen in classifier.Generalizations)   
{ Debug.Assert(classifier == gen.Specific); }  
```  
  
```  
  
/// InterfaceRealization:  
IEnumerable<IInterface> GetRealizedInterfaces  
    (this IBehavioredClassifier classifier);  
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers  
    (this IInterface interface);  
  
```  
  
### <a name="dependency"></a>依存関係  
  
```  
/// Returns the elements depending on this element  
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);   
/// Returns the elements this element depends on  
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);  
  
```  
  
### <a name="activity-edge"></a>アクティビティ エッジ  
  
```  
/// Returns the nodes targeted by edges outgoing from this one  
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);  
/// Returns the nodes sourcing edges incoming to this one  
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);  
  
```  
  
### <a name="connector-assembly-and-delegation"></a>コネクタ (アセンブリと委任)   
  
```  
/// Returns the elements connected via assembly   
/// or delegation to this one  
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);  
  
```  
  
### <a name="messages-and-lifelines"></a>メッセージと生存線  
  
```  
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);   
// both from lifeline and execution occurrences  
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);  
ILifeline GetSourceLifeline(this IMessage message);   
    // may return null for found messages  
ILifeline GetTargetLifeline(this IMessage message);    
    // may return null for lost messages  
  
```  
  
### <a name="package-import"></a>パッケージ インポート  
  
```  
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);  
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);  
  
```  
  
### <a name="use-case-extend-and-include"></a>ユース ケースの拡張と包含  
  
```  
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);  
```  
  
## <a name="enumerating-relationships"></a>リレーションシップの列挙  
 複数の値を返す UML モデルのすべてのプロパティは、IEnumerable <> インターフェイスに準拠します。 つまり、使用[Linq クエリ式](http://go.microsoft.com/fwlink/?LinkId=168834)で定義されている拡張メソッドと、 **System.Linq**名前空間。  
  
 例えば:  
  
```  
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()  
where shape.Color == System.Drawing.Color.Red  
select shape.Element  
  
```  
  
## <a name="see-also"></a>関連項目  
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [UML モデル内を移動する](../modeling/navigate-the-uml-model.md)



