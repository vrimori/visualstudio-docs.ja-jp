---
title: "AL (Assembly Linker) Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AL task [MSBuild]"
  - "MSBuild, AL task"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AL (Assembly Linker) Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

AL タスクは、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] と一緒に配布される AL.exe ツールをラップします。  このアセンブリ リンカー ツールは、モジュール ファイルまたはリソース ファイルである 1 つ以上のファイルから、マニフェスト付きでアセンブリを作成するために使用されます。  これらの機能はコンパイラおよび開発環境に既に備わっている場合があるため、必ずしもこのタスクを直接使用する必要はありません。  アセンブリ リンカーが最も役立つのは、開発者が混合言語による開発で生成されるコンポーネント ファイルなどの複数のコンポーネント ファイルから 1 つのアセンブリを作成する必要がある場合です。  このタスクは、各モジュールを 1 つのアセンブリ ファイルに結合するものではありません。作成されたアセンブリを正常に読み込むためには、個々のモジュールを引き続き配布して、配布先で使用できるようにする必要があります。  AL.exe の詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」を参照してください。  
  
## パラメーター  
 `AL` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|------------|--------|  
|`AlgorithmID`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリ マニフェストを含むファイルを除き、マルチファイル アセンブリ内の全ファイルをハッシュするためのアルゴリズムを指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/algid` オプションの説明を参照してください。|  
|`BaseAddress`|省略可能な `String` 型のパラメーターです。<br /><br /> 実行時にユーザーのコンピューターに DLL を読み込む先のアドレスを指定します。  オペレーティング システムにプロセス空間内で DLL を再配置させる代わりに DLL のベース アドレスを指定しておくと、アプリケーションの読み込み速度が速くなります。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の \/base\[address\] オプションに対応します。|  
|`CompanyName`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Company` フィールドの文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/comp[any]` オプションの説明を参照してください。|  
|`Configuration`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Configuration` フィールドの文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/config[uration]` オプションの説明を参照してください。|  
|`Copyright`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Copyright` フィールドの文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/copy[right]` オプションの説明を参照してください。|  
|`Culture`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリに関連付けるカルチャ文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/c[ulture]` オプションの説明を参照してください。|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 公開キーだけをアセンブリに格納する場合は `true`、アセンブリに完全に署名する場合は `false` にします。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/delay[sign]` オプションの説明を参照してください。|  
|`Description`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Description` フィールドの文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/descr[iption]` オプションの説明を参照してください。|  
|`EmbedResources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 指定されたリソースを、アセンブリ マニフェストを格納するイメージに埋め込みます。  このタスクでは、リソース ファイルの内容をイメージにコピーします。  このパラメーターに渡すアイテムには、`LogicalName` および `Access` と呼ばれるオプションのメタデータを付加することができます。  `LogicalName` メタデータは、リソースの内部 ID を指定するために使用します。  `Access` メタデータを `private` に設定すると、このリソースを他のアセンブリで表示できないようにすることができます。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/embed[resource]` オプションの説明を参照してください。|  
|`EvidenceFile`|省略可能な `String` 型のパラメーターです。<br /><br /> `Security.Evidence` のリソース名を持つアセンブリに、指定されたファイルを埋め込みます。<br /><br /> 通常のリソースに対して `Security.Evidence` を使用することはできません。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/e[vidence]` オプションに対応します。|  
|`ExitCode`|省略可能な `Int32` 型の読み取り専用出力パラメーターです。<br /><br /> 実行したコマンドの終了コードを示します。|  
|`FileVersion`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `File Version` フィールドの文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/fileversion` オプションの説明を参照してください。|  
|`Flags`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Flags` フィールドに値を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/flags` オプションの説明を参照してください。|  
|`GenerateFullPaths`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> エラー メッセージで報告されるすべてのファイルについて、絶対パスを使用するようタスクに指定します。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/fullpaths` オプションに対応します。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> キー ペアを保持するコンテナーを指定します。  これにより、公開キーがアセンブリ マニフェストに挿入され、アセンブリに署名 \(厳密な名前が指定\) されます。  次に、タスクは最終的なアセンブリに秘密キーで署名します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/keyn[ame]` オプションの説明を参照してください。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリに署名するためのキー ペアまたは公開キーだけを含むファイルを指定します。  コンパイラは、アセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/keyf[ile]` オプションの説明を参照してください。|  
|`LinkResources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 指定されたリソース ファイルをアセンブリにリンクします。  リソースはアセンブリの一部になりますが、ファイルはコピーされません。  このパラメーターに渡すアイテムには、`LogicalName`、`Target`、および `Access` と呼ばれるオプションのメタデータを付加することができます。  `LogicalName` メタデータは、リソースの内部 ID を指定するために使用します。  `Target` メタデータは、タスクがファイルをコピーする場所のパスとファイル名を指定できます。その後、この新しいファイルはアセンブリにコンパイルされます。  `Access` メタデータを `private` に設定すると、このリソースを他のアセンブリで表示できないようにすることができます。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/link[resource]` オプションの説明を参照してください。|  
|`MainEntryPoint`|省略可能な `String` 型のパラメーターです。<br /><br /> モジュールを実行可能ファイルに変換するときにエントリ ポイントとして使用する、メソッドの完全修飾名 \(*class.method*\) を指定します。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/main` オプションに対応します。|  
|`OutputAssembly`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> このタスクで作成されるファイルの名前を指定します。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/out` オプションに対応します。|  
|`Platform`|省略可能な `String` 型のパラメーターです。<br /><br /> このコードを実行できるプラットフォームを限定します。`x86`、`Itanium`、`x64`、または `anycpu` のいずれかです。  既定値は `anycpu` です。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/platform` オプションに対応します。|  
|`ProductName`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Product` フィールドに文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/prod[uct]` オプションの説明を参照してください。|  
|`ProductVersion`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `ProductVersion` フィールドに文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/productv[ersion]` オプションの説明を参照してください。|  
|`ResponseFiles`|省略可能な `String[]` 型のパラメーターです。<br /><br /> アセンブリ リンカーに渡す追加のオプションを含む応答ファイルを指定します。|  
|`SdkToolsPath`|省略可能な `String` 型のパラメーターです。<br /><br /> resgen.exe などの SDK ツールのパスを指定します。|  
|`SourceModules`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> アセンブリにコンパイルする 1 つ以上のモジュールです。  モジュールは作成されるアセンブリのマニフェストに一覧表示されますが、アセンブリを読み込むには、モジュールを配布して、配布先で使用できるようにする必要があります。  このパラメーターに渡されるアイテムには、`Target` と呼ばれるメタデータを付加することができます。このメタデータは、タスクがファイルをコピーする場所のパスとファイル名を指定できます。その後、この新しいファイルはアセンブリにコンパイルされます。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」を参照してください。  このパラメーターは、特定のスイッチを指定しないで Al.exe に渡したモジュールの一覧に相当します。|  
|`TargetType`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルのファイル形式として、`library` \(コード ライブラリ\)、`exe` \(コンソール アプリケーション\)、または `win` \(Windows ベースのアプリケーション\) のいずれかを指定します。  既定値は `library` です。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/t[arget]` オプションに対応します。|  
|`TemplateFile`|省略可能な `String` 型のパラメーターです。<br /><br /> カルチャ フィールドを除く、すべてのアセンブリ メタデータの継承元であるアセンブリを指定します。  厳密な名前を持つアセンブリを指定する必要があります。<br /><br /> `TemplateFile` パラメーターを指定して作成したアセンブリは、サテライト アセンブリになります。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/template` オプションに対応します。|  
|`Timeout`|省略可能な `Int32` 型のパラメーターです。<br /><br /> タスク実行を終了するまでの時間をミリ秒単位で指定します。  既定値は `Int.MaxValue` であり、タイムアウト期限がないことを示します。|  
|`Title`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Title` フィールドに文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/title` オプションの説明を参照してください。|  
|`ToolPath`|省略可能な `String` 型のパラメーターです。<br /><br /> このタスクで基になる実行可能ファイル \(Al.exe\) を読み込む場所を指定します。  このパラメーターを指定しないと、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行しているフレームワークのバージョンに対応する SDK インストール パスが使用されます。|  
|`Trademark`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリの `Trademark` フィールドに文字列を指定します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/trade[mark]` オプションの説明を参照してください。|  
|`Version`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリのバージョン情報を指定します。  文字列の形式は、*major.minor.build.revision* です。  既定値は 0 です。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/v[ersion]` オプションの説明を参照してください。|  
|`Win32Icon`|省略可能な `String` 型のパラメーターです。<br /><br /> .ico ファイルをアセンブリに挿入します。  .ico ファイルは出力ファイルにファイル エクスプローラーの目的の外観を与えます。  このパラメーターは、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/win32icon` オプションに対応します。|  
|`Win32Resource`|省略可能な `String` 型のパラメーターです。<br /><br /> Win32 リソース \(.res ファイル\) を出力ファイルに挿入します。  詳細については、「[Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)」の `/win32res` オプションの説明を参照してください。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 使用例  
 指定されたオプションで、アセンブリを作成する例を次に示します。  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)