---
title: "方法: Visual Studio 拡張機能の UI のルールに基づくコンテキストを使用 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
caps.handback.revision: 6
ms.author: "gregvanl"
---
# 方法: Visual Studio 拡張機能の UI のルールに基づくコンテキストを使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio vspackages にある種の読み込みを許可するよく知られた <xref:Microsoft.VisualStudio.Shell.UIContext>s がアクティブにします。 ただし、これら UI コンテキストは非常に細かく、粒度を選択しない拡張機能の作成者のままですが、ポイントの前にアクティブに使用できる UI コンテキストを取得する、本当に VSPackage を読み込みます。 よく知られた UI コンテキストの一覧は、次を参照してください。 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>します。  
  
 パッケージを読み込むと、パフォーマンスに影響する可能性があり、必要になるよりも早く読み込むはベスト プラクティスではません。 Visual Studio 2015 には、UI コンテキストのルールに基づく、拡張機能の作成者にする UI コンテキストがアクティブになり、関連付けられている Vspackage が読み込まれる正確な条件を定義できるようにするメカニズムの概念が導入されました。  
  
## UI のルールに基づくコンテキスト  
 「ルール」は、新しい UI コンテキスト \(GUID\) と 1 つまたは複数の「用語」を参照するブール式組み合わせる論理「および」,「または」、"not に"操作します。 「条件」は、実行時に動的に評価され、するたびに、用語の変更のいずれか、式が再評価されます。 式の評価が true と関連付けられている UI コンテキストがアクティブ化します。 それ以外の場合、UI コンテキストとは非アクティブにされました。  
  
 ルール ベースの UI コンテキストは、さまざまな方法で使用できます。  
  
1.  コマンドとツール ウィンドウの表示\/非表示の制約を指定します。 UI コンテキスト規則が満たされるまでは、コマンド\/ツール ウィンドウを非表示にすることができます。  
  
2.  自動読み込みの制約: 自動読み込みは、規則が満たされた場合にのみパッケージ化  
  
3.  遅延したタスク: 指定した間隔が経過し、規則が満たされたままになるまでの読み込みを遅延します。  
  
 メカニズムは、Visual Studio 拡張機能で使用できます。  
  
## ルール ベースの UI コンテキストを作成します。  
 TestPackage、.config 拡張子の付いたファイルのみに適用されるメニュー コマンドを提供するという拡張機能があるとします。 VS2015、前に、最適なオプションが TestPackage を読み込めませんでしたと <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI コンテキストがアクティブ化されました。 読み込まれているソリューションも含めることはできません、.config ファイルので効率的ではありません。 お知らせを参照してください UI のルールに基づくコンテキストは、.config 拡張子の付いたファイル場合にのみ、UI コンテキストをアクティブ化に使用できますが選択されているし、その UI コンテキストがアクティブになったときに、TestPackage をロードします。  
  
1.  新しい UIContext GUID を定義し、VSPackage クラスを追加 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> と <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>です。  
  
     たとえば、新しい UIContext と"UIContextGuid"を追加します。 GUID の作成 \(ツールをクリックして、GUID を作成できます\]\-\> \[guid を作成する\) は"8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B"です。 次のコードを追加して、パッケージ クラスの内部。  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     属性で、次のコードを追加します \(これらの属性の詳細については、後で説明\)。  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     これらのメタデータは、新しい UIContext GUID \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) と 1 つの用語"DotConfig"を参照する式を定義します。 "DotConfig"という用語は、"\\.config$"\(".config"で終わる\) 正規表現パターンに一致する名前が有効な階層の現在の選択しているときに、true に評価されます。 \(既定値\) の値では、デバッグに役立つルールのオプションの名前を定義します。  
  
     属性の値は、ビルド時にその後に生成 pkgdef に追加されます。  
  
2.  TestPackage のコマンドの VSCT ファイルでは、適切なコマンドを"DynamicVisibility"フラグを追加します。  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  VSCT の可視性のセクションでは、新しい UIContext 1 で定義されている GUID を適切なコマンドを関連付けます。  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Symbols セクションでは、UIContext の定義を追加します。  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     これで、ソリューション エクスプ ローラーで選択した項目が、.config ファイルであり、それらのコマンドのいずれかを選択するまで、パッケージを読み込むことができませんが場合のみ、\*.config ファイルのコンテキスト メニュー コマンドは表示されます。  
  
 次に、パッケージにのみと思いますが読み込まれることを確認する、デバッガーを使用してみましょう。 TestPackage をデバッグします。  
  
1.  ブレークポイントを設定、 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドです。  
  
2.  TestPackage をビルドしてデバッグを開始します。  
  
3.  プロジェクトを作成するか、いずれかを開きます。  
  
4.  .Config 以外の拡張子を指定したファイルを選択します。 ブレークポイントはヒットしません必要があります。  
  
5.  App.Config ファイルを選択します。  
  
 TestPackage を読み込んではブレークポイントで停止します。  
  
