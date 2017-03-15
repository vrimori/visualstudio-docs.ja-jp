---
title: "MSBuild Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild プロパティ"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Properties1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロパティはビルドを設定するための名前と値のペアです。 プロパティを使用することで、タスクに値を渡したり、条件を評価したりできるだけでなく、プロジェクト ファイルで参照する値を格納しておくこともできます。  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>プロジェクト ファイルでのプロパティの定義と参照  
 プロパティが宣言の子として、プロパティの名前を持つ要素を作成することで、 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 要素。 たとえば、次の XML では、`BuildDir` という名前のプロパティを作成し、`Build` を値として設定しています。  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 プロジェクト ファイルでプロパティを参照するには、$(`PropertyName`) という構文を使用します。 たとえば、前の例に示したプロパティを参照するには、$(BuildDir) と記述します。  
  
 プロパティ値を変更するには、プロパティを再定義します。 `BuildDir` プロパティに新しい値を設定するには、次の XML を使用します。  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 プロパティは、プロジェクト ファイルに表示される順に評価されます。 `BuildDir` の新しい値は、古い値が割り当てられた後で宣言する必要があります。  
  
## <a name="reserved-properties"></a>予約済みのプロパティ  
 MSBuild では、プロジェクト ファイルに関する情報や MSBuild のバイナリに関する情報を保持するために、いくつかのプロパティ名が予約されています。 これらのプロパティは、他のプロパティと同じように $ 表記を使用して参照できます。 たとえば、$(MSBuildProjectFile) は、ファイル名の拡張子を含むプロジェクト ファイルの完全なファイル名を返します。  
  
 詳細については、次を参照してください。 [方法: 名前またはプロジェクト ファイルの場所を参照](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) と [MSBuild の予約済みおよび知られているプロパティ](../msbuild/msbuild-reserved-and-well-known-properties.md)します。  
  
