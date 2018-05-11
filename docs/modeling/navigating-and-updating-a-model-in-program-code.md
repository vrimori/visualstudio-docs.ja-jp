---
title: プログラム コードにおけるモデル内の移動およびモデルの更新
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7e98be1dd16705be00f388419013686f861f3753
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="navigate-and-update-a-model-in-program-code"></a>移動し、プログラム コードでモデルを更新します

作成およびモデル要素を削除、プロパティの設定、および作成、要素間のリンクを削除するコードを記述することができます。 トランザクション内ですべての変更を加える必要があります。 要素は、ダイアグラムで表示され場合の図は、「修正されます」自動的に、トランザクションの終了時。

## <a name="in-this-topic"></a>このトピックの内容
 [DSL 定義の例](#example)

 [モデルを移動します。](#navigation)

 [クラスの情報にアクセスします。](#metadata)

 [トランザクション内の変更を実行します。](#transaction)

 [モデル要素を作成します。](#elements)

 [リレーションシップ リンクの作成](#links)

 [要素を削除します。](#deleteelements)

 [リレーションシップ リンクの削除](#deletelinks)

 [リレーションシップのリンクの並べ替え](#reorder)

 [ロック](#locks)

 [コピーと貼り付け](#copy)

 [移動して、ダイアグラムの更新](#diagrams)

 [図形と要素間を移動します。](#views)

 [図形とコネクタのプロパティ](#shapeProperties)

 [DocView と DocData](#docdata)

##  <a name="example"></a> DSL 定義の例
 これは、このトピックの例として DslDefinition.dsl の主要部分です。

 ![DSL 定義ダイアグラム&#45;ファミリ ツリー モデル](../modeling/media/familyt_person.png "FamilyT_Person")

 このモデルでは、この DSL のインスタンスを示します。

 ![Tudor ファミリ ツリー モデル](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>参照と名前空間
 このトピックのコードを実行するを参照する必要があります。

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 コードには、この名前空間で使用します。

 `using Microsoft.VisualStudio.Modeling;`

 さらに、DSL が定義されている 1 つから別のプロジェクトで、コードを記述する場合は、Dsl プロジェクトによってビルドされたアセンブリをインポートする必要があります。

##  <a name="navigation"></a> モデルを移動します。

### <a name="properties"></a>プロパティ
 DSL 定義で定義したドメインのプロパティでは、プログラム コードでアクセスできるプロパティになります。

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 プロパティを設定する場合は、行う必要があります内、[トランザクション](#transaction):

 `henry.Name = "Henry VIII";`

 DSL 定義で、プロパティの場合**種類**は**Calculated**、設定することはできません。 詳細については、次を参照してください。[記憶域のカスタム プロパティして計算された](../modeling/calculated-and-custom-storage-properties.md)です。

### <a name="relationships"></a>リレーションシップ
 DSL 定義に定義しているドメイン リレーションシップでは、1 つは、リレーションシップの両端にクラス プロパティのペアになります。 プロパティの名前は、リレーションシップの両側に、役割のラベルとして DslDefinition ダイアグラムに表示されます。 ロールの多重度、に応じてプロパティの型は、リレーションシップのもう一方の端にクラスまたはそのクラスのコレクションのいずれかです。

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 リレーションシップのもう一方の端にあるプロパティは常に逆数。 リンクを作成または削除すると、両方の要素のロールのプロパティが更新されます。 次の式 (の拡張機能を使用する`System.Linq`) は常に、例では、ParentsHaveChildren リレーションシップの true:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**です。 リレーションシップがモデル要素と呼ばれるによっても表されます、*リンク*、これは、ドメイン リレーションシップの種類のインスタンス。 常に、リンクは、1 つのソース要素と 1 つのターゲット要素を持ちます。 ソース要素とターゲット要素を同じにすることができます。

 リンクとそのプロパティにアクセスできます。

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 既定では、リレーションシップの 2 つ以上のインスタンスが許可されたモデル要素のすべてのペアをリンクします。 DSL 定義である場合は、`Allow Duplicates`フラグは、リレーションシップを true に設定し、1 つ以上のリンクがある可能性があります、使用する必要があります`GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 リンクにアクセスするためには、その他の方法もあります。 例えば:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **非表示の役割です。** DSL 定義の場合**プロパティが生成**は**false**で特定のロール、プロパティは生成されませんそのロールに対応します。 ただし、引き続きリンクにアクセスして、リレーションシップのメソッドを使用してリンクを通過します。

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 最もよく使用される例は、<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>ダイアグラムに表示される図形からモデル要素へのリンク関係。

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>要素ディレクトリ
 要素のディレクトリを使用して、ストア内のすべての要素を表示できます。

 `store.ElementDirectory.AllElements`

 次などの要素を検索するための方法もあります。

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

##  <a name="metadata"></a> クラスの情報にアクセスします。
 クラス、リレーションシップ、および DSL 定義の他の側面についての情報を取得することができます。 例えば:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 モデル要素の先祖のクラスは次のとおりです。

-   ModelElement - すべての要素および関係は、モデル要素

-   ElementLink - すべてのリレーションシップは ElementLinks

##  <a name="transaction"></a> トランザクション内の変更を実行します。
 ストアでは何も、プログラム コードが変わるたびに、トランザクション内行うがあります。 これは、すべてのモデル要素、リレーションシップ、図形、図、およびそのプロパティに適用されます。 詳細については、「<xref:Microsoft.VisualStudio.Modeling.Transaction>」を参照してください。

 トランザクションを管理するための最も便利な方法は、`using`ステートメントで囲む、`try...catch`ステートメント。

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 任意の数の 1 つのトランザクションの内部で変更を行うことができます。 アクティブなトランザクション内で新しいトランザクションを開くことができます。

 変更を恒久的なようにするには`Commit`トランザクションが破棄される前にします。 トランザクション内でキャッチされない例外が発生した場合、ストアは、変更前に、の状態にリセットされます。

##  <a name="elements"></a> モデル要素を作成します。
 この例では、既存のモデル要素を追加します。

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 この例では、要素の作成について、次の重要な点を示します。

-   ストアの特定のパーティションで、新しい要素を作成します。 モデル要素と、リレーションシップがない図形、これは通常、既定のパーティションです。

-   埋め込みリレーションシップの対象となります。 この例の DslDefinition、各ユーザーは埋め込みリレーションシップ FamilyTreeHasPeople のターゲットをする必要があります。 これを実現するには、するには、Person オブジェクトの FamilyTreeModel ロールのプロパティを設定おか、FamilyTreeModel オブジェクトのユーザー ロールのプロパティにユーザーを追加します。

-   対象のプロパティでは特に、新しい要素のプロパティを設定`IsName`DslDefinition に当てはまります。 このフラグは、その所有者内で一意に要素を識別するプロパティをマークします。 この場合、名前プロパティには、そのフラグがあります。

-   この DSL の DSL 定義は、ストアに読み込まれている必要があります。 メニュー コマンドなどの拡張機能を作成している場合は、この通常は既に true です。 その他の場合は、明示的に、モデルの読み込み、ストアにしたり、使用<xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>ファイルを読み込むことです。 詳細については、次を参照してください。[する方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)です。

 この方法で要素を作成するときに (DSL に図がある場合)、図形が自動的に作成します。 既定の図形、色、およびその他の機能と、自動的に割り当てられる場所に表示されます。 参照してください、関連付けられた図形が表示される場所と方法を制御する場合[要素とその図形を作成する](#merge)です。

##  <a name="links"></a> リレーションシップ リンクの作成
 DSL 定義の例で定義されている 2 つのリレーションシップがあります。 各リレーションシップを定義、*ロール プロパティ*リレーションシップの両端にあるクラスにします。

 リレーションシップのインスタンスを作成できる 3 つの方法があります。 これら 3 つのメソッドのそれぞれは、同じ効果があります。

-   ソース ロール プレーヤーのプロパティを設定します。 例えば:

    -   `familyTree.People.Add(edward);`

    -   `edward.Parents.Add(henry);`

-   ターゲット ロール プレーヤーのプロパティを設定します。 例えば:

    -   `edward.familyTreeModel = familyTree;`

         このロールの多重度が`1..1`ので、値を割り当てます。

    -   `henry.Children.Add(edward);`

         このロールの多重度が`0..*`のため、コレクションに追加しました。

-   リレーションシップのインスタンスを明示的に作成します。 例えば:

    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

 最後のメソッドは、リレーションシップ自体のプロパティを設定する場合に便利です。

 この方法で要素を作成するときに、図上のコネクタが自動的に作成するが既定の図形、色、およびその他の機能があります。 関連するコネクタを作成する方法を制御するを参照してください。[要素とその図形を作成する](#merge)です。

##  <a name="deleteelements"></a> 要素を削除します。
 呼び出すことにより、要素を削除`Delete()`:

 `henry.Delete();`

 この操作も削除されます。

-   要素との間のリレーションシップ リンクします。 たとえば、`edward.Parents`含まれなくなります`henry`です。

-   対象のロールにある要素、`PropagatesDelete`フラグが true です。 たとえば、要素を表示する図形が削除されます。

 既定では、各埋め込みリレーションシップが`PropagatesDelete`ターゲット ロールの場合は true です。 削除する`henry`は削除されません、`familyTree`が`familyTree.Delete()`すべてを削除、`Persons`です。 詳細については、次を参照してください。[削除の動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)です。

 既定では、`PropagatesDelete`参照リレーションシップのロールには当てはまりません。

 オブジェクトを削除する場合は、特定の伝達を省略する削除ルールが発生することができます。 これは、別の 1 つの要素を置換する場合に便利です。 1 つ以上のロールを削除する必要があります伝達できませんの GUID を指定します。 GUID は、リレーションシップ クラスから取得できます。

 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

 (この例の効果はありません、ため`PropagatesDelete`は`false`の役割に対して、`ParentsHaveChildren`リレーションシップです)。

 場合によっては、要素または伝達によって削除される要素のいずれか、ロックの存在によって削除が回避されます。 使用することができます`element.CanDelete()`要素を削除できるかどうかを確認します。

##  <a name="deletelinks"></a> リレーションシップ リンクの削除
 リレーションシップ リンクを削除するには、ロールのプロパティから要素を削除します。

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 リンクを明示的にも削除できます。

 `edwardHenryLink.Delete();`

 これら 3 つのメソッドには、同じ効果があります。 これらのいずれかを使用する必要があるだけです。

 役割に 0..1 または 1..1 の多重度がある場合に設定できます`null`、または別の値にします。

 `edward.FamilyTreeModel = null;` または。

 `edward.FamilyTreeModel = anotherFamilyTree;`

##  <a name="reorder"></a> リレーションシップのリンクの順序を変更
 ソースまたは特定のモデル要素を対象とされている特定の関係のリンクでは、特定のシーケンスがあります。 追加された順序で表示されます。 たとえば、このステートメントは常に同じ順序で子を生成します。

 `foreach (Person child in henry.Children) ...`

 リンクの順序を変更することができます。

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

##  <a name="locks"></a> ロック
 変更内容は、ロックによってできない可能性があります。 個々 の要素、パーティション、およびストアのロックを設定できます。 変更の種類を防止するロックを持つこれらのレベルのいずれかの場合は、試行したときに例外がスロー可能性があります。 ロックは、要素を使用して設定するかどうかを検出できます。名前空間で定義されている拡張メソッドである GetLocks()<xref:Microsoft.VisualStudio.Modeling.Immutability>です。

 詳細については、次を参照してください。[に読み取り専用セグメントを作成するロックのポリシーを定義する](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)です。

##  <a name="copy"></a> コピーと貼り付け
 要素または要素のグループにコピーすることができます、 <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 要素は、シリアル化された要素のグループとして保存されます。

 IDataObject からの要素は、モデルにマージできます。

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` いずれかを受け取ることができます、`PresentationElement`または`ModelElement`です。 指定した場合、 `PresentationElement`、3 番目のパラメーターとしてコピー先のダイアグラムでの位置を指定することもできます。

##  <a name="diagrams"></a> 移動して、ダイアグラムの更新
 DSL で、個人または曲などの概念を表す、ドメイン モデル要素とは別をダイアグラムに表示されるものを表す図形要素には。 ドメイン モデル要素には、重要なプロパティおよび概念の関係が格納されます。 図形要素は、サイズ、位置とダイアグラムで、オブジェクトの表示の色、およびその構成部分のレイアウトを格納します。

### <a name="presentation-elements"></a>プレゼンテーション要素
 ![基本図形および要素の型のクラス ダイアグラム](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")

 DSL 定義では、指定した各要素は、標準的なクラスを次のいずれかから派生したクラスを作成します。

|要素の種類|基底クラス|
|---------------------|----------------|
|ドメイン クラス|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|ドメインの関係|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|形式|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|コネクタ|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|図|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 図の要素は、通常、モデル要素を表します。 通常 (必ずではありませんが)、<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>ドメイン クラスのインスタンスを表す、<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>ドメイン リレーションシップ インスタンスを表します。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>リレーションシップが、そのモデル要素にノードまたはリンクの図形をリンクします。

 すべてのノードまたはリンクの図形は、1 つの図に属しています。 バイナリ リンク図形は、2 つのノードの図形を接続します。

 図形は、2 つのセットで子シェイプを持つことができます。 内の図形、`NestedChildShapes`セットは、その親の境界ボックスに限定します。 内の図形、`RelativeChildShapes`一覧がラベルやポートなどの親の範囲外外側または一部を表示できます。 ダイアグラムを持たない`RelativeChildShapes`および no`Parent`です。

###  <a name="views"></a> 図形と要素間を移動します。
 ドメイン モデル要素と図形要素で関連付けられた、<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>リレーションシップです。

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 同じリレーションシップをリンクを図上のコネクタに関係しています。

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 このリレーションシップでは、図に、モデルのルートもリンクします。

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 図形によって表されるモデル要素を取得するには、次のコマンドを使用します。

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>ダイアグラム上で移動します。
 一般に上の図は、図形やコネクタ間を移動することをお勧めはできません。 ダイアグラムの外観に使用する必要がある場合にのみ、図形とコネクタの間で移動、モデルでリレーションシップをナビゲートすることをお勧めします。 これらのメソッドは、コネクタをそれぞれの側での図形にリンクします。

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 多くの図形が合成です。構成親シェイプと子の 1 つまたは複数のレイヤー。 別の形を基準に配置した図形と呼ばれますその*子*です。 親シェイプを動かすと、子はそのと共に移動します。

 *相対的な子*親シェイプの境界ボックス外に置くことができます。 *入れ子になった*子は、親の境界内にのみが表示されます。

 ダイアグラムで図形の最上位のセットを取得するには、次のように使用します。

 `Diagram.NestedChildShapes`

 図形とコネクタの親クラスがあります。

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

###  <a name="shapeProperties"></a> 図形とコネクタのプロパティ
 ほとんどの場合は、図形に明示的な変更を加える必要はありません。 モデル要素を変更したときに、「修正」ルールは、図形とコネクタを更新します。 詳細については、次を参照してください。[への応答と変更を反映する](../modeling/responding-to-and-propagating-changes.md)です。

 ただしは、モデル要素に依存しないプロパティ内の図形にいくつかの明示的な変更を加えることをお勧めします。 たとえば、これらのプロパティを変更する可能性があります。

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -形状の幅と高さを決定します。

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -親図形または図に対する相対的な位置

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -一連のペンや図形またはコネクタを描画するために使用されるブラシ

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> 図形を非表示にします。

-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> 図形の後に表示します。 `Hide()`

###  <a name="merge"></a> 要素とその図形を作成します。
 要素を作成するリレーションシップの埋め込みのツリーにリンクすると、図形が自動的に作成され、関連付けられています。 これは、トランザクションの最後に実行する「修正」規則を実行します。 ただし、図形は、自動的に割り当てられている場所に表示されます、形状、色、およびその他の機能が既定値です。 図形を作成する方法を制御するには、マージ関数を使用できます。 最初、ElementGroup に追加する要素を追加し、図に、グループをマージする必要があります。

 この方法では:

-   要素名としてプロパティを割り当てた場合は、名前を設定します。

-   DSL 定義で指定した要素をマージ ディレクティブすべてを監視します。

 この例では、ユーザーの図をダブルクリックしたときにマウスの位置に図形を作成します。 このサンプルでは、DSL 定義で、`FillColor`プロパティ`ExampleShape`公開されています。

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 複数の図形を指定した場合を使用してそれらの相対位置を設定、`AbsoluteBounds`です。

 色、このメソッドを使用してコネクタの公開されている他のプロパティを設定することもできます。

### <a name="use-transactions"></a>トランザクションを使用して
 図形、コネクタと図がのサブタイプ<xref:Microsoft.VisualStudio.Modeling.ModelElement>とストアでライブします。 トランザクション内でのみに変更を行う必要がありますのでです。 詳細については、次を参照してください。[する方法: モデルを更新するトランザクションを使用して](../modeling/how-to-use-transactions-to-update-the-model.md)です。

##  <a name="docdata"></a> ドキュメント ビューとドキュメントのデータ
 ![標準タイプのクラス ダイアグラム](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>パーティションを格納します。
 モデルが読み込まれるときに、同時に付随する図が読み込まれます。 通常、Store.DefaultPartition に、モデルが読み込まれ、ダイアグラムの内容が別のパーティションに読み込まれます。 通常、各パーティションのコンテンツが読み込まれ、別のファイルに保存されます。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)
- [ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)
- [方法: トランザクションを使用してモデルを更新する](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Visual Studio Modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)
