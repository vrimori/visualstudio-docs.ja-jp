---
title: "Visual Studio Modelbus を使用して、モデルの統合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# Visual Studio Modelbus を使用して、モデルの統合
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus はモデルにモデル間およびその他のツールのリンクを作成するためのメソッドを提供します。 たとえば、ドメイン固有言語 \(DSL\) モデルと UML モデルを関連付けることができます。 Dsl の統合セットを作成することができます。  
  
 ModelBus を使用して、モデルまたはモデル内の特定の要素の一意の参照を作成できます。 この参照は別のモデル内の要素のなど、モデルの外部に格納できます。 後で何度では、ツールは、要素へのアクセスを取得する必要がある場合は、モデル バス インフラストラクチャが適切なモデルを読み込むし、要素を返します。 する場合は、ユーザーに、モデルを表示できます。 ファイルは、以前の場所にアクセスできない場合、は、ModelBus はそれを検索するユーザーを要求します。 ユーザーには、ファイルが検出されると、ModelBus はそのファイルへのすべての参照を修正します。  
  
> [!NOTE]
>  現在の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus、リンクされたモデルの実装は、同じアイテムである必要があります [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションです。  
  
 詳細およびサンプル コードでは、参照してください。  
  
-   [方法: ドラッグ アンド ドロップ ハンドラーを追加する](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Modeling SDK for Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> DSL にアクセスするため  
 モデルまたはその要素への ModelBus 参照を作成するには、DSL の ModelBusAdapter を定義する必要があります。 これを行う最も簡単な方法が使用するには、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] モデル バス拡張機能は、コマンドを DSL デザイナーに追加します。  
  
###  <a name="expose"></a> DSL 定義をモデル バスを公開するには  
  
1.  ダウンロードして、既にインストールしていない場合は、Visual Studio モデル バス拡張機能をインストールします。 詳細については、次を参照してください。 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)します。  
  
2.  DSL 定義ファイルを開きます。 デザイン サーフェイスを右クリックし、をクリックし、 **Modelbus の有効化**します。  
  
3.  ダイアログ ボックスで選択 **この DSL を ModelBus に公開する**します。 この DSL のモデルを公開して、他の Dsl への参照を使用する場合は、両方のオプションを選択できます。  
  
4.  **\[OK\]** をクリックします。 新しいプロジェクト"ModelBusAdapter"が DSL ソリューションに追加されます。  
  
5.  テキスト テンプレートから DSL にアクセスする場合は、新しいプロジェクトで AdapterManager.tt を変更する必要があります。 コマンドとイベント ハンドラーなどの他のコードから DSL にアクセスする場合は、この手順を省略します。 詳細については、「[テキスト テンプレートでの Visual Studio ModelBus の使用](../modeling/using-visual-studio-modelbus-in-a-text-template.md)」を参照してください。  
  
    1.  AdapterManagerBase の基底クラスを変更する <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>です。  
  
    2.  ファイルの末尾付近のクラス AdapterManager の前にこの追加の属性を挿入します。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  参照の ModelBusAdapter プロジェクトで追加 **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**します。  
  
     テキスト テンプレートとその他のコードの両方の DSL にアクセスする場合は、2 つのアダプター、いずれかの未変更の状態および更新する必要があります。  
  
6.  クリックして **すべてテンプレートが変換**します。  
  
7.  ソリューションをリビルドします。  
  
 この DSL のインスタンスを開く modelbus なっています。  
  
 フォルダー `ModelBusAdapters\bin\*` によってビルドされたアセンブリを含む、 `Dsl` プロジェクトおよび `ModelBusAdapters` プロジェクトです。 この DSL を別の DSL から参照するには、これらのアセンブリをインポートする必要があります。  
  
### 要素を参照できることを確認  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus アダプターでは、要素の guid を使用して、既定でそれを識別します。 これらの識別子は、モデル ファイルのため永続化する必要があります。  
  
##### その要素の Id が保持されることを確認するには  
  
1.  DslDefinition.dsl を開きます。  
  
2.  DSL エクスプ ローラーで、 **Xml Serialization Behavior**, 、し **クラスのデータ**します。  
  
3.  モデル バスを作成する各クラスに次のように参照します。  
  
     クラスのノードをクリックし、\[プロパティ\] ウィンドウのことを確認して **Id のシリアル化** に設定されている `true`します。  
  
 または、guid ではなく要素を識別するために、要素名を使用する場合、生成されたアダプターの部分をオーバーライドできます。 アダプター クラスに次のメソッドをオーバーライドします。  
  
-   オーバーライド `GetElementId` を使用する識別子を返します。 参照を作成するときに、このメソッドが呼び出されます。  
  
-   オーバーライド `ResolveElementReference` モデル バス参照から正しい要素を検索します。  
  
