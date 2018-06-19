---
title: '方法: Visual Studio 拡張機能の規則ベースの UI コンテキストを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133710"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>方法: Visual Studio 拡張機能の規則ベースの UI コンテキストを使用
Visual Studio により、読み込み時に特定の Vspackage のよく知られた<xref:Microsoft.VisualStudio.Shell.UIContext>s がアクティブにします。 しかし、これらの UI コンテキストが非常に細かい設定が可能な拡張機能の作成者を選択しないまま、ポイントの前にアクティブに使用できる UI コンテキストを取得する本当にありました、VSPackage を読み込みます。 よく知られている UI コンテキストの一覧は、次を参照してください。<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>です。  
  
 パッケージを読み込むことができます、パフォーマンスに影響を持ち、必要なよりも早く読み込みのベスト プラクティスではありません。 Visual Studio 2015 には、ルールに基づく UI コンテキストにより、拡張機能の作成者にする UI コンテキストがアクティブになり、関連付けられている Vspackage が読み込まれる正確な条件を定義するメカニズムの概念が導入されました。  
  
## <a name="rule-based-ui-context"></a>ルール ベースの UI コンテキスト  
 「ルール」新しい UI コンテキスト (GUID) で構成され、1 つまたは複数の「条項」を参照するブール式と組み合わせて使用論理"and"、「または」、"not"操作します。 「条件」は、実行時に動的に評価され、ときに、用語の変更のいずれか、式が再評価されます。 式は、true に評価されると、関連付けられた UI コンテキストがアクティブになります。 それ以外の場合、UI コンテキストが非アクティブにされました。  
  
 ルール ベースの UI コンテキストは、さまざまな方法で使用できます。  
  
1.  コマンドとツール ウィンドウの表示の制約を指定します。 UI コンテキスト規則が満たされるまでは、コマンドまたはツール ウィンドウを非表示にすることができます。  
  
2.  自動として負荷を抑える: 自動読み込みが、ルールを満たしている場合にのみをパッケージ化  
  
3.  遅延したタスク: 指定した間隔が経過し、規則が満たされたままになるまでの読み込みを遅延します。  
  
 Visual Studio 拡張機能ではのメカニズムを使用する可能性があります。  
  
## <a name="create-a-rule-based-ui-context"></a>ルール ベースの UI コンテキストを作成します。  
 ".Config"の拡張子を持つファイルのみに適用されるメニュー コマンドを提供する TestPackage と呼ばれる拡張機能があるとします。 VS2015、まで、最適なオプションが TestPackage を読み込めませんだったとき<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI コンテキストがアクティブ化されました。 読み込まれているソリューションも含めることはできません、.config ファイルのため効率的で、これはありません。 お知らせを参照してくださいルール ベースの UI コンテキストを使用して、ファイル拡張子 .config を付けた場合にのみ、UI コンテキストをライセンス認証方法が選択され、その UI コンテキストがアクティブになったときに、TestPackage を読み込みます。  
  
1.  新しい UIContext GUID を定義して、VSPackage クラスに追加<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>です。  
  
     たとえば、新しい UIContext を仮定"UIContextGuid"を追加します。 作成された GUID ([ツール] をクリックして、GUID を作成することができます]-> [guid を作成する) は、"8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"です。 次のコードを追加するパッケージ クラス内。  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     属性で、次のコードを追加します (これらの属性の詳細については後述)。  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     これらのメタデータは、新しい UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) と 1 つの用語「DotConfig」を参照する式を定義します。 "DotConfig"という用語は、true と評価された場合は常にアクティブな階層の現在の選択、正規表現パターンに一致する名前"\\.config$"(".config"で終わる)。 (既定値) の値では、オプションのデバッグに役立つ、ルールの名前を定義します。  
  
     属性の値は、ビルド時にその後で生成された pkgdef に追加されます。  
  
2.  TestPackage のコマンドの VSCT ファイルでは、適切なコマンドを"DynamicVisibility"フラグを追加します。  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  可視性のセクションで、VSCT、新しい UIContext 1 で定義されている GUID を適切なコマンドを関連付けます。  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  [シンボル] セクションで、UIContext の定義を追加します。  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     ここで、ソリューション エクスプ ローラーで選択した項目が".config"ファイルとそれらのコマンドのいずれかを選択するまで、パッケージを読み込むことができませんが場合にのみ、*.config ファイルのコンテキスト メニュー コマンドは表示されます。  
  
 次に、のみと本来は、パッケージを読み込むことを確認するデバッガーを使用してみましょう。 TestPackage をデバッグします。  
  
1.  ブレークポイントを設定、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドです。  
  
2.  TestPackage をビルドしてデバッグを開始します。  
  
3.  プロジェクトを作成するか、1 つを表示します。  
  
4.  .Config 以外の拡張子を指定したファイルを選択します。ブレークポイントがヒットしない必要があります。  
  
5.  App.Config ファイルを選択します。  
  
 TestPackage を読み込んで、ブレークポイントで停止します。  
  
