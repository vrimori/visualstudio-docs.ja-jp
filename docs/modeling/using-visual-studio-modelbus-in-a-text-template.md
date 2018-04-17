---
title: Visual Studio ModelBus を使用して、テキスト テンプレートで |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9a3cca1ed96cc2190ace1c8e1ece0423221f59f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>テキスト テンプレートでの Visual Studio ModelBus の使用
テキスト テンプレートを含むモデルを読み取ることを記述するかどうかは[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ModelBus を参照して、ターゲットのモデルにアクセスする参照を解決することができます。 その場合は、テキスト テンプレートを使用し、参照先のドメイン固有言語 (Dsl) を調整する必要があります。  
  
-   参照の対象となっている DSL には、テキスト テンプレートからのアクセス用に構成されている ModelBus アダプター必要があります。 アクセスすることも、DSL 他のコードから、再構成されたアダプターが、標準の ModelBus アダプターだけでなく必要です。  
  
     継承する必要があるアダプター マネージャー <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> 、属性が必要と`[HostSpecific(HostName)]`です。  
  
-   テンプレートを継承する必要があります<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>です。  
  
> [!NOTE]
>  DSL モデル ModelBus の参照が含まれていないことを確認するには、DSL プロジェクトで生成されたディレクティブ プロセッサを使用することができます。 詳細については、次を参照してください。[テキスト テンプレートからへのアクセス モデル](../modeling/accessing-models-from-text-templates.md)です。  
  
 テキスト テンプレートの詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して、デザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)です。  
  
## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>テキスト テンプレートからのアクセスのモデル バス アダプターを作成します。  
 テキスト テンプレートで ModelBus の参照を解決するのには、互換性のあるアダプターがターゲット DSL に必要です。 テキスト テンプレートをから別の AppDomain で実行、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターに対しを文書化し、アダプターが DTE を介してアクセスするのではなくモデルを読み込むためにします。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>テキスト テンプレートと互換性がある ModelBus アダプターを作成するには  
  
1.  ターゲットの DSL ソリューションがあるない場合、 **ModelBusAdapter**プロジェクト、Modelbus の拡張ウィザードを使用して 1 つを作成します。  
  
    1.  ダウンロードしてインストール、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus 拡張機能、していない場合。 詳細については、次を参照してください。 [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)です。  
  
    2.  DSL 定義ファイルを開きます。 デザイン サーフェイスを右クリックし、をクリックして**を有効にする Modelbus**です。  
  
    3.  ダイアログ ボックスで選択**、ModelBus をこの DSL を公開する**です。 この DSL をそのモデルを公開し、その他の Dsl への参照を使用する場合は、両方のオプションを選択できます。  
  
    4.  **[OK]**をクリックします。 新しいプロジェクト "ModelBusAdapter" が DSL ソリューションに追加されます。  
  
    5.  をクリックして**すべてのテンプレートを変換**です。  
  
    6.  ソリューションをリビルドします。  
  
2.  重複するテキスト テンプレートと、コマンドなどの他のコードの両方に、DSL をアクセスする場合、 **ModelBusAdapter**プロジェクト。  
  
    1.  Windows エクスプ ローラーにコピーして、含まれているフォルダーを貼り付ける**ModelBusAdapter.csproj**です。  
  
    2.  プロジェクト ファイルの名前 (たとえば、 **T4ModelBusAdapter.csproj**)。  
  
    3.  **ソリューション エクスプ ローラー**ソリューション ノードを右クリックしをポイントし、**追加**、クリックして**既存のプロジェクト**です。 新しいアダプター プロジェクト**T4ModelBusAdapter.csproj**です。  
  
    4.  各`*.tt`ファイル、新しいプロジェクトの名前空間を変更します。  
  
    5.  ソリューション エクスプ ローラーで新しいプロジェクトを右クリックし、[プロパティ] をクリックします。 プロパティ エディターでは、生成されたアセンブリと既定の名前空間の名前を変更します。  
  
    6.  DslPackage プロジェクトでは、新しいアダプター プロジェクトへの参照を追加し、両方のアダプターへの参照があるようにします。  
  
    7.  DslPackage\source.extension.tt では、新しいアダプター プロジェクトを参照する行を追加します。  
  
        ```  
        <MefComponent>|T4ModelBusAdapter|</MefComponent>  
        ```  
  
    8.  **すべてのテンプレートを変換**ソリューションをリビルドします。 ビルド エラーは発生しません。  
  