##  <a name="editRef"></a> 別の DSL から DSL にアクセスします。  
 モデル バス参照を格納するには、DSL でドメイン プロパティと、それらを使用するカスタム コードを記述することができます。 ユーザーがモデル ファイルとその中の要素を選択して、モデル バス参照を作成することもできます。  
  
 別の DSL への参照を使用する DSL を有効にする必要があります最初に、 *コンシューマー* モデル バス参照のです。  
  
#### 公開されている DSL への参照を使用する DSL を有効にするには  
  
1.  DSL 定義図で、図の主な部分を右クリックし、クリックして **Modelbus の有効化**します。  
  
2.  ダイアログ ボックスで選択 **モデル バス参照を使用するには、このモデルを有効にする**します。  
  
3.  利用する DSL の Dsl プロジェクトでは、プロジェクトの参照に、次のアセンブリを追加します。 公開されている DSL の ModelBusAdapter\\bin\\ \* ディレクトリにこれらのアセンブリ \(.dll ファイル\) を紹介します。  
  
    -   例については、公開されている DSL アセンブリ **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   公開されているモデル バス アダプター アセンブリがたとえば **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  次の .NET アセンブリを利用する DSL プロジェクトのプロジェクト参照に追加します。  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### ドメイン プロパティに、モデル バス参照を格納するには  
  
1.  利用する DSL の DSL 定義では、ドメイン クラスにドメイン プロパティを追加し、その名前を設定します。  
  
2.  \[プロパティ ウィンドウで選択すると、ドメイン プロパティを使用して設定 **型** に `ModelBusReference`します。  
  
 この段階で、プログラム コードは、プロパティの値を設定できますが、プロパティ ウィンドウでは、読み取り専用です。  
  
 特殊な ModelBus 参照エディターを使用してプロパティを設定できます。 このエディターの 2 つのバージョンまたは *ピッカー:* いずれかにより、ユーザーがモデル ファイルを選択でき、その他のユーザーがモデル ファイルと、モデル内の要素を選択します。  
  
#### モデル バス参照をドメイン プロパティに設定するユーザーを許可するには  
  
1.  ドメイン プロパティを右クリックし、 **編集 ModelBusReference 固有プロパティ**します。 ダイアログ ボックスが開きます。 これは、 *モデル バス ピッカー*します。  
  
2.  適切な選択 **modelbusreference の種類\]**: モデルまたはモデル内の要素。  
  
3.  ファイル ダイアログ フィルター文字列を文字列入力など `Family Tree files |*.ftree`します。 公開される DSL のファイル拡張子を置き換えます。  
  
4.  モデル内の要素を参照することを選択する場合は、ユーザーが選択すると、たとえば Company.FamilyTree.Person 型のリストを追加できます。  
  
5.  をクリックして **OK**, 、\] をクリックし、 **すべてのテンプレートの変換** ソリューション エクスプ ローラーのツールバー。  
  
    > [!WARNING]
    >  場合は、有効なモデルまたはエンティティを選択していない、\[ok\] ボタン効果はありません、場合でも、有効になっている場合があります。  
  
6.  Company.FamilyTree.Person などのターゲット型の一覧を指定した場合、必要があります、アセンブリ参照を追加する、DSL プロジェクト ターゲット DSL、Company.FamilyTree.Dsl.dll などの DLL の参照  
  
#### モデル バス参照をテストするには  
  
1.  公開され、コンシューマー側の両方の Dsl をビルドします。  
  
2.  F5 キーまたは ctrl キーを押しながら f5 キーを押して、Dsl のいずれかの実験モードで実行します。  
  
3.  デバッグ プロジェクトの実験用インスタンスで [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、各 DSL のインスタンスであるファイルを追加します。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus は、同じアイテムであるモデルへの参照を解決できるだけ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションです。 たとえば、ファイル システムの別の部分に、モデル ファイルへの参照を作成できません。  
  
4.  公開されている DSL のインスタンスにいくつかの要素およびリンクを作成し、保存します。  
  
5.  利用する DSL のインスタンスを開き、モデル バス参照プロパティを持つモデル要素を選択します。  
  
6.  \[プロパティ\] ウィンドウで、モデル バス参照プロパティをダブルクリックします。 ピッカー ダイアログが開きます。  
  
7.  クリックして **参照** 公開されている DSL のインスタンスを選択します。  
  
     ピッカーがすることもできますモデルでは、項目を選択して要素固有モデル バス参照の種類を指定した場合。  
  
## プログラム コードで参照を作成します。  
 作成するモデルまたはモデル内の要素への参照を格納する場合、 `ModelBusReference`です。 2 種類の `ModelBusReference`: モデル参照と要素の参照。  
  
 モデルの参照を作成する必要があります、モデルは、インスタンスと、ファイル名を DSL の AdapterManager または [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] モデルのプロジェクト項目。  
  
 要素の参照を作成するには、モデル ファイルとを参照する要素に、アダプターが必要です。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus、参照を作成するアイテムにのみ、同じ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションです。  
  
### 公開されている DSL アセンブリをインポートします。  
 利用するプロジェクトでは、公開されている DSL の DSL と ModelBusAdapter アセンブリへのプロジェクト参照を追加します。  
  
 たとえば、ModelBus References を MusicLibrary DSL の要素に格納するとします。 ModelBus References は FamilyTree DSL の要素を参照してください。`Dsl` 参照設定\] ノードには、MusicLibrary ソリューションのプロジェクトは、次のアセンブリへの参照を追加します。  
  
