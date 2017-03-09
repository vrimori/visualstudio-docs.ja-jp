---
title: "プロパティと項目の比較 | Microsoft Docs"
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
  - "msbuild では、msbuild プロパティ"
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# プロパティと項目の比較
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild プロパティと項目はどちらを使用して情報をタスクに渡す、条件を評価およびプロジェクト ファイルを参照する値を格納します。  
  
-   プロパティは、名前と値のペアです。 詳細については、次を参照してください。 [MSBuild プロパティ](../msbuild/msbuild-properties.md)します。  
  
-   項目は、通常のファイルを表すオブジェクトです。 項目のオブジェクトには、メタデータのコレクションを関連付けることができます。 メタデータは、名前と値のペアです。 詳細については、次を参照してください。 [項目](../msbuild/msbuild-items.md)します。  
  
## <a name="scalars-and-vectors"></a>スカラーおよびベクトル  
 MSBuild プロパティは 1 つの文字列値を持つ名前/値ペアであるため、多くの場合は *スカラー*します。 MSBuild 項目の種類は項目のリストであるため、多くの場合は *ベクトル*します。 ただし、実際には、プロパティは、複数の値を表すことができ、項目の種類は、0 個または 1 つの項目を持つことができます。  
  
### <a name="target-dependency-injection"></a>ターゲットの依存関係の挿入  
 プロパティが複数の値を表す方法を表示するには、ターゲットをビルドするターゲットの一覧に追加するための一般的な使用パターンを検討してください。 このリストは通常、セミコロンで区切って指定した名前とプロパティの値によって表されます。  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
  `BuildDependsOn` プロパティは、通常、ターゲットの引数として使用 `DependsOnTargets` 属性に、効果的に項目リストに変換します。 ターゲットを追加するか、ターゲットの実行順序を変更するのには、このプロパティをオーバーライドすることができます。 次に例を示します。  
  
```  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 対象のリストに CustomBuild ターゲットを追加付与 `BuildDependsOn` 値 `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`です。  
  
 以降では、MSBuild 4.0 は、対象の依存関係の注入は推奨されません。 使用して、 `AfterTargets` と `BeforeTargets` 属性の代わりにします。 詳細については、次を参照してください。 [ターゲットのビルド順序](../msbuild/target-build-order.md)します。  
  
### <a name="conversions-between-strings-and-item-lists"></a>文字列と項目リストの間の変換  
 MSBuild では、項目の種類と、必要に応じて、文字列値間で変換を実行します。 項目のリストを使用して文字列値に変換する方法を表示するには、項目の種類を MSBuild プロパティの値として使用する場合の動作を考慮してください。  
  
```  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 OutputDir が項目の種類、 `Include` 属性の値"KeyFiles\\です。証明書\\"です。 MSBuild は、2 つの項目にこの文字列を解析して: KeyFiles\ と証明書\\します。 MSBuild が変換またはセミコロンで区切られた文字列に項目の種類を「フラット化」OutputDir 項目の種類は OutputDirList プロパティの値として使用するときに"KeyFiles\\です。証明書\\"です。  
  
## <a name="properties-and-items-in-tasks"></a>プロパティとタスク内の項目  
 プロパティと項目は、入力と出力は、MSBuild タスクとして使用されます。 詳細については、次を参照してください。 [タスク](../msbuild/msbuild-tasks.md)します。  
  
 プロパティは、属性として、タスクに渡されます。 タスク内では、MSBuild プロパティは文字列との間、値を変換できるプロパティの型によって表されます。 サポートされているプロパティの種類には、 `bool`, 、`char`, 、`DateTime`, 、`Decimal`, 、`Double`, 、`int`, 、`string`, 、任意の型と <xref:System.Convert.ChangeType%2A> を処理できます。  
  
 項目がタスクに渡される <xref:Microsoft.Build.Framework.ITaskItem> オブジェクトです。 タスク内で <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> 項目の値を表すと <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> そのメタデータを取得します。  
  
 項目の種類の項目の一覧を配列として渡すことが `ITaskItem` オブジェクトです。 以降、.NET Framework 3.5 では、項目を削除できるターゲットの項目のリストからを使用して、 `Remove` 属性です。 項目リストから項目を削除できる、ためには、0 個の項目が項目の種類は可能です。 項目のリストが渡された場合、タスク、タスクのコードはこの可能性を確認する必要があります。  
  