3.  新しいアダプター プロジェクトでは、次のアセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
         Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
4.  AdapterManager.tt: で  
  
    -   継承するように AdapterManagerBase の宣言を変更する<xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>です。  
  
         `public partial class <#= dslName =>AdapterManagerBase :`  
  
         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`  
  
    -   ファイルの最後に、近く AdapterManager クラスの前に HostSpecific 属性で置き換えます。 次の行を削除します。  
  
         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`  
  
         次の行を挿入します。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         この属性は、modelbus コンシューマーがアダプターを検索するときに使用されるアダプターのセットをフィルター処理します。  
  
5.  **すべてのテンプレートを変換**ソリューションをリビルドします。 ビルド エラーは発生しません。  
  
## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus の参照を解決できるテキスト テンプレートの作成  
 通常、読み込み、「ソース」DSL からファイルを生成するテンプレートを使用して開始します。 このテンプレートに記載されているようにソース モデル ファイルを読み取るソース DSL プロジェクトで生成されたディレクティブを使用して[テキスト テンプレートからへのアクセス モデル](../modeling/accessing-models-from-text-templates.md)です。 ただし、ソース DSL には、"target"DSL へ ModelBus の参照が含まれています。 そのため参照を解決するには、DSL のターゲットにアクセスして、テンプレート コードを有効にします。 そのため調整しなければならない場合、テンプレート、次の手順。  
  
-   テンプレートの基本クラスを変更<xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>です。  
  
-   含める`hostspecific="true"`テンプレート ディレクティブにします。  
  
-   ターゲット DSL およびそのアダプター ModelBus を有効にするには、アセンブリ参照を追加します。  
  
-   ターゲット DSL の一部として生成されるディレクティブが不要です。  
  
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
    // (Let's assume they're all in the same model file):  
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
  
 このテキスト テンプレートを実行すると、`SourceDsl`ディレクティブは、ファイルを読み込みます`Sample.source`です。 テンプレートから、そのモデルの要素にアクセスできます`this.ModelRoot`です。 コードには、ドメイン クラスとその DSL のプロパティを使用できます。  
  
 さらに、テンプレートは ModelBus 参照を解決することができます。 参照は、対象のモデルをポイントして、場所アセンブリ ディレクティブは、ドメイン クラスとそのモデルの DSL のプロパティを使用してコードを使用できます。  
  
-   DSL プロジェクトによって生成されたディレクティブを使用しない場合、次の必要があります。  
  
    ```  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>  
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>  
    ```  
  
-   使用して`this.ModelBus`ModelBus へアクセスを取得します。  
  
## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>チュートリアル: ModelBus を使用するテキスト テンプレートのテスト  
 このチュートリアルでは、次の手順に従います。  
  
1.  2 つの Dsl を構築します。 1 つの DSL、*コンシューマー*が、`ModelBusReference`プロパティその他の DSL の場合を参照できる、*プロバイダー*です。  
  
2.  プロバイダーで次の 2 つの ModelBus アダプターの作成: 他の通常のコードによって、テキスト テンプレートのアクセスのいずれか。  
  
3.  実験用の単一のプロジェクトでの Dsl のインスタンス モデルを作成します。  
  
4.  その他のモデルをポイントする 1 つのモデルでドメインのプロパティを設定します。  
  
5.  指す、モデルを開く をダブルクリック ハンドラーを記述します。  
  
6.  最初のモデルを読み込み、以下の他のモデルへの参照および他のモデルを読み込むことができますをテキスト テンプレートを作成します。  
  
#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>コンストラクトが ModelBus にアクセスする DSL には、  
  
1.  新しい DSL ソリューションを作成します。 この例では、タスク フロー ソリューション テンプレートを選択します。 言語名を設定します`MBProvider`と".provide"にファイル名拡張子。  
  