## UI コンテキストに対してルールを追加します。  
 UI コンテキスト ルールは、ブール式であるためには、UI コンテキストのより限定的規則を追加できます。 たとえば、上の UI のコンテキストで、プロジェクトをソリューションが読み込まれるときにのみ、ルールが適用されることを指定できます。 この方法でコマンド スタンドアロン ファイルとして、プロジェクトの一部としてではなく、.config ファイルを開くかどうか表示されません。  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 今すぐ式では、次の 3 つの用語を参照します。 最初の 2 つの用語、"SingleProject"および「行わ」は、\(その Guid\) を他のよく知られた UI コンテキストを参照してください。 3 番目の用語では、"DotConfig"は、先ほど定義した、規則に基づく UI コンテキストです。  
  
## アクティブ化を遅らせる  
 ルールには、省略可能な「遅延」ことができます。 遅延時間はミリ秒単位で指定します。 存在する場合、遅延によって、ライセンス認証またはその時間間隔で遅延する場合に、ルールの UI のコンテキストの非アクティブ化します。 ルールの変更が遅延間隔の前にバックアップを作成し、何も起こりません。 このメカニズムは、"時差を設定する"初期化の手順の 1 回だけ初期化特にタイマーしたりアイドル状態の通知を登録することがなく使用できます。  
  
 たとえば、100 ミリ秒の遅延が発生して、ルールのテスト負荷を指定できます。  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## 端末の種類  
 サポートされているさまざまな種類の用語を次に示します。  
  
|||  
|-|-|  
|{nnnnnnnn\-nnnn\-nnnn\-nnnn\-nnnnnnnnnnnn}|GUID は、UI コンテキストを参照します。 という用語は、UI コンテキストがアクティブで false それ以外の場合、true になります。|  
|HierSingleSelectionName: \< パターン \>|アクティブな階層内の選択が 1 つの項目では、選択した項目の名前が「パターン」によって指定された .Net 正規表現と一致するたびに、用語が true になります。|  
|UserSettingsStoreQuery: \< クエリ \>|「クエリ」は、0 以外の値に評価される必要がありますユーザー設定ストアに完全なパスを表します。 クエリは、「コレクション」および"propertyName"最後のスラッシュでに分割されます。|  
|ConfigSettingsStoreQuery: \< クエリ \>|「クエリ」は、0 以外の値に評価される必要があります構成設定ストアに完全なパスを表します。 クエリは、「コレクション」および"propertyName"最後のスラッシュでに分割されます。|  
|ActiveProjectFlavor: \< projectTypeGuid \>|現在選択されているプロジェクトのフレーバーされるたびに、用語が true になります \(集計\) あり、特定のプロジェクトの種類の GUID が一致するフレーバー。|  
|ActiveEditorContentType: \< contentType \>|という用語は、選択されているドキュメントが特定のコンテンツの種類とテキスト エディターである場合に true になります。|  
|ActiveProjectCapability: \< 式 \>|という用語は、アクティブなプロジェクトの機能が提供されている式に一致する場合に当てはまります。 式には、VB のようなものを指定できます。CSharp|  
|SolutionHasProjectCapability: \< 式 \>|上記に似ていますが用語ではソリューションには、読み込まれているプロジェクトの式と一致する場合は true です。|  
  
## バージョン間の拡張機能との互換性  
 ベースの UI コンテキストを選択し、Visual Studio 2015 の新機能は、以前のバージョンに移植しないようルールします。 これには、Visual Studio 2013 で自動的に読み込まれると、以前のバージョンをする必要がありますが、ルール ベース UI コンテキストをされて自動的に読み込まれる Visual Studio 2015 を防ぐためにメリットを活用する Visual Studio の複数のバージョンを対象とする拡張機能\/パッケージに問題が作成されます。  
  
 このようなパッケージをサポートするためにでは、レジストリ内の AutoLoadPackages エントリは、Visual Studio 2015 以降のエントリをスキップすることを示すために、\[値\] フィールドにフラグにより提供されます。 フラグのオプションを追加することによってこれ行う <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>します。 追加できるように VSPackages **SkipWhenUIContextRulesActive** オプションを <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Visual Studio 2015 以降は、エントリを無視するかを指定する属性です。  
  
## 拡張可能な UI コンテキスト ルール  
 場合によっては、パッケージは、静的コンテキストの UI のルールを使用できません。 たとえば、インポートされた MEF プロバイダーによってサポートされている種類のエディターでコマンドの状態を基になるように機能拡張をサポートするパッケージがあるとします。 現在の編集の種類をサポートする拡張機能がある場合、コマンドが有効にします。 このような場合、パッケージ自体は条項が変更される MEF に応じて拡張機能が提供されてから静的 UI コンテキスト ルールを使用できません。  
  
 ルール ベースの UI のコンテキストがハードコードされた式をサポートするこのようなパッケージをサポートするために"\*"を示すすべて、以下の条件に結合されますか。 これは既知のルール ベースの UI のコンテキストを定義するマスター パッケージであり、このコンテキストにそのコマンドの状態を関連付けます。 後で、マスター パッケージの対象となる、MEF の拡張機能では、その他の用語やマスター式の影響を与えずには、エディターでその条件を追加できます。  
  
 コンス トラクターは、 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> ドキュメントは、拡張可能な UI コンテキスト規則の構文を示しています。