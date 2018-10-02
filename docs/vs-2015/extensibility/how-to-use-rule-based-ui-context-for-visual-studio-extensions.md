---
title: '方法: Visual Studio 拡張機能のルール ベースの UI コンテキストを使用して |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 8
ms.author: gregvanl
ms.openlocfilehash: dfe3e1645bd23c859a36f4de222472b8460fd305
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538602"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>方法: Visual Studio 拡張機能のルール ベースの UI コンテキストを使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: Visual Studio 拡張機能の使用規則ベースの UI コンテキスト](https://docs.microsoft.com/visualstudio/extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions)します。  
  
Visual Studio と特定の Vspackage の読み込みを許可するよく知られている<xref:Microsoft.VisualStudio.Shell.UIContext>s がアクティブ化されます。 しかし、これらの UI コンテキストが非常に細かく、拡張機能の作成者を選択しないまま、ポイントの前にアクティブにする使用可能な UI コンテキストを選択する本当に望んで、VSPackage を読み込みます。 よく知られている UI コンテキストの一覧は、次を参照してください。<xref:Microsoft.VisualStudio.Shell.KnownUIContexts>します。  
  
 パッケージを読み込むと、パフォーマンスに影響する可能性があり、読み込むことが必要なよりも早くは、そのベスト プラクティスではありません。 Visual Studio 2015 には、規則に基づいた UI コンテキスト、する UI コンテキストがアクティブになるし、関連付けられている Vspackage が読み込まれる正確な条件を定義する拡張機能の作成者をできるようにするメカニズムの概念が導入されました。  
  
## <a name="rule-based-ui-context"></a>ルール ベースの UI コンテキスト  
 「ルール」は、新しい UI コンテキスト (GUID) と 1 つまたは複数の"Terms"を参照するブール式を組み合わせる論理"and"、「または」、"not"操作。 「条件」は、実行時に動的に評価され、されるたびに、用語の変更のいずれかの式が再評価されます。 式の評価が true と関連付けられた UI コンテキストがアクティブにします。 それ以外の場合、UI コンテキストでは、解除が有効にします。  
  
 ルール ベースの UI コンテキストは、さまざまな方法で使用できます。  
  
1.  コマンドとツール ウィンドウの可視性の制約を指定します。 UI コンテキスト ルールが満たされるまでは、コマンド/ツール ウィンドウを非表示にすることができます。  
  
2.  自動読み込みの制約: ルールが満たされたときにのみパッケージを自動読み込み  
  
3.  遅延したタスク: 指定した間隔が経過し、ルールがまだ満たされていればまでの読み込みを遅延します。  
  
 Visual Studio 拡張機能によって、メカニズムを使用することがあります。  
  
## <a name="create-a-rule-based-ui-context"></a>ルール ベースの UI コンテキストを作成します。  
 という、TestPackage".config"拡張子を持つファイルのみに適用されるメニュー コマンドを提供する拡張機能があるとします。 、VS2015 の前に、最適なオプションが TestPackage を読み込むときに<xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A>UI コンテキストがアクティブ化します。 読み込まれているソリューションでもは .config ファイルので効率的ではありません。 お知らせを参照してください .config 拡張子の付いたファイル場合にのみ、UI コンテキストをアクティブ化するルール ベースの UI コンテキストを使用する方法が選択され、その UI コンテキストがアクティブになる TestPackage を読み込みます。  
  
1.  新しい UIContext GUID を定義し、VSPackage のクラスに追加<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>と<xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>します。  
  
     たとえば、新しい UIContext と仮定"UIContextGuid"が追加されます。 作成した GUID (ツールをクリックして、GUID を作成することができます]-> [guid を作成する)"8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"です。 次のコードを追加する、パッケージ、クラス内で。  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     属性で、次のコードを追加します (これらの属性の詳細は後述)。  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     これらのメタデータは、新しい UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) と 1 つの用語「DotConfig」を参照する式を定義します。 アクティブな階層の現在の選択が、正規表現パターンに一致する名前を持つときに、"DotConfig"という用語が true に評価された"\\.config$"(".config"で終わる)。 (既定値) の値は、オプションのデバッグに役立つルールの名前を定義します。  
  
     属性の値は、その後のビルド時に生成された pkgdef に追加されます。  
  
2.  TestPackage のコマンドの VSCT ファイルでは、適切なコマンドに"DynamicVisibility"フラグを追加します。  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  VSCT の可視性のセクションでは、新しい UIContext 1 で定義されている GUID を適切なコマンドを関連付けます。  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  シンボルのセクションで、UIContext の定義を追加します。  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     ここで、ソリューション エクスプ ローラーで選択した項目が".config"ファイルと、これらのコマンドのいずれかが選択されるまで、パッケージを読み込むことができませんが場合にのみ、*.config ファイルのコンテキスト メニュー コマンドは表示されます。  
  
 次に、デバッガーを使用してみましょうのみと本来は、パッケージが読み込まれることを確認します。 TestPackage をデバッグします。  
  
1.  ブレークポイントを設定、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッド。  
  
2.  TestPackage をビルドしてデバッグを開始します。  
  
3.  プロジェクトを作成するか、いずれかを開きます。  
  
4.  .Config 以外の拡張子を指定したファイルを選択します。ブレークポイントをヒットしない必要があります。  
  
5.  App.Config ファイルを選択します。  
  
 TestPackage は読み込みをブレークポイントで停止します。  
  
