---
title: "テキスト テンプレートでの Visual Studio ModelBus の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# テキスト テンプレートでの Visual Studio ModelBus の使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 参照を含むモデルを読み込むテキスト テンプレートを作成してターゲット モデルにアクセスするための参照を解決する場合があります。  この場合はテキスト テンプレートと参照先のドメイン固有言語を使用 \(DSLs\) する必要があります :  
  
-   参照先のある DSL はテキスト テンプレートからアクセスするように構成されている ModelBus のアダプターが必要です。  他のコードからアクセスDSL を再構成されたアダプターは ModelBus 標準のアダプターに加えて必要です。  
  
     アダプターは <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> マネージャーから継承し属性 `[HostSpecific(HostName)]` が必要です。  
  
-   テンプレートは <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation> から継承する必要があります。  
  
> [!NOTE]
>  ModelBus 参照を含まない DSL モデルを読み込む場合はDSL のプロジェクトで生成されたディレクティブ プロセッサを使用できます。  詳細については、「[テキスト テンプレートからモデルへのアクセス](../modeling/accessing-models-from-text-templates.md)」を参照してください。  
  
 テキスト テンプレートの詳細については、「[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)」を参照してください。  
  
## テキスト テンプレートからアクセスするためのモデル バス アダプターの作成  
 テキスト テンプレートの ModelBus 参照を解決するには対象の DSL は互換性のあるアダプターが必要です。  テキスト テンプレートは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のドキュメントのエディターから別の AppDomain で実行するためアダプターはDTE によりアクセスする代わりにモデルを読み込む必要があります。  
  
#### テキスト テンプレートと互換性がある ModelBus のアダプターを作成するには  
  