-   Fabrikam.FamilyTree.Dsl.dll \- 公開されている DSL。  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll \- 公開されている DSL の ModelBus アダプター。  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 これらのアセンブリを参照して、 `ModelBusAdapters` 公開されている DSL のプロジェクトで、 `bin\*`です。  
  
 参照を作成するコード ファイルでは、これらの名前空間をインポートする必要が通常。  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### モデルへの参照を作成するには  
 モデルの参照を作成するには、公開されている DSL の AdapterManager にアクセスし、モデルへの参照の作成に使用します。 いずれか、ファイル パスを指定する、または `EnvDTE.ProjectItem`です。  
  
 AdapterManager から、モデルの個々 の要素へのアクセスを提供するアダプターを取得できます。  
  
> [!NOTE]
>  関連付けが完了したら、Adapter を破棄する必要があります。 これを実現する最も簡単な方法は、 `using` ステートメントです。 次に例を示します。  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 使用したい場合 `modelReference` を外部の型を持つドメイン プロパティに格納した後で `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 のこのドメイン プロパティの編集を許可するには使用 `ModelReferenceEditor` 、Editor 属性のパラメーターとして。 詳細については、次を参照してください。 [の参照を編集するアクセス許可](#editRef)します。  
  
### 要素への参照を作成するには  
 作成し、参照を解決するのには、モデル用に作成したアダプターを使用できます。  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 使用したい場合 `elementReference` を外部の型を持つドメイン プロパティに格納した後で `ModelBusReference`します。 の編集を許可するには使用 `ModelElementReferenceEditor` 、Editor 属性のパラメーターとして。 詳細については、次を参照してください。 [の参照を編集するアクセス許可](#editRef)します。  
  
### 参照を解決します。  
 ある場合、 `ModelBusReference` \(MBR\)、モデルまたは参照するモデル要素を取得できます。 図または他のビューの要素が存在している場合は、ビューを開くし、要素を選択します。  
  
 MBR からアダプターを作成できます。 アダプターからは、モデルのルートを取得できます。 モデル内の特定の要素を参照する Mbr を解決できます。  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### テキスト テンプレート内の ModelBus References を解決するのには  
  
1.  アクセスする DSL には、テキスト テンプレートによるアクセス用に構成された ModelBus Adapter が必要です。 詳細については、「[DSL にアクセスするため](#provide)」を参照してください。  
  
2.  通常、ソース DSL に格納されている DSL モデル バス参照 \(MBR\) を使用してターゲットをアクセスする場合は。 そのため、テンプレートには、MBR を解決するのには、ソース DSL とコードのディレクティブが含まれています。 テキスト テンプレートの詳細については、次を参照してください。 [ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)します。  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 詳細とチュートリアルでは、次を参照してください。 [テキスト テンプレートでの Visual Studio ModelBus の使用](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## ModelBusReference のシリアル化します。  
 格納する場合、 `ModelBusReference` \(MBR\) 形式では、文字列のシリアル化できますが。  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 このような方法でシリアル化される MBR はコンテキストに依存しません。 単純なファイル ベース モデル バス アダプターを使用している場合、MBR には、絶対ファイル パスが含まれています。 これは、インスタンス モデル ファイルは移動されない場合に不十分です。 ただし、モデル ファイル通常は内の項目、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトです。 ユーザーはプロジェクト全体をファイル システムのさまざまな部分に移動できると期待しています。 期待がわかるソース管理対象のプロジェクトを保存して開くには別のコンピューターでできるようにします。 したがって、パス名はファイルを含むプロジェクトの場所に対する相対シリアル化する必要があります。  
  
### 指定されたファイル パスを基準にシリアル化します。  
 A `ModelBusReference` を含む、 `ReferenceContext`, 、基準となることをシリアル化するファイルのパスなどの情報を格納しているディクショナリであります。  
  
 パス相対シリアル化。  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 文字列から、参照を取得します。  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### その他のアダプターにより作成された ModelBusReferences  
 次の情報は、独自のアダプターを作成する場合に便利です。  
  
 A `ModelBusReference` \(MBR\) は、2 つの部分で構成されています: MBR ヘッダーは、モデル バスにより逆シリアル化、および特定のアダプター マネージャーにより処理されるアダプター固有です。 これにより、独自のアダプター シリアル化形式を提供できます。 など、ファイルではなく、データベースを参照することがまたはアダプター参照の追加情報を格納できます。 独自のアダプターの追加情報を配置できます、 `ReferenceContext`です。  
  
 MBR を逆シリアル化するときに、ReferenceContext は、MBR オブジェクトに格納されますを指定する必要があります。 MBR をシリアル化する場合、文字列の作成を支援する、保存された ReferenceContext はアダプターによって使用されます。 逆シリアル化された文字列では、ReferenceContext 内のすべての情報は含まれません。 たとえば、単純なファイルベースのアダプターで、ReferenceContext にはシリアル化された MBR 文字列に格納されていないルート ファイル パスが含まれます。  
  
 MBR は 2 つの段階で逆シリアル化します。  
  
-   `ModelBusReferencePropertySerializer` MBR ヘッダーを処理する標準のシリアライザーです。 標準の DSL を使用して `SerializationContext` に格納されているプロパティ バッグ、 `ReferenceContext` キーを使用して `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`します。 具体的には、 `SerializationContext` のインスタンスを含める必要があります `ModelBus`します。  
  
-   ModelBus Adapter は MBR のアダプター固有の部分について説明します。 MBR の ReferenceContext に保存された追加の情報を使用できます。 単純なファイルベースのアダプターは、キーを使用してルート ファイル パスを保持 `FilePathLoadContextKey` と `FilePathSaveContextKey`です。  
  
     モデル ファイル内のアダプター参照を使用している場合にのみ逆シリアル化します。  
  
## モデルを作成するには  
  
### 作成する、オープン、およびモデルの編集  
 次のフラグメントは、VMSDK Web サイトの State Machine サンプルから取得されます。 これは、ModelBusReferences を作成し、モデルを開くと、モデルに関連付けられているダイアグラムを取得するの使用方法を示します。  
  
 このサンプルでは、ターゲット DSL の名前は StateMachine です。 いくつかの名前は、モデル クラスの名前や ModelBusAdapter の名前など、そこから派生します。  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## 参照の検証  
 BrokenReferenceDetector は ModelBusReferences を保持できるストアにすべてのドメインのプロパティをテストします。 アクションを呼び出す任意のアクションが検出される場合に指定されます。 これは、検証メソッドに特に便利です。 次の検証メソッドは、ストア、モデルの保存の試みをテストして、エラー ウィンドウで壊れている参照を報告します。  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## ModelBus 拡張機能によって実行されるアクション  
 次の情報は、これが重要ではありませんが、ModelBus を頻繁に使用する場合に便利です。  
  
 ModelBus 拡張機能は、DSL ソリューションで、次の変更を加えます。  
  
 DSL 定義図を右クリックしたときにをクリックして **Modelbus の有効化**, 、し、\[ **この DSL が ModelBus を利用を有効にする**:  
  
-   DSL プロジェクト内の参照に追加 **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   DSL 定義で、外部型参照を追加します。 `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`します。  
  
     内の参照を確認できます **DSL エクスプ ローラー**, \[ **ドメイン型**します。 外部型参照を手動で追加するには、ルート ノードを右クリックします。  
  
-   新しいテンプレート ファイルを追加すると、 **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**します。  
  
 ときに ModelBusReference ドメイン プロパティの型を設定し、プロパティを右クリックし、\] をクリックして **\[ModelBusReference 固有プロパティ**:  
  
-   いくつかの CLR 属性は、ドメイン プロパティに追加されます。 \[プロパティ\] ウィンドウの Custom Attributes フィールドには、それらを表示できます。**Dsl\\GeneratedCode\\DomainClasses.cs**, 、プロパティ宣言上の属性を確認できます。  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 DSL 定義図右クリックして、クリックして **ModelBus の有効化**, を選択して **この DSL を ModelBus に公開**:  
  
-   新しいプロジェクト `ModelBusAdapter` ソリューションに追加します。  
  
-   参照を `ModelBusAdapter` に追加、 `DslPackage` プロジェクトです。`ModelBusAdapter` 参照を持つ、 `Dsl` プロジェクトです。  
  
-   **DslPackage\\source.extention.tt**, 、`|ModelBusAdapter|` を MEF コンポーネントとして追加します。  
  
## 参照  
 [方法: プログラム コード内のファイルからモデルを開く](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [UML モデルを他のモデルおよびツールと統合する](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [方法: ドラッグ アンド ドロップ ハンドラーを追加する](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [テキスト テンプレートでの Visual Studio ModelBus の使用](../modeling/using-visual-studio-modelbus-in-a-text-template.md)