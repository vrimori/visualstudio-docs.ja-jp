---
title: DslDefinition.dsl ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: f3fc3ed7-2438-4e5a-b3d7-fe7e0e8a134c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5bf56b06771b905ec4982f7de7f91648c2e6b3a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306125"
---
# <a name="the-dsldefinitiondsl-file"></a>DslDefinition.dsl ファイル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックでは、Dsl プロジェクトの DslDefinition.dsl ファイルの構造を説明します、[!INCLUDE[dsl](../includes/dsl-md.md)]を定義するには、ソリューション、*ドメイン固有言語*します。 DslDefinition.dsl ファイルは、クラスと、図、図形、コネクタ、シリアル化形式と、ドメイン固有言語のリレーションシップについて説明しますと**ツールボックス**のドメイン固有言語とそのツールを編集します。 ドメイン固有言語ソリューションでは、これらのツールを定義するコードは DslDefinition.dsl ファイルの情報に基づいて生成されます。  
  
 一般に、使用、*ドメイン固有言語デザイナー* DslDefinition.dsl ファイルを編集します。 ただし DslDefinition.dsl ファイルの未加工の形式は XML であるため、DslDefinition.dsl ファイルを XML エディターで開くことができます。 ファイルに記述されている情報と、ファイルの編成を理解しておくと、デバッグおよび拡張を行う際に役立つことがあります。  
  
 このトピックに記載されている例は、コンポーネント図のソリューション テンプレートのものです。 例を確認するには、コンポーネント モデルのソリューション テンプレートに基づくドメイン固有言語ソリューションを作成します。 ソリューションの作成後に、DslDefinition.dsl ファイルが Domain-Specific Language Designer に表示されます。 ファイルを閉じてでを右クリックして**ソリューション エクスプ ローラー**、 をポイント**プログラムから開く**、 をクリックして**XML エディター**、順にクリックします**OK**します。  
  
## <a name="sections-of-the-dsldefinitiondsl-file"></a>DslDefinition.dsl ファイルの各セクション  
 ルート要素は\<Dsl >、およびその属性がドメイン固有言語、名前空間の名前を特定のバージョン管理のメジャーおよびマイナー バージョン番号します。 `DslDefinitionModel` スキーマは、有効な DslDefinition.dsl ファイルの内容と構造を定義します。  
  
 子要素、 \<Dsl > ルート要素は、次のとおり。  
  
 クラス  
 このセクションでは、生成されるコードでクラスを生成する各ドメイン クラスを定義します。  
  
 関係  
 このセクションでは、モデル内の各リレーションシップを定義します。 ソース とターゲットは、リレーションシップの両側を表します。  
  
 型  
 このセクションでは、各型とその名前空間を定義します。 ドメイン プロパティには 2 つの型があります。 `DomainEnumerations` はモデルで定義され、DomainModel.cs に型を生成します。 `ExternalTypes` は、それ以外の場所で定義されている型 (`String` や `Int32` など) を参照するだけであり、何も生成しません。  
  
 図形  
 このセクションでは、デザイナーにモデルを表示する方法を記述するシェイプを定義します。 これらの幾何的シェイプは、Diagram セクションのモデルのクラスにマップされています。  
  
 コネクタ  
 このセクションでは、デザイナーに表示されるコネクタの外観を定義します。 これらの幾何的スタイル記述は、Diagram セクションのモデル内の特定のリレーションシップにマップされています。  
  
 XmlSerializationBehavior  
 このセクションでは、シリアル化方式が定義され、各クラスがどのようにファイルに保存されるかについて追加情報が提供されます。  
  
 ExplorerBehavior  
 このセクションで定義する方法、 **DSL エクスプ ローラー**ユーザーがモデルを編集するときに、ウィンドウが表示されます。  
  
 ConnectionBuilders  
 このセクションでは、各コネクタ ツール (接続可能な 2 つのクラスを結ぶリンクを作成するツール) の接続ビルダーを定義します。 このセクションでは、ソース クラスとターゲット クラスを接続できるかどうかを決定します。  
  
 図  
 このセクションでは図を定義します。このセクションを使用して、背景色やルート クラスなどのプロパティを指定できます。 (ルート クラスは、図全体が表すドメイン クラスです。)Diagram セクションには、ShapeMap 要素と ConnectorMap 要素も含まれています。これらの要素は、各ドメイン クラスまたはリレーションシップを表すシェイプまたはコネクタを指定します。  
  
 Designer  
 このセクションで定義を集めてデザイナー (エディター)、**ツールボックス**検証の設定、図、およびシリアル化スキーム。 Designer セクションでは、モデルのルート クラスも定義されます。これは通常、図のルート クラスでもあります。  
  
 エクスプローラー  
 このセクションで、 **DSL エクスプ ローラー** (XmlSerializationBehavior セクションで定義されている) 動作します。  
  