1.  ターゲットの DSL のソリューションに **ModelBusAdapter** プロジェクトがない場合はModelbus の拡張機能の追加ウィザードを使用して 1 個の作成 :  
  
    1.  まだ行っていない場合は[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 拡張機能をダウンロードしてインストールします。  詳細については" " を参照してください。[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)  
  
    2.  DSL の定義ファイルを開きます。  デザイン サーフェイスを右クリックしを ENT0ENT \[\] をクリックします。  
  
    3.  ダイアログ ボックスで\[入力\] ENT0ENT を選択します。  このに DSL モデルを公開し他の DSL への参照を実装する場合は両方のオプションを選択できます。  
  
    4.  **\[OK\]** をクリックします。  新しいプロジェクトは」 「 ModelBusAdapter DSL のソリューションに追加されます。  
  
    5.  \[ENT0ENT\] をクリックします。  
  
    6.  ソリューションをビルドし直します。  
  
2.  重複のプロジェクト **ModelBusAdapter** テキスト テンプレートと他のコードからの DSL はコマンドと同じようにアクセスするには :  
  
    1.  Windows エクスプローラーで**ModelBusAdapter.csproj** を含むフォルダーをコピーして貼り付けます。  
  
    2.  プロジェクト ファイルの名前を変更します \(**T4ModelBusAdapter.csproj**\)。  
  
    3.  **ソリューション エクスプローラー**  でソリューション ノードを右クリックし **追加**  をポイントし\[ENT2ENT\] をクリックします。  新しいアダプターのプロジェクト**T4ModelBusAdapter.csproj** を探します。  
  
    4.  新しいプロジェクトの `*.tt` の各ファイルで名前空間を変更します。  
  
    5.  ソリューション エクスプローラーで新しいプロジェクトを右クリックし\[プロパティ\] をクリックします。  プロパティ エディターで生成されるアセンブリおよび既定の名前空間の名前を変更します。  
  
    6.  DslPackage のプロジェクトでは両方のアダプターへの参照が新しいアダプターのプロジェクトへの参照を追加します。  
  
    7.  DslPackage \\ source.extension.tt では新しいアダプターのプロジェクトを参照する行を追加します。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **すべてのテンプレートの変換 \(&T\)**ソリューションをビルドし直し。  ビルド エラーが発生することはありません。  
  
3.  新しいアダプターのプロジェクトでは次のアセンブリへの参照を追加します :  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  AdapterManager.tt:  
  
    -   <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>AdapterManagerBase から継承するようにの宣言を変更します。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   ファイルの末尾の近くでHostSpecific の属性を AdapterManager クラスの前に置き換えます。  次の行を削除します :  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         次の行を挿入します :  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         この属性は modelbus コンシューマーがアダプターを検索するときに使用できるアダプターのセットをフィルター処理します。  
  
5.  **すべてのテンプレートの変換 \(&T\)**ソリューションをビルドし直し。  ビルド エラーが発生することはありません。  
  
## ModelBus 参照を解決できるテキスト テンプレートを作成する  
 通常は「」の DSL のソース ファイルを読み取り生成するテンプレートから開始します。  このテンプレートは [テキスト テンプレートからモデルへのアクセス](../modeling/accessing-models-from-text-templates.md) で説明されている方法でソース モデル ファイルを読み取るソースの DSL のプロジェクトで生成されるディレクティブを使用します。  ただしソースの DSL ターゲットは「」の DSL の ModelBus への参照が含まれています。  この参照を解決し対象の DSL のテンプレート コードがアクセスできるようにする必要があります。  これらの手順に従ってテンプレートを変更する必要があります :  
  
-   <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation> にテンプレートの基本クラスを変更します。  
  
-   テンプレート ディレクティブに `hostspecific="true"` を追加します。  
  
-   ターゲットの DSL およびアダプターのアセンブリへの参照をModelBus を有効にするに追加します。  
  
-   ターゲットの DSL の一部として生成されるディレクティブは必要ではありません。  
  
```  
<#@ template debug="true" hostspecific="true" language="C#"  
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
<#@ output extension=".txt" #>  
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>  
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>  
<#@ assembly name = "System.Core" #>  
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
<#@ import namespace="Company.TargetDsl" #>  
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>  
<#@ import namespace="System.Linq" #>  
<#  
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.  
  // In the source DSL Definition, the root element has a model reference:  
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)   
  {if (adapter != null)  
   {  
      // Get the root of the target model:  
      TargetRoot target = adapter.ModelRoot;  
    // The source DSL Definition has a class "SourceElement" embedded under the root.  
    // (Let’s assume they’re all in the same model file):  
    foreach (SourceElement sourceElement in source.Elements)  
    {  
      // In the source DSL Definition, each SourceElement has a MBR property:  
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;  
      // Resolve the target model element:   
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);   
#>  
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.  
<#  
    }  
  }}  
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename   
  // from a path that is relative to the text template.  
#>  
  
```  
  
 このテキスト テンプレートを実行すると`SourceDsl` のディレクティブはファイル `Sample.source` を読み込みます。  テンプレートは `this.ModelRoot` でそのモデル内の要素にアクセスできます。  コードではDSL のドメイン クラスとプロパティを使用できます。  
  
 またテンプレートは ModelBus 参照を解決できます。  ターゲット モデルへの基準点がアセンブリ ディレクティブをコードではそのモデルの DSL のドメイン クラスとプロパティ使用してします。  
  
-   DSL のプロジェクトで生成されたディレクティブを使用すると次のようになります。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   ModelBus へのアクセスを取得するに `this.ModelBus` を使用します。  
  
## チュートリアル : ModelBus を使用してテキスト テンプレートをテストします。  
 このチュートリアルでは次の手順を行います。:  
  
1.  DSL 2 を構築します。  DSL 1 *コンシューマーに* 他の DSL を参照できる `ModelBusReference` のプロパティ  *プロバイダーが*  あります。  
  
2.  プロバイダーの ModelBus の 2 種類のアダプターを作成します : テキスト テンプレートによるアクセスの 1 つが通常のコードの他。  
  
3.  単一の実験プロジェクトの DSL モデルのインスタンスを作成します。  
  
4.  他のモデルを指す 1 種類のモデルのドメインのプロパティを設定します。  
  
5.  指すモデルを開くダブル クリック ハンドラーを記述します。  
  
6.  モデル最初のモデルを読み込みそのへの参照に従いそのモデルを読み取ることができるテキスト テンプレートを記述します。  
  
#### ModelBus にアクセスできる DSL を構築します。  
  
1.  新しい DSL のソリューションを作成します。  この例ではタスクのフローのソリューション テンプレートを選択します。  `MBProvider` に言語名および 「」 .provide にファイル拡張子を設定します。  
  
2.  ユース ケース図の定義は上の方にある右クリックし\[\] をクリック ENT0ENT の図の空白部分を示します。  
  
    -   **\*\*\* Enable Modelbus \*\*\*** がない場合はVMSDK ModelBus 拡張機能をダウンロードしインストールする必要があります。  一つの VMSDK サイトの下にあります : [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)。  
  
3.  \[入力\] ENT0ENT ダイアログ ボックスでENT1ENT \[\] を選択し次に \[ENT3ENT\] をクリックします。  
  
     新しい `ModelBusAdapter`プロジェクトがソリューションに追加されます。  
  
 ModelBus これによりテキスト テンプレートにアクセスできる DSL があります。  モデル ファイルのエディターの AppDomain で実行するコマンドイベント ハンドラーまたは規則のコードにある要素への参照を解決できます。  ただしテキスト テンプレートは別の AppDomain で編集するときに実行しモデルにアクセスできません。  テキスト テンプレートからこの DSL の ModelBus への参照にアクセスする場合は別の ModelBusAdapter が必要です。  
  
#### テキスト テンプレート用に構成された ModelBus のアダプターを作成するには  
  
1.  Windows エクスプローラーでModelBusAdapter.csproj を含むフォルダーをコピーして貼り付けます。  
  
     フォルダー T4ModelBusAdapter を付けます。  
  
     プロジェクト ファイル T4ModelBusAdapter.csproj の名前を変更します。  
  
2.  ソリューション エクスプローラーでMBProvider のソリューションに T4ModelBusAdapter を追加します。  ソリューション ノードを右クリックし **追加**  をポイントし\[ENT1ENT\] をクリックします。  
  
3.  T4ModelBusAdapter のプロジェクト ノードを右クリックし\[プロパティ\] をクリックします。  プロジェクトのプロパティ ウィンドウで`Company.MBProvider.T4ModelBusAdapters` に  **アセンブリ名**  と  **既定の名前空間**  を変更します。  
  
4.  T4ModelBusAdapter の各 \*.tt ファイルの行は次のように名前空間の最後の部分に挿入 「 T4 」。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  `DslPackage` のプロジェクトでは`T4ModelBusAdapter` へのプロジェクト参照を追加します。  
  
6.  DslPackage \\ source.extension.tt では`<Content>` の下に次の行を追加します。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  `T4ModelBusAdapter` のプロジェクトではへの参照を追加します : **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  開いている T4ModelBusAdapter \\ AdapterManager.tt:  
  
    1.  <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> に AdapterManagerBase の基本クラスを変更します。  ファイルのこの部分では次のようになります。  
  
        ```  
        namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters  
        {  
            /// <summary>  
            /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer  
            /// </summary>  
            public partial class <#= dslName #>AdapterManagerBase   
            : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager  
            {  
  
        ```  
  
    2.  ファイルの末尾の近くでクラス AdapterManager の前に次の属性を挿入します。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         結果は次のようになります。  
  
        ```  
        /// <summary>  
        /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter  
        /// </summary>  
        [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]  
        [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]  
        [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]  
        [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]  
        public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase  
        {  
        }  
  
        ```  
  
9. ソリューション エクスプローラーのタイトル バーに ENT0ENT \[\] をクリックします。  
  
10. ソリューションをビルドし直します。  F5 をクリックします。  
  
11. DSL が F5 キーを押しても動作することを確認します。  テスト プロジェクトで`Sample.provider` を開きます。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用のインスタンスを閉じます。  
  
 テキスト テンプレートと通常のコードでDSL の ModelBus への参照は解決できます。  
  
#### ModelBus 参照のドメインがDSL を構築します。  
  
1.  最小限の言語のソリューション テンプレートを使用して新しい DSL を作成します。  言語 MBConsumer を付け「」 .consume にファイル拡張子を設定します。  
  
2.  DSL のプロジェクトではMBProvider の DSL のアセンブリへの参照を追加します。  `MBConsumer\Dsl\References` を右クリックしを ENT0ENT \[\] をクリックします。  \[入力\] ENT2ENT タブので`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll` を探します。  
  
     これにより他の DSL を使用するコードを作成することができます。  複数のユースへの参照を作成する場合はそれらも追加します。  
  
3.  DSL 定義図で図を右クリックしを ENT0ENT \[\] をクリックします。  ダイアログ ボックスで\[入力\] ENT0ENT を選択します。  
  
4.  クラス `ExampleElement` でプロパティ ウィンドウに新しいドメイン `MBR` のプロパティを設定します `ModelBusReference` に型を追加します。  
  
5.  図のドメインのプロパティを右クリックしを ENT0ENT \[\] をクリックします。  ダイアログ ボックスで\[入力\] ENT0ENT を選択します。  
  
     次にダイアログのファイル フィルターを設定します。  
  
     `Provider File|*.provide`  
  
     後半部分文字列 「 &#124; 」ファイルの選択ダイアログ ボックスのフィルターです。  \*.\* を使用してファイルを許可するように設定できます。  
  
     \[入力\] ENT0ENT リストではプロバイダー \(DSL\) Company.MBProvider.Task に 1 個の鉱石名前のドメイン クラスを詳細に入力します。  これらは抽象クラスでもできます。  リストを空白にするとユーザーは要素への参照を設定できます。  
  
6.  ダイアログおよび  **すべてのテンプレートの変換 \(&T\)** を閉じます。  
  
 別の DSL の要素への参照を含めることができる DSL を作成します。  
  
#### ソリューション内の別のファイルへの ModelBus 参照を作成します。  
  
1.  MBConsumer のソリューションではF5 キーを押します。  **MBConsumer\\Debugging** プロジェクトの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンス。  
  
2.  **MBConsumer\\Debugging** プロジェクトに Sample.provide のコピーを追加します。  これは ModelBus 参照が同じソリューション ファイルを参照する必要があるためです。  
  
    1.  デバッグのプロジェクトを右クリックし **追加**  をポイントし\[ENT1ENT\] をクリックします。  
  
    2.  \[入力\] ENT0ENT ダイアログ ボックスので **すべてのファイル \(\*.\*\)** にフィルターを設定します。  
  
    3.  `MBProvider\Debugging\Sample.provide` に移動し\[ENT0ENT\] をクリックします。  
  
3.  `Sample.consume` を起動します。  
  
4.  プロパティ ウィンドウの 1 種類の図形もENT0ENT \[\] をクリックします MBR のプロパティをクリックします。  ダイアログ ボックスで`Sample.provide` を ENT2ENT \[\] をクリックしをクリックします。  要素のウィンドウで型のタスクを展開し要素の 1 つがを選択します。  
  
5.  ファイルを保存します。  
  
     \(まだ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスは閉じないでください\)。  
  
 別のモデル内の要素への ModelBus 参照を含むモデルが作成されました。  
  
#### テキスト テンプレートの ModelBus 参照を解決します。  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスでサンプル テキスト テンプレート ファイルを開きます。  内容を次のように設定します。  
  
    ```  
    <#@ template debug="true" hostspecific="true" language="C#"  
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="Company.MBProvider" #>  
    <#  
      // Property provided by the Consumer directive processor:  
      ExampleModel consumerModel = this.ExampleModel;   
      // Iterate through Consumer model, listing the elements:  
      foreach (ExampleElement element in consumerModel.Elements)  
      {  
    #>  
       <#= element.Name #>   
    <#  
        if (element.MBR != null)  
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))  
      {   
              // If we allowed multiple types or DSLs in the MBR, discover type here.  
        Task task = adapter.ResolveElementReference<Task>(element.MBR);  
    #>  
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>  
    <#  
          }  
      }  
    #>  
  
    ```  
  
     次の点に注目してください。  
  
    1.  `template` のディレクティブの `hostSpecific` と `inherits` の属性を設定する必要があります。  
  
    2.  コンシューマーはDSL モデルで生成されたディレクティブ プロセッサを使用して通常の方法でアクセスできます。  
  
    3.  アセンブリとインポート ディレクティブはプロバイダーの DSL の ModelBus と型にアクセスする必要があります。  
  
    4.  多くの MBR は同じモデル要素にリンクすることがわかっている場合はCreateAdapter を呼び出すことをお勧めします。1 回だけ。  
  
2.  テンプレートを保存したとき。  生成されたテキスト ファイルが次のようになっていることを確認します。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### ジェスチャ ハンドラーの ModelBus 参照を解決します。  
  
1.  実行する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスを閉じます。  
  
2.  MBConsumer \\ \\ Dsl Custom.cs という追加しコンテンツを設定します。ファイルを表します。  
  
    ```  
  
    namespace Company.MB2Consume  
    {  
      using Microsoft.VisualStudio.Modeling.Integration;  
      using Company.MB3Provider;  
  
      public partial class ExampleShape  
      {  
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)  
        {  
          base.OnDoubleClick(e);  
          ExampleElement element = this.ModelElement as ExampleElement;  
          if (element.MBR != null)  
          {  
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;  
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))  
            {  
              Task task = adapter.ResolveElementReference<Task>(element.MBR);  
              // Open a window on this model:  
              ModelBusView view = adapter.GetDefaultView();  
              view.Show();  
              view.SetSelection(element.MBR);  
            }  
          }  
        }  
      }  
    }  
  
    ```  
  
3.  Ctrl \+ F5 キーを押します。  
  
4.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスで`Debugging\Sample.consume` を開きます。  
  
5.  1 種類の図形をダブルをクリックします。  
  
     設定がその要素の MBR 場合参照されたモデルが開き参照先の要素が選択されます。  
  
## 参照  
 [Visual Studio Modelbus を使用して、モデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)