2.  DSL 定義ダイアグラムで、上部付近れない図の空白部分を右クリックし、をクリックして**を有効にする Modelbus**です。  
  
    -   表示されない場合**を有効にする Modelbus**、ダウンロードして VMSDK ModelBus 拡張機能をインストールする必要があります。 VMSDK サイト上で見つけ: [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579)です。  
  
3.  **Modelbus を有効にする**ダイアログ ボックスで、**この DSL、ModelBus への公開**、クリックして**[ok]**です。  
  
     新しいプロジェクト`ModelBusAdapter`ソリューションに追加します。  
  
 DSL ModelBus を使用してテキスト テンプレートでアクセスできるようになりましたがあります。 参照は、コマンド、イベント ハンドラー、またはルールをモデル ファイル エディターの AppDomain で動作するすべてのコードで解決できます。 ただし、テキスト テンプレートは、別の AppDomain で実行され、編集中の場合、モデルにアクセスできません。 テキスト テンプレートからこの DSL への参照を ModelBus にアクセスする場合は、個別の ModelBusAdapter が必要です。  
  
#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>テキスト テンプレートに構成されている ModelBus アダプターを作成するには  
  
1.  Windows エクスプローラで、コピーして ModelBusAdapter.csproj を含まれているフォルダーを貼り付けます。  
  
     T4ModelBusAdapter フォルダーの名前を指定します。  
  
     T4ModelBusAdapter.csproj プロジェクト ファイルの名前を変更します。  
  
2.  ソリューション エクスプ ローラーで、T4ModelBusAdapter を MBProvider ソリューションに追加します。 ソリューション ノードを右クリックし、**追加**、クリックして**既存のプロジェクト**です。  
  
3.  T4ModelBusAdapter プロジェクト ノードを右クリックし、[プロパティ] をクリックします。 プロジェクトのプロパティ ウィンドウで変更、**アセンブリ名**と**Default Namespace**に`Company.MBProvider.T4ModelBusAdapters`です。  
  
4.  T4ModelBusAdapter で各 *.tt ファイルには、行は、次のようにできるように、名前空間の最後の部分に"T4"を挿入します。  
  
     `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`  
  
5.  `DslPackage`プロジェクト、プロジェクト参照を追加`T4ModelBusAdapter`です。  
  
6.  DslPackage\source.extension.tt の下にある次の行を追加`<Content>`です。  
  
     `<MefComponent>|T4ModelBusAdapter|</MefComponent>`  
  
7.  `T4ModelBusAdapter`プロジェクトの参照を追加する: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**  
  
8.  T4ModelBusAdapter\AdapterManager.tt を開きます。  
  
    1.  AdapterManagerBase の基底クラスを <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> に変更します。 ファイルのこの部分が、次のようになります。  
  
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
  
    2.  ファイルの最後に、近くクラス AdapterManager の前に、次の追加属性を挿入します。  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
         結果には、次のようになります。  
  
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
  
9. をクリックして**すべてのテンプレートの変換**タイトル バーのソリューション エクスプ ローラーでします。  
  
10. ソリューションをリビルドします。 F5 キーをクリックします。  
  
11. F5 キーを押して、DSL が動作していることを確認します。 実験用のプロジェクトで開きます`Sample.provider`です。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用インスタンスを閉じます。  
  
 テキスト テンプレートで、通常のコードでも、この dsl ModelBus 参照を解決ようになりましたことができます。  
  
#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>DSL ModelBus 参照ドメインのプロパティを持つコンス トラクター  
  
1.  新しい DSL を作成するには、最小限の言語のソリューション テンプレートを使用します。 MBConsumer 言語の名前し、".consume"にファイル名拡張子を設定します。  
  
2.  DSL プロジェクトでは、MBProvider DSL アセンブリへの参照を追加します。 右クリック`MBConsumer\Dsl\References` をクリックし、**参照の追加**です。 **参照** タブで、検索 `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`  
  
     これにより、他の DSL を使用するコードを作成することができます。 いくつかの Dsl への参照を作成する場合も追加します。  
  
3.  DSL 定義ダイアグラムでダイアグラムを右クリックし、をクリックして**を有効にする ModelBus**です。 ダイアログ ボックスで選択**、ModelBus を使用するには、この DSL を有効にする**です。  
  