## <a name="monikers-in-the-dsldefinitiondsl-file"></a>DslDefinition.dsl ファイルのモニカー  
 DslDefinition.dsl ファイルでは、モニカーを使用して特定の項目のクロス リファレンスを作成できます。 たとえば、リレーションシップの各定義には Source サブセクションと Target サブセクションが含まれています。 各サブセクションには、そのリレーションシップを使用してリンクできるオブジェクトのクラスのモニカーが含まれています。  
  
```  
<DomainRelationship …        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole …>  
       <RolePlayer>  
         <DomainClassMoniker Name="Library" />  
       </RolePlayer>  
     </DomainRole>  
   </Source>  
```  
  
 通常、参照される項目 (この例では `Library` ドメイン クラス) の名前空間は、参照元項目 (この例では LibraryHasMembers ドメイン リレーションシップ) と同じです。 これらの場合、モニカーによってクラス名だけが指定される必要があります。 それ以外の場合は、/Namespace/Name という完全な形式を使用する必要があります。  
  
```  
  
<DomainClassMoniker Name="/ExampleNameSpace/Library" />  
  
```  
  
 モニカー システムでは、XML ツリー内で兄弟関係にあるクラスには、識別可能な名前を使用する必要があります。 このため、たとえば同名のクラスが 2 つ含まれているドメイン固有言語定義を保存しようとすると、検証エラーが発生します。 後で DslDefinition.dsl ファイルを正しく再読み込みできるようにするため、DslDefinition.dsl ファイルを保存する前に必ず重複名エラーなどを訂正してください。  
  
 それぞれの型に固有のモニカーがあります (DomainClassMoniker、DomainRelationshipMoniker など)。  
  
## <a name="types"></a>型  
 Types セクションでは、DslDefinition.dsl ファイルにプロパティの型として含まれているすべての型が指定されます。 これらの型は、外部型 (System.String など) と列挙型に分類されます。  
  
### <a name="external-types"></a>外部型  
 コンポーネント図の例では、一連の標準基本型がリストされていますが、使用されるのはその一部のみです。  
  
 各外部型の定義は、名前と名前空間 (String と System など) だけで構成されます。  
  
```  
<ExternalType Name="String" Namespace="System" />  
```  
  
 型に対応するコンパイラ キーワード ("string" など) の代わりに、型の完全な名前が使用されます。  
  
 外部型は、標準ライブラリの型に制限されていません。  
  
### <a name="enumerations"></a>列挙型  
 標準的な列挙型の指定は次の例のようになります。  
  
```  
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">  
  <Literals>  
    <EnumerationLiteral Name="Start" Value="1"/>  
    <EnumerationLiteral Name="Decision" Value="2"/>  
  </Literals>  
</DomainEnumeration>  
```  
  
 `IsFlags` 属性は、生成されるコードに `[Flags]` 共通言語ランタイム (CLR) 属性がプレフィックスとして付けられるかどうかを制御します。この CLR 属性は、列挙の値がビットごとに結合できるかどうかを決定します。 この属性が true に設定されている場合は、リテラル値に 2 の累乗値を指定する必要があります。  
  
## <a name="classes"></a>クラス  
 ドメイン固有言語の定義の要素のほとんどは、直接的または間接的に `DomainClass` のインスタンスです。 `DomainClass` のサブクラスには、`DomainRelationship`、`Shape`、`Connector`、`Diagram` などがあります。 DslDefinition.dsl ファイルの `Classes` セクションには、ドメイン クラスがリストされます。  
  
 各クラスには一連のプロパティがあります。また、クラスに基底クラスが含まれていることもあります。 コンポーネント図の例では、`NamedElement` は `Name` プロパティ (型は文字列) を持つ抽象クラスです。  
  
```  
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">  
  <Properties>  
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
</DomainClass>  
```  
  
 `NamedElement` は、`Component` などのその他の複数のクラスの基底クラスであり、`Name` から継承した `NamedElement` プロパティのほかに固有のプロパティを持ちます。 BaseClass 子ノードにはモニカー参照が含まれています。 参照先クラスは同じ名前空間内にあるので、モニカーで必要となるのはその名前だけです。  
  
```  
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">  
  <BaseClass>  
    <DomainClassMoniker Name="NamedElement" />  
  </BaseClass>  
  <Properties>  
    <DomainProperty Name="Kind" DisplayName="Kind" >  
      <Type>  
        <ExternalTypeMoniker Name="/System/String" />  
      </Type>  
    </DomainProperty>  
  </Properties>  
```  
  
 すべてのドメイン クラス (リレーションシップ、シェイプ、コネクタ、図など) には、次の属性と子ノードを含めることができます。  
  
-   **Id.** この属性は、GUID です。 ファイルに値を指定しないと、Domain-Specific Language Designer によって値が作成されます。 (このドキュメントの説明では、スペースを節約するためこの属性は通常省略しています。)  
  
-   **Name および Namespace。** これらの属性は、生成されたコードで、クラスの名前空間と名前を指定します。 これらの属性の組み合わせは、ドメイン固有言語内で一意である必要があります。  
  
-   **InheritanceModifier します。** この属性は、"abstract"、"sealed"または none です。  
  
