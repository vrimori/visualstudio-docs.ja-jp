---
title: UML モデル内の要素および関係の作成 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 55d1a54fad3a420c60cf69bc93d29a675f9e802e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545492"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>UML モデル内に要素および関係を生成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[で UML モデル要素および関係を作成する](https://docs.microsoft.com/visualstudio/modeling/create-elements-and-relationships-in-uml-models)します。  
  
Visual Studio の拡張機能のプログラム コードでは、要素とリレーションシップを作成および削除できます。  
  
## <a name="create-a-model-element"></a>モデル要素の作成  
  
### <a name="namespace-imports"></a>名前空間のインポート  
 次の `using` ステートメントを含める必要があります。  
  
 作成 メソッドは、この名前空間の拡張メソッドとして定義されます。  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>作成する要素の所有者を取得します。  
 モデルのルートを除いて、項目ごとに 1 つの所有者があるように、モデルは 1 つのツリーで形成されています。 モデルのルートは `IModel` 型です。これは `IPackage` の型です。  
  
 たとえばユーザーの現在のダイアグラムなど、特定のダイアグラムに表示される要素を作成する場合、通常はそのダイアグラムとリンクしているパッケージ内に作成する必要があります。 例:  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 次の表は、共通のモデル要素の所有権をまとめたものです。  
  
|作成する要素|Owner|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>所有者に対して Create メソッドを呼び出す  
 形式は、メソッド名: `Create` *OwnedType*`()`します。 例えば:  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 特にシーケンス図では、型によっては作成方法がより複雑になります。 参照してください[UML API を使用して編集 UML シーケンス図](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)します。  
  
 要素の型によっては、`SetOwner(newOwner)` を使用して、存続期間中に要素の所有者を変更できます。  
  
### <a name="set-the-name-and-other-properties"></a>名前とその他のプロパティの設定  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>例  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>アソシエーションの作成  
  
#### <a name="to-create-an-association"></a>アソシエーションを作成するには  
  
1.  アソシエーションの所有者を取得します。通常、これはリレーションシップのソース エンドを含むパッケージまたはモデルになります。  
  
2.  所有者に対して必要な Create メソッドを呼び出します。  
  
3.  リレーションシップのプロパティ (名前など) を設定します。  
  
     例:  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4.  リレーションシップの両方の側のプロパティを設定します。 常に 2 つの `MemberEnds` があります。 例:  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>汎化の作成  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>モデルから要素、リレーションシップ、または汎化を削除する  
  
```  
anElement.Delete();  
```  
  
 モデルから要素を削除する場合:  
  
-   要素にリンクしているすべてのリレーションシップも削除されます。  
  
-   ダイアグラムに表されるすべての図形も削除されます。  
  
## <a name="see-also"></a>関連項目  
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [図に UML モデルを表示する](../modeling/display-a-uml-model-on-diagrams.md)



