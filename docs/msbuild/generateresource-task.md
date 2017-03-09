---
title: "GenerateResource Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateResource task"
  - "GenerateResource task [MSBuild]"
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateResource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

.txt ファイルおよび .resx \(XML ベースのリソース形式\) ファイルと共通言語ランタイムの .resources バイナリ ファイルとの間の変換を行います。.resources ファイルは、ランタイム バイナリ実行可能ファイルに埋め込んだり、サテライト アセンブリにコンパイルしたりできます。  このタスクは通常、.txt ファイルまたは .resx ファイルを .resource ファイルに変換するために使用します。  `GenerateResource` タスクの機能は [resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) の機能に似ています。  
  
## パラメーター  
 `GenerateResource` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|Description|  
|------------|-----------------|  
|`AdditionalInputs`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]`  型のパラメーターです。<br /><br /> このタスクが実行する依存関係のチェックで使用される追加入力が格納されます。  たとえば、通常、プロジェクト ファイルおよびターゲット ファイルは入力であり、それらが更新された場合、すべてのリソースが再生成される必要があります。|  
|`EnvironmentVariables`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 標準の環境ブロックに追加して \(または標準の環境ブロックの一部をオーバーライドする形で\) 子の resgen.exe に渡される、環境変数の名前と値のペアの配列を指定します。|  
|`ExcludedInputPaths`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]`  型のパラメーターです。<br /><br /> 最新かどうかをチェックするときに無視する追跡対象の入力のパスを指定する項目の配列を指定します。|  
|`ExecuteAsTool`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` の場合、アウトプロセスで適切なターゲット フレームワークの tlbimp.exe および aximp.exe が実行されて、必要なラッパー アセンブリが生成されます。  このパラメーターにより、`ResolveComReferences` のマルチ ターゲットが可能になります。|  
|`FilesWritten`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> ディスクに書き込んだすべてのファイルの名前が含まれています。  キャッシュ ファイルがある場合には、キャッシュ ファイルも含まれます。  このパラメーターは、クリーン処理を行う場合に便利です。|  
|`MinimalRebuildFromTracking`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 追跡されているインクリメンタル ビルドが使用されるかどうかを指定するスイッチを取得または設定します。  `true` の場合は、インクリメンタル ビルドが有効になっています。それ以外の場合は、リビルドが強制されます。|  
|`NeverLockTypeAssemblies`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> .resources ファイルなど、作成されるファイルの名前を指定します。  名前を指定しなかった場合には、対応する入力ファイルの名前が使用され、.resources ファイルは、入力ファイルがあるディレクトリに作成されます。|  
|`OutputResources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の出力パラメーター。<br /><br /> .resources ファイルなど、作成されるファイルの名前を指定します。  名前を指定しなかった場合には、対応する入力ファイルの名前が使用され、.resources ファイルは、入力ファイルがあるディレクトリに作成されます。|  
|`PublicClass`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、厳密に型指定されたリソース クラスをパブリック クラスとして作成します。|  
|`References`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 変換元の .resx ファイル内にある読み込み型への参照です。  .resx ファイルでは、データ要素として .NET 型を持つことができます。  この型は .resx ファイルを読み込むときに解決される必要があります。  通常は、標準の型の読み込み規則を使用して正常に解決できます。  アセンブリを `References` に指定した場合には、そのアセンブリが優先されます。<br /><br /> 厳密な型のリソースの場合、このパラメーターは不要です。|  
|`SdkToolsPath`|省略可能な `String` 型のパラメーターです。<br /><br /> resgen.exe などの SDK ツールのパスを指定します。|  
|`Sources`|必須の <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 変換するアイテムを指定します。  このパラメーターに渡すアイテムの拡張子は、以下のいずれかである必要があります。<br /><br /> -   `.txt`: 変換するテキスト ファイルの拡張子として指定します。  テキスト ファイルには、文字列リソースだけを含めることができます。<br />-   `.resx`: 変換する XML ベースのリソース ファイルの拡張子として指定します。<br />-   `.restext`: .txt と同じ形式のファイルに指定します。  この拡張子は、ビルド プロセスで使用するソース ファイルのうち、どのソース ファイルにリソースが含まれているのかを明示する場合に便利です。<br />-   `.resources`: 変換するリソース ファイルの拡張子として指定します。|  
|`StateFile`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> .resx 入力ファイルにあるリンクの依存関係のチェック速度を向上させるためにオプションで使用する、キャッシュ ファイルのパスを指定します。|  
|`StronglyTypedClassName`|省略可能な `String` 型のパラメーターです。<br /><br /> 厳密な型のリソース クラスのクラス名を指定します。  このパラメーターを指定しなかった場合には、リソース ファイルの基本名が使用されます。|  
|`StronglyTypedFilename`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> ソース ファイルの名前を指定します。  このパラメーターを指定しなかった場合には、クラス名がベース ファイル名として使用され、言語に対応する拡張子が付加されます。  たとえば、`MyClass.cs` となります。|  
|`StronglyTypedLanguage`|省略可能な `String` 型のパラメーターです。<br /><br /> 厳密な型のリソースのクラス ソースの生成に使用する言語を指定します。  このパラメーターは、CodeDomProvider で使用されている言語のいずれかに完全に一致する必要があります。  たとえば、`VB` または `C#` です。<br /><br /> このパラメーターに値を渡すと、厳密な型のリソースが作成されます。|  
|`StronglyTypedManifestPrefix`|省略可能な `String` 型のパラメーターです。<br /><br /> 生成される厳密な型のリソースのクラス ソースで使用するリソース名前空間プレフィックスまたはマニフェスト プレフィックスを指定します。|  
|`StronglyTypedNamespace`|省略可能な `String` 型のパラメーターです。<br /><br /> 生成される厳密な型のリソースのクラス ソースで使用する名前空間を指定します。  このパラメーターを指定しなかった場合には、厳密な型のリソースはすべてグローバル名前空間のリソースになります。|  
|`TLogReadFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の読み取り専用パラメーターです。<br /><br /> 読み取り追跡ログを表す項目の配列を取得します。|  
|`TLogWriteFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型の読み取り専用パラメーターです。<br /><br /> 書き込み追跡ログを表す項目の配列を取得します。|  
|`ToolArchitecture`|省略可能な [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 型のパラメーターです。<br /><br /> Tracker.exe を使用して ResGen.exe を実行する必要があるかどうかを判断するために使用されます。<br /><br /> <xref:Microsoft.Build.Utilities.ExecutableType> 列挙体のメンバーが解析できる必要があります。  `String.Empty` の場合、ヒューリスティックを使用して既定のアーキテクチャが判断されます。  Microsoft.Build.Utilities.ExecutableType 列挙体のメンバーが解析できる必要があります。|  
|`TrackerFrameworkPath`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> FileTracker.dll が含まれる適切な .NET Framework の場所のパスを指定します。<br /><br /> 設定した場合は、渡される FileTracker.dll のビットが、使用される ResGen.exe のビットと一致していることをユーザーが確認する必要があります。  設定しない場合は、タスクによって現在の .NET Framework のバージョンに基づいて適切な場所が判断されます。|  
|`TrackerLogDirectory`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> このタスクの実行による追跡ログが配置される中間ディレクトリを指定します。|  
|`TrackerSdkPath`|省略可能な assetId:///String?qualifyHint=False&autoUpgrade=True 型のパラメーターです。<br /><br /> Tracker.exe が含まれる適切な Windows SDK の場所のパスを指定します。<br /><br /> 設定した場合は、渡される Tracker.exe のビットが、使用される ResGen.exe のビットと一致していることをユーザーが確認する必要があります。  設定しない場合は、タスクによって現在の Windows SDK に基づいて適切な場所が判断されます。|  
|`TrackFileAccess`|省略可能な [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) 型のパラメーターです。<br /><br /> true の場合、入力ファイルのディレクトリを使用して相対ファイル パスが解決されます。|  
|`UseSourcePath`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定した場合は、入力ファイルのディレクトリを使用して相対ファイル パスを解決することを指定します。|  
  
## 解説  
 .resx ファイルには、他のリソース ファイルへのリンクを含めることができるため、.resx ファイルと .resource ファイルのタイムスタンプを比較するだけでは、出力が最新であるかどうかを確認できません。  `GenerateResource` タスクを使用すると、.resx ファイル内のリンクをたどり、リンク先のファイルのタイムスタンプも確認できます。  したがって、`GenerateResource` タスクを持つターゲットについては、`Inputs` 属性と `Outputs` 属性の使用は基本的に避けてください。実行する必要のあるターゲットがスキップされてしまう可能性があります。  
  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
 MSBuild 4.0 を使用して .NET 3.5 プロジェクトをターゲットにしている場合、x86 リソースでビルドが失敗することがあります。  この問題を回避するために、ターゲットを AnyCPU アセンブリとしてビルドできます。  
  
## 使用例  
 `GenerateResource` タスクを使用して、`Resx` アイテム コレクションから .resources ファイルを作成する例を次に示します。  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource` タスクは、\<EmbeddedResource\> アイテムの \<LogicalName\> メタデータを使用して、アセンブリに埋め込まれるリソースに名前を付けます。  
  
 アセンブリの名前が myAssembly である場合、次のコードでは、someQualifier.someResource.resources という名前の埋め込みリソースが生成されます。  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 \<LogicalName\> メタデータがない場合、リソースは myAssembly.myResource.resources という名前になります。  この例は、Visual Basic と Visual C\# のビルド処理にのみ適用されます。  
  
## 参照  
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)