-   **DisplayName.** この属性に表示される名前、**プロパティ**ウィンドウ。 DisplayName 属性には、スペースとその他の句読点を使用できます。  
  
-   **GeneratesDoubleDerived.** この属性設定されている場合は true、2 つのクラスが生成され、1 つは、他のサブクラスです。 生成されるすべてのメソッドは基底クラスに含まれ、コンストラクターはサブクラスに含まれます。 この属性を設定すると、カスタム コードで生成されるメソッドをすべてオーバーライドできます。  
  
-   **HasCustomConstructor**します。 この属性が true に設定されている場合、生成されるコードからコンストラクターが省略されるため、独自のコンストラクターを作成できます。  
  
-   **属性**します。 この属性には、生成されたクラスの CLR 属性が含まれています。  
  
-   **BaseClass**します。 基底クラスを指定する場合、同じ型でなければなりません。 たとえば、ドメイン クラスにはその基底クラスとして別のドメイン クラスを指定する必要があり、コンパートメント シェイプにはコンパートメント シェイプを含める必要があります。 基底クラスを指定しない場合は、生成されるコード内のクラスは標準フレームワーク クラスから派生されます。 たとえば、ドメイン クラスは `ModelElement` から派生します。  
  
-   **プロパティ**します。 この属性には、トランザクション制御で保持され、モデルを保存するときに維持されるプロパティが含まれています。  
  
-   **ElementMergeDirectives**します。 各要素マージ ディレクティブは、別のクラスの異なるインスタンスがどのように親クラス インスタンスに追加されるかを制御します。 このトピックの後半で、要素マージ ディレクティブの詳細について説明します。  
  
-   `Classes` セクションにリストされているドメイン クラスごとに C# クラスが生成されます。 C# クラスは Dsl\GeneratedCode\DomainClasses.cs に生成されます。  
  
### <a name="properties"></a>プロパティ  
 各ドメイン プロパティには、名前と型があります。 この名前は、ドメイン クラスとその中間基底クラス内で固有である必要があります。  
  
 型は `Types` セクションにリストされている型の 1 つを参照している必要があります。 一般に、モニカーには名前空間を含める必要があります。  
  
```  
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">  
  <Type>  
    <ExternalTypeMoniker Name="/System/String" />  
  </Type>  
</DomainProperty>  
```  
  
 各ドメイン プロパティには次の属性も指定できます。  
  
-   **IsBrowsable**します。 この属性がプロパティを表示するかどうかを指定します、**プロパティ**ウィンドウ、ユーザーが親クラスのオブジェクトをクリックするとします。  
  
-   **IsUIReadOnly**します。 この属性は、ユーザーがでプロパティを変更できるかどうかを指定します、**プロパティ**ウィンドウまたはデコレータ プロパティが表示されます。  
  
-   **種類**します。 この属性は、Normal、Calculated、CustomStorage のいずれかに設定できます。 この属性を Calculated に設定する場合は、値を決定するカスタム コードを記述する必要があります。また、このプロパティは読み取り専用になります。 この属性を CustomStorage に設定する場合は、値の取得と設定の両方を行うコードを記述する必要があります。  
  
-   **IsElementName**します。 この属性を true に設定すると、親クラスのインスタンスの作成時にその値が自動的に固有値に設定されます。 各クラスで 1 つの文字列型プロパティのみに対して、この属性を true に設定できます。 コンポーネント図の例では、`Name` の `NamedElement` プロパティで `IsElementName` が true に設定されています。 ユーザーが `Component` 要素 (`NamedElement` から継承) を作成するときは常に、名前が自動的に初期化され、"Component6" のようになります。  
  
-   `DefaultValue`。 この属性を指定した場合、このクラスの新規インスタンスでは、指定した値がこの属性に割り当てられます。 `IsElementName` が設定されている場合、DefaultValue 属性は新しい文字列の初期部分を指定します。  
  
-   **カテゴリ**ヘッダーでプロパティを表示するには、**プロパティ**ウィンドウ。  
  
## <a name="relationships"></a>リレーションシップ  
 `Relationships` セクションには、ドメイン固有言語のすべてのリレーションシップがリストされます。 すべての `Domain Relationship` はバイナリで有向性があり、ソース クラスのメンバーとターゲット クラスのメンバーをリンクします。 ソース クラスとターゲット クラスは通常はドメイン クラスですが、その他のリレーションシップとのリレーションシップも使用できます。  
  
 たとえば Connection リレーションシップは OutPort クラスのメンバーを InPort クラスのメンバーにリンクします。 このリレーションシップの各リンク インスタンスは、OutPort インスタンスを InPort インスタンスに接続します。 リレーションシップは多対多であるため、各 OutPort インスタンスにはそのインスタンスをソースとする Connection リンクを複数作成でき、各 InPort インスタンスにはそのインスタンスをターゲットとする Connection リンクを複数作成できます。  
  