4.  クラスの`ExampleElement`、新しいドメインのプロパティを追加`MBR`、[プロパティ] ウィンドウでその型に設定し、`ModelBusReference`です。  
  
5.  図上のドメインのプロパティを右クリックし、をクリックして**固有のプロパティを編集 ModelBusReference**です。 ダイアログ ボックスで選択**モデル要素**です。  
  
     ファイル ダイアログ ボックスのフィルターを次に設定します。  
  
     `Provider File|*.provide`  
  
     後の部分文字列"&#124;"ファイルの選択 ダイアログ ボックスのフィルターです。 使用してファイルのことを許可するように設定する可能性があります * です。\*  
  
     **モデル要素の型**一覧で、プロバイダー DSL (たとえば、Company.MBProvider.Task) で 1 つ以上のクラスの複数のドメインの名前を入力します。 抽象クラスがあることができます。 一覧を空白のままにする場合、ユーザーは、いずれかの要素への参照を設定できます。  
  
6.  ダイアログ ボックスを閉じると**すべてのテンプレートの変換**です。  
  
 別の DSL 内の要素への参照を含めることができる DSL が作成されました。  
  
#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>ソリューション内の別のファイルへの参照を ModelBus の作成します。  
  
1.  MBConsumer ソリューションでは、ctrl キーを押しながら f5 キーを押します。 実験用インスタンス[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]で開き、 **MBConsumer\Debugging**プロジェクト。  
  
2.  Sample.provide のコピーを追加、 **MBConsumer\Debugging**プロジェクト。 ModelBus の参照は必要があります、同じソリューション内のファイルを参照してください。 これは必要です。  
  
    1.  デバッグ プロジェクトを右クリックし、**追加**、クリックして**既存項目の**します。  
  
    2.  **項目の追加**ダイアログ ボックスで、フィルターに設定**すべてのファイル (\*.\*)**.  
  
    3.  移動`MBProvider\Debugging\Sample.provide` をクリックし、**追加**です。  
  
3.  `Sample.consume` を開きます。  
  
4.  1 つの例の図形をクリックし、[プロパティ] ウィンドウでをクリックして**[...]** MBR プロパティにします。 ダイアログ ボックスで、をクリックして**参照**選択`Sample.provide`です。 要素 ウィンドウで、タスクの種類を展開し、要素のいずれかを選択します。  
  
5.  ファイルを保存します。  
  
     (の実験用インスタンスをまだ終了しないでください[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)])。  
  
 別のモデル内の要素への参照を ModelBus を含むモデルを作成しました。  
  
#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>テキスト テンプレートで ModelBus の参照を解決するには  
  
1.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]サンプルのテキスト テンプレート ファイルを開きます。 その内容を次のように設定します。  
  
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
  
     次の点にも注意します。  
  
    1.  `hostSpecific`と`inherits`の属性、`template`ディレクティブを設定する必要があります。  
  
    2.  コンシューマー モデルにはその DSL で生成されたディレクティブ プロセッサを通常の方法でアクセスします。  
  
    3.  アセンブリおよびインポートのディレクティブは、ModelBus と、DSL、プロバイダーの種類にアクセスできる必要があります。  
  
    4.  Mbr の多くが、同じモデルにリンクされていることがわかっている場合は、CreateAdapter を 1 回だけ呼び出すことをお勧めします。  
  
2.  テンプレートを保存したとき。 生成されたテキスト ファイルが、次のようになっていることを確認します。  
  
    ```  
  
    ExampleElement1   
    ExampleElement2   
         ExampleElement2 is linked to Task: Task2  
  
    ```  
  
#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>ジェスチャ ハンドラーの ModelBus 参照を解決するには  
  
1.  実験用インスタンスを閉じる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が実行されている場合は、します。  
  
2.  MBConsumer\Dsl\Custom.cs をという名前で、次にその内容を設定したファイルを追加します。  
  
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
  
3.  Ctrl キーを押しながら、F5 キーを押します。  
  
4.  実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、開かれている`Debugging\Sample.consume`です。  
  
5.  1 つの図形をダブルクリックします。  
  
     その要素で MBR を設定する場合は、参照先のモデルが表示されますされ、参照される要素が選択されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Modelbus を使用してモデルを統合します。](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [コード生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
