---
title: "ナビゲートおよびでのモデルの更新プログラムのコード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 26
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: f17f676025a19efb09184b7a49645986723cb29f
ms.lasthandoff: 02/22/2017

---
# <a name="navigating-and-updating-a-model-in-program-code"></a>プログラム コードにおけるモデル内の移動およびモデルの更新
作成しモデル要素を削除、プロパティの設定、および作成、要素間のリンクを削除するコードを記述することができます。 すべての変更は、トランザクション内で行う必要があります。 要素を図に表示する場合の図は""自動的に修正、トランザクションの終了時。  
  
## <a name="in-this-topic"></a>このトピックの内容  
 [DSL 定義の例](#example)  
  
 [モデル内の移動](#navigation)  
  
 [クラス情報へのアクセス](#metadata)  
  
 [トランザクション内の変更を加える](#transaction)  
  
 [モデル要素を作成します。](#elements)  
  
 [リレーションシップ リンクの作成](#links)  
  
 [要素を削除します。](#deleteelements)  
  
 [リレーションシップ リンクを削除します。](#deletelinks)  
  
 [リレーションシップのリンクの順序変更](#reorder)  
  
 [ロック](#locks)  
  
 [コピーと貼り付け](#copy)  
  
 [ナビゲートおよび図を更新](#diagrams)  
  
 [図形および要素間を移動します。](#views)  
  
 [図形とコネクタのプロパティ](#shapeProperties)  
  
 [DocView と DocData](#docdata)  
  
##  <a name="a-nameexamplea-an-example-dsl-definition"></a><a name="example"></a>DSL 定義の例  
 これは、このトピックの例として DslDefinition.dsl の主要部分です。  
  
 ![DSL 定義ダイアグラム - ファミリ ツリー モデル](~/docs/modeling/media/familyt_person.png "FamilyT_Person")  
  
 このモデルでは、この DSL のインスタンスを示します。  
  
 ![Tudor ファミリ ツリー モデル](~/docs/modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>参照と名前空間  
 このトピックのコードを実行するを参照する必要があります。  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 コードでは、この名前空間を使用します。  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 さらに、DSL が定義されている&1; つから別のプロジェクトで、コードを記述する場合は、Dsl プロジェクトでビルドされるアセンブリをインポートする必要があります。  
  
##  <a name="a-namenavigationa-navigating-the-model"></a><a name="navigation"></a>モデル内の移動  
  
### <a name="properties"></a>プロパティ  
 DSL 定義で定義したドメインのプロパティでは、プログラム コードで使用できるプロパティになります。  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 プロパティを設定する場合は、行う必要があります内、[トランザクション](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 DSL 定義で、プロパティの場合**種類**は**計算**、設定することはできません。 詳細については、次を参照してください。[計算し、カスタム ストレージ プロパティ](../modeling/calculated-and-custom-storage-properties.md)します。  
  
### <a name="relationships"></a>リレーションシップ  
 DSL 定義で定義したドメインの関係では、1 つは、リレーションシップの両端にクラス プロパティのペアになります。 プロパティの名前は、リレーションシップの両端でロールのラベルとして DslDefinition ダイアグラムに表示されます。 ロールの多重度、に応じてプロパティの型は、リレーションシップのもう一方の端にあるクラスまたはそのクラスのコレクションのいずれかです。  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 リレーションシップのもう一方の端にあるプロパティは常に逆数。 リンクを作成または削除すると、両方の要素のロールのプロパティが更新されます。 次の式 (の拡張機能を使用して`System.Linq`) は常に ParentsHaveChildren リレーションシップの例では true。  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**します。 リレーションシップと呼ばれるモデル要素によって表されるも、*リンク*、ドメイン リレーションシップの種類のインスタンスであります。 リンクには、必ず、1 つのソース要素と&1; つのターゲット要素があります。 ソース要素とターゲット要素を同じにすることができます。  
  
 リンクとそのプロパティにアクセスできます。  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 既定では、リレーションシップの&2; つ以上のインスタンスが許可されたモデル要素のペアをリンクします。 DSL 定義の場合は、`Allow Duplicates`フラグは、リレーションシップの場合は true、1 つ以上のリンクがある可能性があり、使用する必要があります`GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 リンクにアクセスするためには、その他の方法も。 例:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **非表示の役割です。** DSL 定義の場合**プロパティが生成**は**false**特定のロールに対して、プロパティは生成されませんそのロールに対応します。 ただし、まだリンクにアクセスしてリレーションシップのメソッドを使用してリンクを通過します。  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 最もよく使用される例は、<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>ダイアグラムに表示される図形からモデル要素へのリンク関係:</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>要素のディレクトリ  
 要素のディレクトリを使用して、ストア内のすべての要素にアクセスできます。  
  
 `store.ElementDirectory.AllElements`  
  
 次のように、要素を検索する方法もあります。  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="a-namemetadataa-accessing-class-information"></a><a name="metadata"></a>クラス情報へのアクセス  
 クラス、リレーションシップ、および DSL 定義の他の側面に関する情報を取得できます。 例:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 モデル要素の親クラスは次のとおりです。  
  
-   モデル要素のすべての要素および関係はモデル要素です。  
  
-   ElementLink - すべてのリレーションシップは ElementLinks  
  
##  <a name="a-nametransactiona-perform-changes-inside-a-transaction"></a><a name="transaction"></a>トランザクション内の変更を加える  
 ストアでは何も、プログラム コードが変わるたびに、トランザクション内は、必要があります。 これは、すべてのモデル要素、リレーションシップ、図形、図、およびそれらのプロパティに適用されます。 詳細については、 <xref:Microsoft.VisualStudio.Modeling.Transaction>。</xref:Microsoft.VisualStudio.Modeling.Transaction>を参照してください。  
  
 トランザクションを管理する最も便利なメソッドは、`using`ステートメントで囲む、`try...catch`ステートメント。  
  
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
  
 任意の数の&1; つのトランザクション内で変更を行うことができます。 アクティブなトランザクション内で新しいトランザクションを開くことができます。  
  
 永続的な変更を加える、する必要があります`Commit`が破棄される前に、トランザクションです。 トランザクション内でキャッチされない例外が発生した場合、ストアは、変更前に、の状態にリセットされます。  
  
##  <a name="a-nameelementsa-creating-model-elements"></a><a name="elements"></a>モデル要素を作成します。  
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
  
-   ストアの特定のパーティションに新しい要素を作成します。 モデル要素と関係が形状ではなく、これは通常、既定のパーティションです。  
  
-   埋め込みリレーションシップのターゲットになります。 この例の DslDefinition で各ユーザーは埋め込みリレーションシップ FamilyTreeHasPeople の対象にする必要があります。 これを実現するには、Person オブジェクトの FamilyTreeModel ロールのプロパティを設定するか、FamilyTreeModel オブジェクトのユーザー ロールのプロパティにそのユーザーを追加おことができます。  
  
-   対象のプロパティでは特に、新しい要素のプロパティを設定`IsName`DslDefinition に当てはまります。 このフラグは、その所有者内で一意に要素を識別するプロパティをマークします。 この場合は、Name プロパティには、そのフラグがいます。  
  
-   この DSL の DSL 定義は、ストアに読み込まれている必要があります。 メニュー コマンドのような拡張機能を作成している場合は、通常これは既に true です。 それ以外の場合に、明示的に、モデル、ストアへの読み込みまたは<xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>を</xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>使用してそれを読み込むことができます。 詳細については、次を参照してください。[方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)します。  
  
 この方法で要素を作成するときに (DSL に図がある場合)、図形が自動的に作成します。 既定の形状、色、およびその他の機能と、自動的に割り当てられている場所に表示されます。 参照してください、関連付けられた図形が表示される場所と方法を制御する場合[要素とその図形を作成する](#merge)です。  
  
##  <a name="a-namelinksa-creating-relationship-links"></a><a name="links"></a>リレーションシップ リンクの作成  
 DSL 定義の例で定義されている&2; つの関係があります。 各リレーションシップを定義、*ロール プロパティ*リレーションシップの両端にあるクラスにします。  
  
 リレーションシップのインスタンスを作成できる&3; つの方法はあります。 これら&3; つのメソッドのそれぞれは、同じ効果があります。  
  
-   ソース ロール プレーヤーのプロパティを設定します。 例:  
  
    -   `familyTree.People.Add(edward);`  
  
    -   `edward.Parents.Add(henry);`  
  
-   ターゲット ロール プレイヤーのプロパティを設定します。 例:  
  
    -   `edward.familyTreeModel = familyTree;`  
  
         このロールの多重度が`1..1`ので、値を代入します。  
  
    -   `henry.Children.Add(edward);`  
  
         このロールの多重度が`0..*`、ため、コレクションに追加します。  
  
-   リレーションシップのインスタンスを明示的に作成します。 例:  
  
    -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
    -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
 最後のメソッドは、リレーションシップ自体のプロパティを設定する場合に便利です。  
  
 この方法で要素を作成するときは、図上のコネクタが自動的に作成するは、既定の図形、色、およびその他の機能があります。 関連するコネクタを作成する方法を制御するを参照してください。[要素とその図形を作成する](#merge)です。  
  
##  <a name="a-namedeleteelementsa-deleting-elements"></a><a name="deleteelements"></a>要素を削除します。  
 呼び出すことにより、要素を削除`Delete()`:  
  
 `henry.Delete();`  
  
 この操作も削除されます。  
  
-   要素との間のリレーションシップ リンクします。 たとえば、`edward.Parents`は含まれなく`henry`します。  
  
-   要素をロールに、`PropagatesDelete`フラグが true を指定します。 たとえば、要素を表示する図形が削除されます。  
  
 既定では、すべての埋め込みリレーションシップを持つ`PropagatesDelete`ターゲット ロールの場合は true です。 削除する`henry`は削除されません、`familyTree`が`familyTree.Delete()`すべてを削除するように、`Persons`です。 詳細については、次を参照してください。[削除の動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)します。  
  
 既定では、`PropagatesDelete`参照リレーションシップのロールについては該当しません。  
  
 削除規則オブジェクトを削除する場合は、特定の伝達を省略する可能性があります。 これは、別の&1; つの要素を置換する場合に便利です。 1 つ以上のロールを削除する必要があります反映できませんの GUID を指定します。 GUID は、リレーションシップ クラスから取得できます。  
  
 `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
 (この例の効果はありません、ため`PropagatesDelete`は`false`の役割、`ParentsHaveChildren`リレーションシップです)。  
  
 場合によっては、削除は、要素または伝達によって削除される要素のいずれか、ロックの存在によってできません。 使用する`element.CanDelete()`要素を削除できるかどうかを確認します。  
  
##  <a name="a-namedeletelinksa-deleting-relationship-links"></a><a name="deletelinks"></a>リレーションシップ リンクを削除します。  
 リレーションシップ リンクを削除するには、ロールのプロパティから要素を削除します。  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 また、リンクを明示的に削除できます。  
  
 `edwardHenryLink.Delete();`  
  
 これら&3; つのメソッドには、同じ効果があります。 うちの&1; つを使用する必要があるだけです。  
  
 役割に 0..1 または 1..1 の多重度がある場合に設定できます`null`、または別の値にします。  
  
 `edward.FamilyTreeModel = null;`または。  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="a-namereordera-re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a>リレーションシップのリンクの順序を変更  
 ソースまたは特定のモデル要素を対象とされている特定のリレーションシップのリンクでは、特定のシーケンスがあります。 追加された順序で表示されます。 たとえば、このステートメントは常に同じ順序で子を生成します。  
  
 `foreach (Person child in henry.Children) ...`  
  
 リンクの順序を変更することができます。  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="a-namelocksa-locks"></a><a name="locks"></a>ロック  
 ロックによって、変更ができない可能性があります。 個々 の要素、パーティション、およびストアのロックを設定できます。 変更の種類を防止するロックを以下のレベルにある場合は、試行するときに例外がスロー可能性があります。 ロックは、要素を使用して設定するかどうかを検出できます。<xref:Microsoft.VisualStudio.Modeling.Immutability>。</xref:Microsoft.VisualStudio.Modeling.Immutability>名前空間で定義されている拡張メソッドである GetLocks()  
  
 詳細については、次を参照してください。[を読み取り専用セグメントを作成するロック ポリシーを定義する](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)です。  
  
##  <a name="a-namecopya-copy-and-paste"></a><a name="copy"></a>コピーと貼り付け  
 <xref:System.Windows.Forms.IDataObject>::</xref:System.Windows.Forms.IDataObject>に要素または要素グループをコピーすることができます。  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 要素は、シリアル化された要素のグループとして格納されます。  
  
 モデルには、IDataObject から要素をマージできます。  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()`いずれかを受け入れることができる、`PresentationElement`または`ModelElement`です。 指定した場合、 `PresentationElement`、3 番目のパラメーターとしてコピー先のダイアグラムでの位置を指定することもできます。  
  
##  <a name="a-namediagramsa-navigating-and-updating-diagrams"></a><a name="diagrams"></a>ナビゲートおよび図を更新  
 DSL、人や音楽などの概念を表す、ドメイン モデル要素は別の図に表示されるものを表す図形要素からです。 ドメイン モデルの要素は、重要なプロパティと概念の間のリレーションシップを格納します。 図形要素は、サイズ、位置、ダイアグラムで、オブジェクトのビューの色とその構成部分のレイアウトを格納します。  
  
### <a name="presentation-elements"></a>プレゼンテーション要素  
 ![基本図形および要素型のクラス図](~/docs/modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 DSL 定義では、指定した各要素は、次の標準的なクラスのいずれかから派生したクラスを作成します。  
  
|要素の種類|基底クラス|  
|---------------------|----------------|  
|ドメイン クラス|<xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|ドメインの関係|<xref:Microsoft.VisualStudio.Modeling.ElementLink></xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|形式|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|コネクタ|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|図|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 図上の要素は、通常、モデル要素を表します。 通常 (必ずではありませんが)、<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>ドメイン クラスのインスタンスを表す、<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>ドメイン リレーションシップのインスタンスを表します</xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>。 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>リレーションシップでは、ノードまたはリンクの図形をそのモデル要素にリンクします</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>。  
  
 すべてのノードまたはリンクの図形は、1 つの図に属しています。 バイナリのリンク図形は、2 つのノードの図形を接続します。  
  
 図形は、2 つのセットに子図形を設定できます。 内の図形、`NestedChildShapes`セットは、親の境界ボックスに限られています。 内の図形、`RelativeChildShapes`一覧が親 – ラベルやポートなどの境界の外側外側、またはその他の部分を表示できます。 ダイアグラムを持たない`RelativeChildShapes`および no`Parent`します。  
  
###  <a name="a-nameviewsa-navigating-between-shapes-and-elements"></a><a name="views"></a>図形および要素間を移動します。  
 ドメイン モデル要素および図形要素は関連する、<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>リレーションシップ</xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>。  
  
```c#  
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
  
 このリレーションシップでは、図にモデルのルートもリンクします。  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 図形により表されるモデル要素を取得するには、次のように使用します。  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>ダイアグラム上で移動します。  
 一般に図形とコネクタ、図の間を移動することをお勧めはできません。 図の外観で作業する必要がある場合にのみ、図形とコネクタの間で移動モデルでリレーションシップをナビゲートすることをお勧めします。 これらのメソッドは、コネクタを両方の end での図形にリンクします。  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 多くの図形は、合成します。これらについては、親シェイプと子の&1; つまたは複数の層の構成されます。 別の形を基準に配置する図形があると言われますが、*子*します。 親シェイプに移動したとき、子はそのと共に移動します。  
  
 *相対子*親シェイプの境界ボックス外に表示されます。 *入れ子になった*子は厳密に親の境界内に表示されます。  
  
 ダイアグラムで図形の上部のセットを取得するには、次のように使用します。  
  
 `Diagram.NestedChildShapes`  
  
 図形とコネクタの親クラスがあります。  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 --<xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement></xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram></xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 -----<xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 -------<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape></xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="a-nameshapepropertiesa-properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a>図形とコネクタのプロパティ  
 ほとんどの場合は、図形に明示的な変更を加える必要はありません。 モデル要素が変更されると、「修正」ルールは、図形とコネクタを更新します。 詳細については、次を参照してください。[に応答すると変更の伝達](../modeling/responding-to-and-propagating-changes.md)します。  
  
 ただし、図形には、モデル要素に依存しないプロパティに明示的ないくつか変更を加える便利です。 たとえば、これらのプロパティを変更する可能性があります。  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>図形の幅と高さを決定します。</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-親図形または図に対して相対的な位置</xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-ペンと、図形またはコネクタを描画するために使用されるブラシのセット</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>その図形を非表示</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>その図形が表示される、`Hide()`</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>  
  
###  <a name="a-namemergea-creating-an-element-and-its-shape"></a><a name="merge"></a>要素とその図形を作成します。  
 作成する要素の埋め込みリレーションシップ ツリーにリンクすると、図形が自動的に作成され、関連付けられています。 これは、トランザクションの最後に実行するルールを「修正」を実行します。 ただし、図形は、自動的に割り当てられている場所に表示されます、形状、色、およびその他の機能が既定値です。 図形を作成する方法を制御するには、マージ関数を使用できます。 まず、ElementGroup に追加する要素を追加し、図に、グループをマージする必要があります。  
  
 この方法では:  
  
-   要素名とプロパティが割り当てられている場合、名前を設定します。  
  
-   DSL 定義で指定した要素マージ ディレクティブすべてを監視します。  
  
 この例では、ユーザーをダブルクリックすると、図に、マウスの位置に図形を作成します。 このサンプルでは、DSL 定義で、`FillColor`の`ExampleShape`公開されています。  
  
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
  
 複数の図形を指定した場合を使用して、相対的な位置を設定、`AbsoluteBounds`です。  
  
 色とコネクタがこのメソッドを使用して公開されているその他のプロパティを設定することもできます。  
  
### <a name="use-transactions"></a>トランザクションを使用して  
 図形、コネクタと図のサブタイプ<xref:Microsoft.VisualStudio.Modeling.ModelElement>とストアのライブ</xref:Microsoft.VisualStudio.Modeling.ModelElement>。 トランザクションの内部でのみ変更を加える必要がありますのでにします。 詳細については、次を参照してください。[方法: モデルを更新するトランザクションを使用して](../modeling/how-to-use-transactions-to-update-the-model.md)します。  
  
##  <a name="a-namedocdataa-document-view-and-document-data"></a><a name="docdata"></a>ドキュメント ビューとドキュメント データ  
 ![標準タイプのクラス図](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>パーティションを格納します。  
 モデルが読み込まれるときに付随する図が同時に読み込まれます。 通常は、モデルが Store.DefaultPartition に読み込まれ、ダイアグラムの内容が別のパーティションに読み込まれます。 通常、各パーティションのコンテンツが読み込まれ、別のファイルに保存されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement></xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)   
 [ドメイン固有言語からコードを生成します。](../modeling/generating-code-from-a-domain-specific-language.md)   
 [方法: トランザクションを使用してモデルを更新します。](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Visual Studio Modelbus を使用して、モデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)