## <a name="adding-more-rules-for-ui-context"></a>UI のコンテキストに対してルールを追加します。  
 UI コンテキスト ルールがブール式であるため、UI コンテキストのさらに制限されたルールを追加できます。 たとえば、上記の UI コンテキストで、プロジェクトをソリューションが読み込まれるときにのみ、規則が適用されることを指定できます。 この方法で、コマンドは表示されませんスタンドアロン ファイルとして、プロジェクトの一部としてではなく、".config"のファイルを開くかどうか。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 今すぐ式では、次の 3 つの用語を参照します。 "SingleProject"と「行わ」、最初の 2 つの条項は、他のよく知られている UI コンテキスト (によって、Guid) を参照してください。 3 番目の語句では、"DotConfig"は、前に定義した規則に基づく UI コンテキストです。  
  
## <a name="delayed-activation"></a>アクティブ化を遅らせる  
 ルールは、省略可能な「遅延」を持つことができます。 遅延時間がミリ秒単位で指定されます。 存在する場合、アクティブ化または非アクティブ化すると、その時間間隔で遅延が発生する規則の UI コンテキストの遅延によって、します。 ルールの変更は、前の遅延間隔にバックアップし、何も起こりません。 このメカニズムは、「時差を設定する」初期化の手順の 1 回だけ初期化特にタイマーに依存したり、アイドル状態の通知を登録せずに使用できます。  
  
 たとえば、100 ミリ秒の遅延、ルールのテストの負荷を指定できます。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>用語の種類  
 サポートされているさまざまな種類の用語を次に示します。  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID は、UI コンテキストを参照します。 UI コンテキストがアクティブでは false、それ以外の場合されるたびに、用語が true になります。|  
|HierSingleSelectionName:\<パターン >|アクティブな階層で選択を 1 つの項目は、選択した項目の名前が「パターン」によって指定された .Net 正規表現に一致するたびに、用語が true になります。|  
|UserSettingsStoreQuery:\<クエリ >|「クエリ」は、0 以外の値に評価される必要がありますのある、ユーザー設定ストアへの完全なパスを表します。 クエリは、"collection"および"propertyName"最後のスラッシュでに分割されます。|  
|ConfigSettingsStoreQuery:\<クエリ >|「クエリ」は、0 以外の値に評価される必要があります構成設定ストアに、完全なパスを表します。 クエリは、"collection"および"propertyName"最後のスラッシュでに分割されます。|  
|ActiveProjectFlavor:\<projectTypeGuid >|現在選択されているプロジェクトのフレーバーされるたびに、用語が true になります (集計) が、指定したプロジェクトの種類の GUID と一致するフレーバーとします。|  
|ActiveEditorContentType:\<contentType >|という用語は、選択したドキュメントが指定されたコンテンツの種類とテキスト エディターの場合、true になります。|  
|ActiveProjectCapability:\<式 >|という用語は、アクティブなプロジェクトの機能が提供されている式に一致する場合に当てはまります。 式には、VB のようなものを指定できる&#124;CSharp|  
|SolutionHasProjectCapability:\<式 >|上記に似ていますが、という用語はソリューションには、式に一致するすべての読み込まれたプロジェクト場合に当てはまります。|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|ソリューション (集計) プロジェクト フレーバーがあり、指定したプロジェクトの種類の GUID と一致するフレーバーされるたびに、用語が true になります。|


  
## <a name="compatibility-with-cross-version-extension"></a>バージョン間の拡張機能との互換性  
 ルール ベースの UI コンテキストは、Visual Studio 2015 の新機能および以前のバージョンに移植しないようです。 これには、Visual Studio 2013 で自動的に読み込み、以前のバージョンをする必要がありますが、ルール ベース UI コンテキストを自動で読み込まれる Visual Studio 2015 を防ぐために利用できる Visual Studio の複数のバージョンを対象とする拡張機能/パッケージに問題が作成されます。  
  
 このようなパッケージをサポートするために、レジストリのエントリを AutoLoadPackages ことができます Visual Studio 2015 以降、エントリをスキップすることを示すために、値フィールドにフラグを提供されています。 フラグのオプションを追加することによってこれ行う<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>です。 追加できるように Vspackage **SkipWhenUIContextRulesActive**オプションをその<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>を Visual Studio 2015 以降、エントリを無視するかを示す属性です。  
  
## <a name="extensible-ui-context-rules"></a>拡張可能な UI コンテキスト ルール  
 場合によっては、パッケージは、静的の UI コンテキスト規則を使用することはできません。 たとえば、インポートされた MEF プロバイダーによってサポートされている種類のエディターでコマンドの状態を基になるように機能拡張をサポートするパッケージがあるとします。 コマンドは、現在編集型をサポートする拡張機能がある場合に有効です。 このような場合に応じてどの MEF 拡張機能が使用可能な条件を変更するため、パッケージ自体は静的 UI コンテキスト規則を使用することはできません。  
  
 ルール ベースの UI コンテキストがハードコーディングされた式をサポートするこのようなパッケージをサポートするために"*"を示すすべて、以下の条件で結合されますか。 これにより、既知の規則ベースの UI コンテキストを定義するマスター パッケージによりし、このコンテキストにそのコマンドの状態を関連付けます。 その後、マスター パッケージの対象となる MEF 拡張機能では、その他の語句またはマスター式の影響を与えずに、エディターの条項を追加できます。  
  
 コンス トラクターは、<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>ドキュメントは、拡張可能な UI コンテキスト規則の構文を示しています。