### <a name="source-and-target-roles"></a>ソース ロールとターゲット ロール  
 各リレーションシップにはソース ロールとターゲット ロールが含まれています。これらのロールの属性を次に示します。  
  
-   `RolePlayer` 属性は、リンクされたインスタンス (ソースは OutPort、ターゲットは InPort) のドメイン クラスを参照します。  
  
-   `Multiplicity` 属性には、ZeroMany、ZeroOne、One、および OneMany という 4 つの値を指定できます。 この属性は、1 つのロール プレーヤーに関連付けることができるこのリレーションシップのリンクの数を示します。  
  
-   `PropertyName` 属性は、もう一方の端にあるオブジェクトにアクセスするためにロール プレイ クラスで使用される名前を指定します。 この名前は、リレーションシップを走査するためにテンプレートまたはカスタム コードで使用されます。 たとえば、ソース ロールの `PropertyName` 属性は `Targets` に設定されます。 したがって、次のコードは機能します。  
  
    ```  
    OutPort op = …; foreach (InPort ip in op.Targets) ...  
    ```  
  
     規則により、多重度が ZeroMany または OneMany の場合、プロパティ名は複数形です。  
  
     ロールの多重度は、このロールの各インスタンスに関連付けることができる反対のロールの数を示します。 たとえば ComponentHasPorts リレーションシップの場合、ターゲット ロールの `RolePlayer` 属性が Port に設定されており、`PropertyName` 属性が Component に設定されており、`Multiplicity` 属性が ZeroOne に設定されています。 したがって、このロールを使用する適切なコードは次のようになります。  
  
    ```  
    ComponentPort p = …; Component c = p.Component; if (c != null) …  
    ```  
  
-   ロールの `Name` は、Relationship クラス内で使用され、リンクの該当する端を指す名前です。 規則により、ロール名は常に単数形です。これは、各リンクのそれぞれの端にあるインスタンスが 1 つのみであるためです。 したがって、次のコードは機能します。  
  
    ```  
    Connection connectionLink = …; OutPort op = connectionLink.Source;  
    ```  
  
-   既定では、`IsPropertyGenerator` 属性は true に設定されています。 この属性が false に設定されている場合、Role Player クラスでプロパティが作成されません。 (この場合 `op.Targets` などは機能しません)。 ただし、カスタム コードを使用してリレーションシップを走査できます。または、カスタム コードでリレーションシップが明示的に使用されている場合は、リンク自体へのアクセスを取得することができます。  
  
    ```  
    OutPort op = …; foreach (InPort ip in Connection.GetTargets(op)) …  
    foreach (Connection link in Connection.GetLinksToTargets(op)) …  
    ```  
  
### <a name="relationship-attributes"></a>リレーションシップ属性  
 すべてのクラスで使用可能な属性と子ノードの他に、各リレーションシップには次の属性があります。  
  
-   **IsEmbedding**します。 このブール属性は、リレーションシップが埋め込みツリーの一部であるかどうかを指定します。 すべてのモデルは、その埋め込みリレーションシップを含むツリーを形成する必要があります。 したがって、モデルのルート以外のすべてのドメイン クラスは、1 つ以上の埋め込みリレーションシップのターゲットである必要があります。  
  
-   **AllowsDuplicates**します。 このブール属性は、ソースとターゲットの両方で多重度が "many" であるリレーションシップにのみ適用されます。既定では false に設定されています。 言語ユーザーが、同一リレーションシップの複数のリンクを使用して、ソース要素とターゲット要素の 1 つのペアを接続できるかどうかを指定します。  
  
## <a name="designer-and-toolbox-tabs"></a>[デザイナー] タブと [ツールボックス] タブ  
 メイン部分、**デザイナー** DslDefinition.dsl ファイルのセクションでは、 **ToolboxTab**要素。 1 つのデザイナーが表す、生成されたデザイナーのヘッダー セクションをこれらの要素のいくつか**ツールボックス**します。 各**ToolboxTab**要素は、1 つまたは複数含めることができます**ElementTool**要素、 **ConnectionTool**要素、またはその両方です。  
  
 要素ツールは、特定のドメイン クラスのインスタンスを作成できます。 ユーザーが要素ツールを図にドラッグしたときの結果は、要素マージ ディレクティブによって決定します。これについては、このトピックの要素マージ ディレクティブに関するセクションで後述します。  
  
 各接続ツールは特定の接続ビルダーを呼び出すことができます。 1 つの接続ビルダーが、ユーザーがマウスをクリックした位置に基づいて複数の種類のリレーションシップを作成できます。これについては、接続ビルダーに関するセクションで説明します。  
  
 いずれの種類のツールでも、シェイプやコネクタは直接作成されません。 それぞれのツールでは、ドメイン クラスまたはドメイン リレーションシップがインスタンス化されます。シェイプとコネクタのマッピングにより、ドメイン クラスまたはドメイン リレーションシップがどのように表示されるかが決まります。  
  