## <a name="property-and-item-evaluation-order"></a>プロパティと項目の評価順序  
 ビルドの評価フェーズでは、インポートされたファイルは、表示される順序でビルドに組み込まれます。 プロパティと項目は、次の順序で 3 つのパスで定義されます。  
  
-   プロパティが定義され、表示される順番を変更します。  
  
-   項目の定義が定義され、表示される順番を変更します。  
  
-   項目が定義され、表示される順番を変更します。  
  
 ビルドの実行フェーズでは、プロパティとターゲット内で定義されている項目共に評価されます単一フェーズで出現する順序で。  
  
 ただし、すべてのストーリーではありません。 プロパティ、項目の定義、または項目を定義すると、その値が評価されます。 式エバリュエーターでは、値を指定する文字列を展開します。 文字列の展開は、ビルド フェーズに依存します。 さらに詳細なプロパティと項目の評価順序を次に示します。  
  
-   ビルドの評価フェーズでは。  
  
    -   プロパティが定義され、表示される順番を変更します。 プロパティ関数が実行されます。 フォーム $(PropertyName) 内のプロパティ値は式内で展開します。 プロパティ値は、展開された式に設定されます。  
  
    -   項目の定義が定義され、表示される順番を変更します。 プロパティ関数は、式の中で既に展開されています。 メタデータの値は、展開された式に設定されます。  
  
    -   項目の種類が定義されているし、出現する順番を変更します。 フォーム内の値を項目 @(ItemType) は展開します。 項目の変換も展開します。 式の中で、プロパティ関数と値は既に展開されています。 項目のリストとメタデータの値は、展開された式に設定されます。  
  
-   ビルドの実行フェーズでは。  
  
    -   プロパティとターゲット内で定義されている項目が表示される順序で共に評価されます。 プロパティ関数は、実行し、プロパティの値は式内で展開します。 項目の値と項目の変換も展開されます。 プロパティ値、項目の種類の値、およびメタデータの値は、展開された式に設定されます。  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>評価順序の繊細な効果  
 ビルドの評価段階で、プロパティの評価では、項目の評価が先頭に付きます。 ただし、プロパティには、項目の値に依存するように表示される値をことができます。 次のスクリプトを検討してください。  
  
```  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Message タスクを実行するには、このメッセージが表示されます。  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 これは、ための値 `KeyFileVersion` 文字列では実際には、 "@(KeyFile->'%(Version)')". 項目と項目の変換、プロパティを最初に定義するとを展開したされないため、 `KeyFileVersion` プロパティには、展開されていない文字列の値が割り当てられました。  
  
 ビルドの実行フェーズでは、Message タスクを処理するときに MSBuild 文字列が展開 "@(KeyFile->'%(Version)')" 「1.0.0.3」を生成します。  
  
 プロパティと項目のグループの順序で逆になった場合でも、同じメッセージが表示されることに注意してください。  
  
 2 番目の例として、プロパティと項目のグループがターゲット内に存在する場合の動作について考慮してください。  
  
```  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Message タスクでは、このメッセージが表示されます。  
  
```  
KeyFileVersion:   
```  
  
 これは、ビルドの実行フェーズでは、ターゲット内で定義されたプロパティと項目のグループが評価されるため、同時に上下します。  `KeyFileVersion` が定義されている `KeyFile` が不明です。 そのため、項目の変換は、空の文字列に展開します。  
  
 この場合、プロパティと項目グループの順序を逆にすると、元のメッセージが復元されます。  
  
```  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 値 `KeyFileVersion` しない「1.0.0.3」に設定されて "@(KeyFile->'%(Version)')". 、Message タスクには、このメッセージが表示されます。  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>関連項目  
 [高度な概念](../msbuild/msbuild-advanced-concepts.md)