## <a name="environment-properties"></a>環境プロパティ  
 プロジェクト ファイルで環境変数を参照する場合も、予約済みのプロパティを参照するときと同じ方法を使用します。 たとえば、プロジェクト ファイルで `PATH` 環境変数を使用するには、$(Path) と記述します。 プロジェクト ファイルに、環境プロパティと同じ名前のプロパティが定義されている場合、環境変数の値はプロジェクト内のプロパティによってオーバーライドされます。  
  
 各 MSBuild プロジェクトには、分離された環境ブロックがあります。各プロジェクトは独自のブロックに対する読み取りと書き込みのみを参照します。  プロジェクト ファイルの評価やビルドを行う前、MSBuild では、プロパティ コレクションが初期化されるときに環境変数のみを読み取ります。 その後で、環境プロパティは静的なプロパティになります。つまり、起動されたツールは、同じ名前と値で実行が開始されます。  
  
 起動されたツール内から環境変数の現在の値を取得する、 [プロパティ関数](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable します。 好みの方法がタスクのパラメーターを使用して <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>します。 この文字列配列に設定されている環境プロパティは、起動されたツールに渡すことができます。このとき、システム環境変数は影響を受けません。  
  
> [!TIP]
>  すべての環境変数が読み取られて、初期プロパティになるわけではありません。 有効な MSBuild プロパティ名 ("386" など) を名前として持っていない環境変数は無視されます。  
  
 詳細については、次を参照してください。 [方法: ビルドで環境変数を使って](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)します。  
  
## <a name="registry-properties"></a>レジストリのプロパティ  
 システム レジストリ値を読み取るには、次の構文を使用します。ここで、`Hive` はレジストリ ハイブ (たとえば、HKEY_LOCAL_MACHINE)、`Key` はキー名、`SubKey` はサブキー名、`Value` はサブキーの値をそれぞれ表します。  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 既定のサブキー値を取得するには、`Value` を省略します。  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 このレジストリ値を使用して、ビルド プロパティを初期化できます。 たとえば、Visual Studio の Web ブラウザーのホーム ページを表すビルド プロパティを作成するには、次のコードを使用します。  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>グローバル プロパティ  
 MSBuild を使用して、コマンドラインでのプロパティを設定することができます、 **/property** (または **/p**) スイッチします。 これらのグローバル プロパティ値は、プロジェクト ファイルで設定されたプロパティ値をオーバーライドします。 これには環境プロパティは含まれますが、予約済みのプロパティは含まれません。予約済みのプロパティは変更できません。  
  
 グローバルな `Configuration` プロパティを `DEBUG` に設定する例を次に示します。  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 グローバル プロパティは、MSBuild タスクの `Properties` 属性を使用することで、複数プロジェクトのビルドに含まれる子プロジェクトに対して設定または変更することもできます。 詳細については、次を参照してください。 [MSBuild タスク](../msbuild/msbuild-task.md)します。  
  
 プロジェクト タグで `TreatAsLocalProperty` 属性を使用してプロパティを指定する場合、そのグローバル プロパティ値は、プロジェクト ファイルで設定されているプロパティ値をオーバーライドしません。 詳細については、次を参照してください。 [Project 要素 (MSBuild)](../msbuild/project-element-msbuild.md) と [方法: さまざまなオプションを同じソース ファイルのビルド](../msbuild/how-to-build-the-same-source-files-with-different-options.md)します。  
  
## <a name="property-functions"></a>プロパティ関数  
 .NET Framework Version 4 以降では、プロパティ関数を使用して MSBuild スクリプトを評価できるようになりました。 MSBuild タスクを使用しなくても、システム時刻の読み取り、文字列の比較、正規表現の照合、その他のさまざまな処理をビルド スクリプト内で実行できます。  
  
 文字列 (インスタンス) メソッドを使用してプロパティ値を操作したり、各種システム クラスの静的メソッドを呼び出したりできます。 たとえば、ビルド プロパティを今日の日付に設定するには、次のようにします。  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 詳細についてとプロパティ関数の一覧は、次を参照してください。 [プロパティ関数](../msbuild/property-functions.md)します。  
  
## <a name="creating-properties-during-execution"></a>実行時のプロパティの作成  
 `Target` 要素の外側にあるプロパティには、ビルドの評価フェーズで値が割り当てられます。 その後の実行フェーズでプロパティを作成または変更するには、次のようにします。  
  
-   プロパティはどのタスクでも生成できます。 プロパティを出力する、 [タスク](../msbuild/task-element-msbuild.md) 要素が子を持つことは [出力](../msbuild/output-element-msbuild.md) を持つ要素を `PropertyName` 属性です。  
  
-   プロパティは生成されることができます、 [CreateProperty](../msbuild/createproperty-task.md) タスクです。 この使用法は推奨されていません。  
  
-   .NET Framework 3.5 以降では、プロパティ宣言を格納できる `Target` 要素を  `PropertyGroup` 要素に含めることができます。  
  
## <a name="storing-xml-in-properties"></a>プロパティに XML を格納する  
 プロパティには、タスクに値を渡したり、ログ情報を表示したりするための任意の XML を格納できます。 次の例では、`ConfigTemplate` プロパティの値に、XML や他のプロパティ参照が使用されています。 このプロパティ参照は、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] により、対応するプロパティ値を使用して置き換えられます。 プロパティ値は表示される順に割り当てられます。 したがって、この例では、`$(MySupportedVersion)`、`$(MyRequiredVersion)`、および `$(MySafeMode)` は既に定義されています。  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>「  
 [MSBuild の概念](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [方法: ビルドで環境変数を使用します。](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [方法: 名前またはプロジェクト ファイルの場所を参照](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [方法: さまざまなオプションを同じソース ファイルのビルド](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild 予約済みおよび既知のプロパティ](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property 要素 (MSBuild)](../msbuild/property-element-msbuild.md)