## <a name="paths"></a>パス  
 ドメイン パスは DslDefinition.dsl ファイル内のさまざまな場所に記述されます。 これは、モデル (ドメイン固有言語のインスタンス) 内の要素間の一連のリンクを指定するパスです。 パスの構文は単純ですが冗長です。  
  
 DslDefinition.dsl ファイルではパスは `<DomainPath>…</DomainPath>` タグに囲まれて指定されます。 パスは複数リンク間を移動できますが、ほとんどの場合は 1 つのリンクのみを移動します。  
  
 1 つのパスはセグメントのシーケンスで構成されます。 各セグメントは、オブジェクトからリンクへのホップ、またはリンクからオブジェクトへのホップです。 したがって、長いパスでは一般にホップが交互に現れます。 1 番目のホップがオブジェクトからリンクのホップ、2 番目はリンクのもう一方の端のオブジェクトへのホップ、3 番目は次のリンクへのホップ、となります。 このシーケンスの例外として、リレーションシップ自体が別のリレーションシップのソースまたはターゲットである場合があります。  
  
 各セグメントはリレーションシップ名で始まります。 オブジェクトからリンクへのホップでは、リレーションシップの後にドットとプロパティ名が続きます (`Relationship . Property`)。 リンクからオブジェクトへのホップでは、リレーションシップの後に感嘆符とロール名が続きます (`Relationship ! Role`)。  
  
 コンポーネント図の例では、ShapeMap の ParentElementPath に InPort のパスが含まれています。 このパスは次のように始まります。  
  
```  
    ComponentHasPorts.Component  
```  
  
 この例では、InPort は ComponentPort のサブクラスであり、リレーションシップ ComponentHasPorts を持ちます。 プロパティの名前は Component です。  
  
 このモデルに対して c# を記述する場合に関連するクラスの各リレーションシップを生成するプロパティを使用して、1 つの手順でリンク経由でジャンプできます。  
  
```  
     InPort port; ...  Component c = port.Component;  
```  
  
 ただし、両方のホップは明示的にパス構文で行う必要があります。 この要件から、中間リンクへのアクセスが容易になります。 リンクから Component へのホップを実行するコードを次に示します。  
  
```  
    ComponentHasPorts.Component / ! Component  
```  
  
 (リレーションシップ名が前のセグメントでの名前と同じ場合は、リレーションシップ名を省略できます。)  
  
## <a name="element-merge-directives"></a>要素マージ ディレクティブ  
 言語ユーザーがから項目をドラッグすると、**ツールボックス**を図に、ツールのクラスのインスタンスを構築します。 また、そのインスタンスと既存のモデル要素の間にリンクが作成されます。 言語ユーザーがドラッグしたときにコンポーネントやコメントなど、一部の項目が作成された、**ツールボックス**図の空白部分にします。 その他の項目は、言語ユーザーがそれらを他のホスト要素にドラッグすると作成されます。 たとえば OutPort または Inport は、言語ユーザーがコンポーネントにドラッグすると作成されます。  
  
 Component などのホスト クラスで新しい要素が受け入れられるのは、ホスト クラスに、新しい要素のクラスのための要素マージ ディレクティブが含まれている場合に限ります。 たとえば Name="Component"が指定されている DomainClass ノードの内容が、次のようであるとします。  
  
```  
<DomainClass Name="Component" …> …  
    <ElementMergeDirective>  
      <Index>  
        <DomainClassMoniker Name="ComponentPort" />  
      </Index>  
      <LinkCreationPaths>  
        <DomainPath>ComponentHasPorts.Ports</DomainPath>  
      </LinkCreationPaths>  
    </ElementMergeDirective> …  
```  
  
 Index ノードの下のクラス モニカーは、受け入れ可能な要素のクラスを参照します。 この場合、ComponentPort は InPort と OutPort の抽象基底クラスです。 したがって、これらの要素のいずれかを受け入れることができます。  
  
 言語のルート クラスである ComponentModel には、コンポーネントとコメントの要素マージ ディレクティブが含まれています。 図の空白部分はルート クラスを表すため、言語ユーザーはこれらのクラスの項目を図に直接ドラッグできます。 ただし ComponentModel には ComponentPort の要素マージ ディレクティブはありません。 したがって、言語ユーザーは InPort または OutPort を図に直接ドラッグできません。  
  
 要素マージ ディレクティブは、新しい要素が既存のモデルと統合またはマージできるように、作成されるリンクを指定します。 ComponentPort の場合、ComponentHasPorts のインスタンスが作成されます。 DomainPath は、新しい要素の追加先である親クラス (Ports) のリレーションシップとプロパティの両方を指定します。  
  
 複数のリンク作成パスを組み込むことで、1 つの要素マージ ディレクティブで複数のリンクを作成できます。 また、いずれかのパスを埋め込む必要があります。  
  
 1 つのリンク作成パスに複数のセグメントを使用できます。 この場合、作成する必要があるリンクは最終セグメントで定義されます。 これより前のセグメントは、親クラスから、新規リンクの作成元オブジェクトに移動します。  
  
 たとえば、この要素マージ ディレクティブを Component クラスに追加できます。  
  