## <a name="adding-more-rules-for-ui-context"></a>UI コンテキストに対してルールを追加します。  
 UI コンテキスト ルールは、ブール式であるために、UI コンテキストのさらに制限された規則を追加できます。 たとえば、上記の UI コンテキストで、規則では、プロジェクトのソリューションが読み込まれるときにのみ適用されるを指定できます。 この方法でのコマンドは、スタンドアロン ファイルとして、プロジェクトの一部としてではなく、.config のファイルを開くかどうか表示されません。  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 今すぐ式は、3 つの用語を参照します。 "SingleProject"と"MultipleProjects"の最初の 2 つの用語では、(その Guid) でよく知られているその他の UI コンテキストを参照してください。 3 番目の用語"DotConfig"は、先ほど定義した規則に基づく UI コンテキストです。  
  
## <a name="delayed-activation"></a>アクティブ化を遅らせる  
 ルールは、省略可能な「遅延」を持つことができます。 遅延時間はミリ秒単位で指定します。 存在する場合、アクティブ化または非アクティブ化が、その時間間隔で遅延する規則の UI コンテキストの遅延によって、します。 規則の変更は、待機時間の間隔の前にバックアップし、何も起こりません。 このメカニズムは、「調整」初期化の手順 - one-time initialization 特にタイマーに依存したり、アイドル状態の通知を登録せずに使用できます。  
  
 たとえば、100 ミリ秒の遅延が発生して、ルールのテスト負荷を指定できます。  
  
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
|{0} この nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID は、UI コンテキストを表します。 という用語は、ときに、UI コンテキストがアクティブで false、それ以外の場合、true になります。|  
|HierSingleSelectionName:\<パターン >|アクティブな階層内の選択範囲が 1 つの項目と、選択した項目の名前「パターン」で指定された .Net の正規表現と一致するたびに、用語が true になります。|  
|UserSettingsStoreQuery:\<クエリ >|"query"は、0 以外の値に評価される必要がありますユーザー設定ストアに完全なパスを表します。 クエリは、"collection"および"propertyName"最後のスラッシュでに分割されます。|  
|ConfigSettingsStoreQuery:\<クエリ >|"query"は、0 以外の値に評価される必要があります構成設定ストアに完全なパスを表します。 クエリは、"collection"および"propertyName"最後のスラッシュでに分割されます。|  
|ActiveProjectFlavor:\<projectTypeGuid >|現在選択されているプロジェクトのフレーバーたびに、用語が true になります (集計) が指定されたプロジェクト型 GUID と一致するフレーバーとします。|  
|ActiveEditorContentType:\<contentType >|という用語は、選択したドキュメントが特定のコンテンツの種類とテキスト エディターである場合に true になります。|  
|ActiveProjectCapability:\<式 >|という用語は、アクティブなプロジェクトの機能が指定された式と一致する場合は true です。 式には、VB のようなものを指定できる&#124;CSharp|  
|SolutionHasProjectCapability:\<式 >|上記に似ていますが、用語はソリューションには、読み込まれているプロジェクトを式に一致する場合に当てはまります。|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|ソリューション (集計) プロジェクト フレーバーがあり、特定のプロジェクト型 GUID と一致するフレーバーたびに、用語が true になります。|


  
## <a name="compatibility-with-cross-version-extension"></a>バージョン間の拡張機能との互換性  
 ルール ベースの UI コンテキストは以前のバージョンに移植しないと、Visual Studio 2015 の新機能です。 これには、Visual Studio 2013 での自動読み込みと以前のバージョンをする必要がありますが、ルール ベースの UI コンテキストを自動で読み込まれる Visual Studio 2015 を防ぐために役立ちますが、Visual Studio の複数のバージョンを対象とする拡張機能/パッケージに問題が作成されます。  
  
 このようなパッケージをサポートするために、レジストリのエントリを AutoLoadPackages はようになりましたを Visual Studio 2015 以降で、エントリがスキップされることを示すために、値フィールドにフラグを指定できます。 フラグを追加することによってこれできます<xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>します。 Vspackage を追加できるようになりました**SkipWhenUIContextRulesActive**オプションをその<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>を Visual Studio 2015 以降、エントリを無視するかを示す属性です。  
  
## <a name="extensible-ui-context-rules"></a>拡張可能な UI コンテキスト ルール  
 場合によっては、パッケージは、静的コンテキストの UI のルールを使用することはできません。 たとえば、コマンドの状態がインポートされた MEF プロバイダーでサポートされている種類のエディターに基づいているような機能拡張をサポートしているパッケージがあるとします。 コマンドは、現在の編集の種類をサポートしている拡張機能がある場合に有効です。 このような場合どの MEF によって拡張機能が利用可能な条件を変更するため、パッケージ自体は、静的 UI コンテキスト規則を使用することはできません。  
  
 ルール ベースの UI コンテキストがハードコーディングされた式をサポートするこのようなパッケージをサポートするために"*"を示すすべて、以下の条項とは結合されますか。 これは、既知のルール ベースの UI コンテキストを定義するマスター パッケージは、し、このコンテキストにそのコマンドの状態を関連付けます。 その後、マスター パッケージの対象となる任意の MEF 拡張機能では、エディターの他の用語や、マスターの式に影響を与えることがなく、サポートの条項を追加できます。  
  
 コンス トラクター<xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A>ドキュメントは、拡張可能な UI コンテキスト規則の構文を示します。