```  
<DomainClass Name="Component" …> …  
  <ElementMergeDirective>  
    <Index>  
       <DomainClassMoniker Name="Comment"/>  
    </Index>  
    <LinkCreationPaths>  
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>  
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>  
    </LinkCreationPaths>  
  </ElementMergeDirective>  
```  
  
 これで、言語ユーザーがコンポーネントにコメントをドラッグすると、そのコンポーネントへのリンクを使用して新しいコメントが自動的に作成されるようになります。  
  
 1 番目のリンク作成パスは `Component` から `ComponentModel` に移動し、その後埋め込みリレーションシップ `ComponentModelHasComments` のインスタンスを作成します。 2 番目のリンク作成パスは、ホスト Component から新しい Comment への参照リレーションシップ CommentsReferenceComponents のリンクを作成します。 すべてのリンク作成パスは、ホスト クラスから始まり、新しくインスタンス化されたクラスへ進むリンクで終わる必要があります。  
  
## <a name="xmlclassdata"></a>XmlClassData  
 各ドメイン クラス (リレーションシップとその他のサブタイプを含む) では、`XmlClassData` ノードに追加情報を指定できます。このノードは、DslDefinition.dsl ファイルの `XmlSerializationBehavior` セクションの下にあります。 これは、モデルをファイルに保存するときに、クラスのインスタンスがシリアル化形式でどのように保存されるかに関する情報です。  
  
 `XmlSerializationBehavior` の影響を受ける生成コードのほとんどは、`Dsl\GeneratedCode\Serializer.cs` 内にあります。  
  
 各 `XmlClassData` ノードには、次の子ノードと属性が含まれています。  
  
-   モニカー ノード。データの適用対象クラスを参照します。  
  
-   **XmlPropertyData**クラスで定義されている各プロパティ。  
  
-   **XmlRelationshipData**各リレーションシップは、クラスに属しています。 (リレーションシップにはそれ自体の XmlClassData ノードも含まれています。)  
  
-   **TypeName**文字列属性は、生成されたコードでシリアル化ヘルパー クラスの名前を指定します。  
  
-   **ElementName**文字列で、このクラスのシリアル化されたインスタンスの XML タグを決定します。 規則では、ElementName は通常、最初の文字が小文字であることを除きクラス名と同一です。 たとえば、サンプル モデル ファイルは次のように始まります。  
  
    ```  
    <componentModel …  
    ```  
  
-   **MonikerElementName**でユーザーのシリアル化されたモデル ファイル。 この属性により、このクラスを参照するモニカーが導入されます。  
  
-   **MonikerAttributeName**モニカー内の XML 属性の名前を識別します。 ドメイン固有言語の作成者によって定義されているユーザーのシリアル化されたファイルのフラグメントで**MonikerElementName** "inPortMoniker"としてと**MonikerAttributeName** "path"として。  
  
    ```  
    <inPortMoniker path="//Component2/InPort1" />  
    ```  
  
### <a name="connectionbuilders"></a>ConnectionBuilders  
 接続ツールごとに接続ビルダーが定義されています。 各接続ビルダーは、1 つ以上の LinkConnectDirective 要素で構成されています。各 LinkConnectDirective 要素は、1 つ以上の SourceDirective 要素と 1 つ以上の TargetDirective 要素で構成されています。 ユーザーは、接続ツールをクリックしたら、SourceDirective 要素のリストに含まれるモデル要素にマップされている任意のシェイプから接続を開始できます。 この接続は、TargetDirective 要素のリストに含まれている要素にマップするシェイプで終端できます。 インスタンス化されるリレーションシップのクラスは、接続の開始位置によって指定される LinkConnectDirective 要素に応じて異なります。  
  
### <a name="xmlpropertydata"></a>XmlPropertyData  
 A **DomainPropertyMoniker**属性は、データが参照するプロパティを識別します。 この属性は、それを囲む ClassData のクラスのプロパティでなければなりません。  
  
 **XmlName**属性は、対応する属性名を XML に表示する必要があります。 規則では、この文字列は、最初の文字が小文字であることを除きプロパティ名と同一です。  
  
 既定で、**表現**属性が属性に設定します。 場合**表現**子要素に設定されて、xml ノードが作成されます。 場合**表現**が Ignore に設定、プロパティはシリアル化されません。  
  
 **IsMonikerKey**と**IsMonikerQualifier**属性は、親クラスのインスタンスを識別する役割プロパティを提供します。 設定できる**IsMonikerKey**で定義されているまたはクラスによって継承されている 1 つのプロパティを true に設定します。 この属性は、親クラスの個別のインスタンスを識別します。 `IsMonikerKey` に設定するプロパティは通常、名前またはその他のキー識別子です。 たとえば `Name` 文字列プロパティは、NameElement およびその派生クラスのモニカー キーです。 ユーザーがモデルをファイルに保存する場合、この属性には、埋め込みリレーションシップ ツリーの兄弟間で固有な各インスタンスの値が含まれている必要があります。  
  
 シリアル化モデル ファイルでは、要素の完全なモニカーはモデル ルートから埋め込みリレーションシップ ツリーへのパスであり、各ポイントでモニカー キーが引用符で囲まれています。 たとえば、InPort は Component に埋め込まれており、Component はモデル ルートに埋め込まれています。 したがって有効なモニカーは次のようになります。  
  
```  
<inPortMoniker name="//Component2/InPort1" />  
```  
  
 設定することができます、 **IsMonikerQualifier**文字列プロパティの属性し、要素の完全な名前を作成するその他の方法を提供します。 など、DslDefinition.dsl ファイルで**Namespace**モニカー修飾子です。  
  
### <a name="xmlrelationshipdata"></a>XmlRelationshipData  
 シリアル化モデル ファイル内では、(埋め込みリレーションシップと参照リレーションシップの両方の) リンクは、リレーションシップのソース エンドの子ノードによって表されます。 埋め込みリレーションシップの場合、子ノードにはサブツリーが含まれています。 参照リレーションシップの場合、子ノードにはツリーの別の部分を参照するモニカーが含まれています。  
  
 **XmlRelationshipData**属性、 **XmlClassData**属性は、ソース要素内で子ノードは入れ子になった方法だけを定義します。 ドメイン クラスのソースであるすべてのリレーションシップが 1 つ**XmlRelationshipData**属性。  
  
 **DomainRelationshipMoniker**クラスのソースとするリレーションシップのいずれかの属性を識別します。  
  
 **RoleElementName**属性をシリアル化されたデータで子ノードを囲む XML タグ名を提供します。  
  
 たとえば DslDefinition.dsl ファイルには次のコードが含まれています。  
  
```  
<XmlClassData ElementName="component" …>  
  <DomainClassMoniker Name="Component" />  
  <ElementData>  
    <XmlRelationshipData RoleElementName="ports">  
      <DomainRelationshipMoniker Name="ComponentHasPorts" />  
    </XmlRelationshipData>  
```  
  
 したがって、シリアル化ファイルの内容は次のようになります。  
  
```  
<component name="Component1"> <!-- parent ->  
   <ports> <!-- role ->  
     <outPort name="OutPort1"> <!-- child element ->  
       …  
     </outPort>  
   </ports> …  
```  
  
 場合、 **UseFullForm**属性に設定されて true の場合、入れ子のレイヤーが導入されます。 このレイヤーはリレーションシップ自体を表します。 リレーションシップにプロパティが含まれている場合、この属性を true に設定する必要があります。  
  
```  
<XmlClassData ElementName="outPort">  
   <DomainClassMoniker Name="OutPort" />  
   <ElementData>  
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">  
       <DomainRelationshipMoniker Name="Connection" />  
     </XmlRelationshipData>  
   </ElementData>  
 </XmlClassData>  
```  
  
 シリアル化ファイルの内容は次のようになります。  
  
```  
<outPort name="OutPort1">  <!-- Parent ->  
   <targets>  <!-- role ->  
     <connection sourceRoleName="X">  <!-- relationship link ->  
         <inPortMoniker name="//Component2/InPort1" /> <!-- child ->  
     </connection>  
    </targets>  
  </outPort>  
```  
  
 (Connection リレーションシップには、要素と属性の名前を指定する独自の XML クラス データがあります。)  
  
 場合、 **OmitElement**属性の設定を true に、リレーションシップ ロール名を省略すると、2 つのクラスは、複数のリレーションシップを持つ場合は、あいまいでないし、シリアル化されたファイルで省略しています。 例えば:  
  
```  
<component name="Component3">  
  <!-- only one relationship could get here: ->  
  <outPort name="OutPort1">    
     <targets> …  
```  
  
### <a name="serialization-of-a-domain-specific-language-definition"></a>ドメイン固有言語定義のシリアル化  
 DslDefinition.dsl ファイル自体がシリアル化ファイルであり、ドメイン固有言語定義に準拠しています。 XML シリアル化定義の例を次に示します。  
  
-   **Dsl** RootClass ノードであり、図のクラス。 DomainClass、DomainRelationship、およびその他の要素は `Dsl` の下に埋め込まれています。  
  
-   **クラス**は、 **RoleElementName**のドメイン固有言語と DomainClass 間のリレーションシップ。  
  
```  
<Dsl Name="CmptDsl5" …>  
  <Classes>  
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" …  
```  
  
-   **XmlSerializationBehavior**属性が下に埋め込まれて、`Dsl`属性が、 **OmitElement**埋め込みリレーションシップ属性が設定されています。 したがって、その間に `RoleElementName` 属性がありません。 これに対し、 **ClassData**属性は、`RoleElementName`間の埋め込みリレーションシップの属性、 **XmlSerializationBehavior**属性および**XmlClassData**属性。  
  
```  
<Dsl Name="CmptDsl5" …> …  
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >  
    <ClassData>  
      <XmlClassData …>…</XmlClassData>  
      <XmlClassData …>…</XmlClassData>  
```  
  
-   ConnectorHasDecorators は、`Connector` と `Decorator` の間の埋め込みリレーションシップです。 `UseFullForm` が設定されているため、Connector オブジェクトからの各リンクのプロパティ リストに、リレーションシップの名前が含まれます。 ただし `OmitElement` も設定されているため、`RoleElementName` 内部に埋め込まれている複数のリンクは `Connector` によって囲まれません。  
  
```  
<Connector Name="AssociationLink" …>  
  <ConnectorHasDecorators Position="TargetTop" …>  
    <TextDecorator Name="TargetRoleName"   />  
  </ConnectorHasDecorators>  
  <ConnectorHasDecorators Position="SourceTop" …>  
    <TextDecorator Name="SourceRoleName"   />  
  </ConnectorHasDecorators>  
</Connector>  
```  
  
## <a name="shapes-and-connectors"></a>シェイプとコネクタ  
 シェイプとコネクタの定義は、ドメイン クラスから属性と子ノードを継承し、さらに次の属性を定義します。  
  
-   `Color` 属性および `Line``Style` 属性。  
  
-   **ExposesFillColorAsProperty**といくつかのような属性。 これらのブール属性により、対応するプロパティをユーザーが変更できるようになります。 一般に、言語ユーザーは、ダイアグラムの図形をクリックすると、プロパティに表示される、**プロパティ**ウィンドウは、図形がマップされているドメイン クラスのインスタンスのものです。 `ExposesFillColorAsProperty` が true に設定されている場合、シェイプ自体のプロパティも表示されます。  
  
-   **ShapeHasDecorators**します。 この属性のインスタンスは、テキスト、アイコン、および展開/折りたたみデコレータごとに生成されます。 (DslDefinition.dsl ファイルでは、`ShapeHasDecorators` は `UseFullForm` が true に設定されたリレーションシップです。)  
  
## <a name="shape-maps"></a>シェイプ マップ  
 シェイプ マップは、特定のドメイン クラスのインスタンス (シェイプによって表される) が画面上にどのように表示されるかを決定します。 シェイプ マップとコネクタ マップはいずれも DslDefinition.dsl ファイルの `Diagram` セクションの下に記述されます。  
  
 次の例に示すように、`ShapeMap` 要素には最小限でもドメイン クラスのモニカー、シェイプのモニカー、および `ParentElementPath` 要素が含まれています。  
  
```  
<ShapeMap>  
  <DomainClassMoniker Name="InPort" />  
  <ParentElementPath>  
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>  
  </ParentElementPath>  
  <PortMoniker Name="InPortShape" />  
</ShapeMap>  
```  
  
 `ParentElementPath` 要素の主な機能は、同じクラスのオブジェクトをコンテキストに応じて異なるシェイプとして表示できるようにすることです。 たとえば `InPort` をコメントに埋め込むこともできる場合、`InPort` をその目的で異なるシェイプとして表示できます。  
  
 次に、シェイプがその親とどのように関連しているかがパスによって決まります。 DslDefinition.dsl ファイルでは、シェイプ間の埋め込み構造は定義されません。 シェイプ マップから構造を推測する必要があります。 シェイプの親は、親要素パスが示すドメイン要素にマップされているシェイプです。 この場合、パスは `InPort` が属するコンポーネントを識別します。 別のシェイプ マップでは、Component クラスは ComponentShape にマップされています。 したがって新しい `InPort` シェイプは、そのコンポーネントの `ComponentShape` の子シェイプになります。  
  
 代わりに、図に InPort シェイプをアタッチした場合は、親要素パスは、図にマップされているコンポーネント モデルへの別のステップをとる必要があります。  
  
```  
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel  
```  
  
 このモデルのルートにはシェイプ マップはありません。 代わりに、ルートは `Class` 要素を持つ図から直接参照されます。  
  
```  
<Diagram Name="ComponentDiagram" >  
    <Class>  
      <DomainClassMoniker Name="ComponentModel" />  
    </Class>…  
```  
  
### <a name="decorator-maps"></a>デコレータ マップ  
 デコレータ マップにより、マップ先クラスのプロパティがシェイプのデコレータに関連付けられます。 プロパティが列挙型またはブール型の場合、デコレータが表示されるかどうかはプロパティの値によって決まります。 デコレータがテキスト デコレータの場合、プロパティの値を表示でき、ユーザーがその値を編集できます。  
  
### <a name="compartment-shape-maps"></a>コンパートメント シェイプ マップ  
 コンパートメント シェイプ マップは、シェイプ マップのサブタイプです。  
  
## <a name="connector-maps"></a>コネクタ マップ  
 最小のコネクタ マップは、1 つのコネクタと 1 つのリレーションシップを参照します。  
  
```  
<ConnectorMap>  
  <ConnectorMoniker Name="CommentLink" />  
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />  
</ConnectorMap>  
```  
  
 コネクタ マップにはデコレータ マップを含めることもできます。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)   
 [モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md)



