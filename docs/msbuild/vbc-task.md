---
title: "Vbc Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Vbc task [MSBuild]"
  - "MSBuild, Vbc task"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Vbc Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

実行可能ファイル \(.exe\)、ダイナミック リンク ライブラリ \(.dll\)、またはコード モジュール \(.  netmodule\) を作成する vbc.exe をラップします。  vbc.exe の詳細については、「[Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)」を参照してください。  
  
## パラメーター  
 `Vbc` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|------------|--------|  
|`AdditionalLibPaths`|省略可能な `String[]` 型のパラメーターです。<br /><br /> References 属性で指定されたアセンブリを検索する追加のフォルダーを指定します。|  
|`AddModules`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 指定ファイルからのすべての型情報をコンパイル中のプロジェクトで使用できるようにします。  このパラメーターは、vbc.exe コンパイラの [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) スイッチに相当します。|  
|`BaseAddress`|省略可能な `String` 型のパラメーターです。<br /><br /> ダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) のベース アドレスを指定します。  このパラメーターは、vbc.exe コンパイラの [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) スイッチに相当します。|  
|`CodePage`|省略可能な `Int32` 型のパラメーターです。<br /><br /> コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  このパラメーターは、vbc.exe コンパイラの [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) スイッチに相当します。|  
|`DebugType`|省略可能な `String[]` 型のパラメーターです。<br /><br /> コンパイラでデバッグ情報が生成されます。  このパラメーターには、次の値を指定できます。<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> 既定値は、実行中のプログラムにデバッガーをアタッチできる `full` です。  `pdbonly` を指定すると、プログラムがデバッガーで開始されたときにはソース コードをデバッグできますが、実行中のプログラムをデバッガーにアタッチしたときはアセンブリ言語コードしか表示されません。  詳細については、「[\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)」を参照してください。|  
|`DefineConstants`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 条件付きコンパイル定数を定義します。  シンボルと値のペアを、セミコロン \(;\) で区切って、次の構文で指定します。<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> このパラメーターは、vbc.exe コンパイラの [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) スイッチに相当します。|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、アセンブリに公開キーが格納されます。  `false` に設定すると、アセンブリに完全な署名が行われます。  既定値は `false` です。このパラメーターは、`KeyFile` パラメーターまたは `KeyContainer` パラメーターと一緒に使用しない場合は無効になります。  このパラメーターは、vbc.exe コンパイラの [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) スイッチに相当します。|  
|`DisabledWarnings`|省略可能な `String` 型のパラメーターです。<br /><br /> 指定された警告の出力を抑制します。  必要なのは、警告 ID の数値を指定することだけです。  複数の警告を指定するときは、セミコロン \(;\) で区切ります。  このパラメーターは、vbc.exe コンパイラの [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) スイッチに相当します。|  
|`DocumentationFile`|省略可能な `String` 型のパラメーターです。<br /><br /> ドキュメント コメントを指定された XML ファイルに出力します。  このパラメーターを指定すると、`GenerateDocumentation` 属性がオーバーライドされます。  詳細については、「[\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)」を参照してください。|  
|`EmitDebugInformation`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、デバッグ情報が生成され、.pdb ファイルに置かれます。  詳細については、「[\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)」を参照してください。|  
|`ErrorReport`|省略可能な `String` 型のパラメーターです。<br /><br /> タスクで内部コンパイル エラーを報告するかどうかを指定します。  このパラメーターには、次の値を指定できます。<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> `prompt` を指定すると、内部コンパイル エラーが発生した場合に、エラー データをマイクロソフトに送信するかどうかを確認するメッセージが表示されます。<br /><br /> `send` を指定すると、内部コンパイル エラーが発生した場合に、このタスクによってエラー データがマイクロソフトに送信されます。<br /><br /> 既定値は `none` です。この場合、エラーはテキストが出力されるだけです。<br /><br /> このパラメーターは、vbc.exe コンパイラの [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) スイッチに相当します。|  
|`FileAlignment`|省略可能な `Int32` 型のパラメーターです。<br /><br /> 出力ファイルでセクションを揃えるサイズをバイト単位で指定します。  このパラメーターには、次の値を指定できます。<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> このパラメーターは、vbc.exe コンパイラの [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) スイッチに相当します。|  
|`GenerateDocumentation`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、ドキュメント情報が生成されます。この情報は、このタスクで作成している実行可能ファイルまたはライブラリの名前を付けた XML ファイルに格納されます。  詳細については、「[\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc)」を参照してください。|  
|`Imports`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 指定されたアイテム コレクションから名前空間をインポートします。  このパラメーターは、vbc.exe コンパイラの [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) スイッチに相当します。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> 暗号化キー コンテナーの名前を指定します。  このパラメーターは、vbc.exe コンパイラの [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) スイッチに相当します。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> 暗号化キーを格納しているファイルの名前を指定します。  詳細については、「[\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile)」を参照してください。|  
|`LangVersion`|省略可能な [String](assetId:///String?qualifyHint=False&autoUpgrade=True) 型のパラメーターです。<br /><br /> 言語のバージョン \("9" または "10"\) を指定します。|  
|`LinkResources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 出力ファイル内に .NET Framework リソースへのリンクを作成します。リソース ファイル自体は、出力ファイルに含まれません。  このパラメーターは、vbc.exe コンパイラの [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) スイッチに相当します。|  
|`MainEntryPoint`|省略可能な `String` 型のパラメーターです。<br /><br /> `Sub Main` プロシージャを含むクラスまたはモジュールを指定します。  このパラメーターは、vbc.exe コンパイラの [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) スイッチに相当します。|  
|`ModuleAssemblyName`|省略可能な `String` 型のパラメーターです。<br /><br /> このモジュールが含まれるアセンブリを指定します。|  
|`NoConfig`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> コンパイラで vbc.rsp ファイルを使用しない場合に指定します。  このパラメーターは、vbc.exe コンパイラの [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) スイッチに相当します。|  
|`NoLogo`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、コンパイラの開始メッセージが表示されなくなります。  このパラメーターは、vbc.exe コンパイラの [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) スイッチに相当します。|  
|`NoStandardLib`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> コンパイラが標準のライブラリを参照しないよう指定します。  このパラメーターは、vbc.exe コンパイラの [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) スイッチに相当します。|  
|`NoVBRuntimeReference`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 内部使用のみ。  true に設定すると、Microsoft.VisualBasic.dll への自動参照は行われなくなります。|  
|`NoWarnings`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、警告は出力されません。  詳細については、「[\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)」を参照してください。|  
|`Optimize`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、コンパイラの最適化が有効になります。  このパラメーターは、vbc.exe コンパイラの [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) スイッチに相当します。|  
|`OptionCompare`|省略可能な `String` 型のパラメーターです。<br /><br /> 文字列比較の方法を指定します。  このパラメーターには、次の値を指定できます。<br /><br /> -   `binary`<br />-   `text`<br /><br /> `binary` を指定すると、タスクでバイナリでの文字列の比較を行います。  `text` を指定すると、タスクでテキストでの文字列の比較を行います。  このパラメーターの既定値は、`binary` です。  このパラメーターは、vbc.exe コンパイラの [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) スイッチに相当します。|  
|`OptionExplicit`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` を設定した場合は、変数を明示的に宣言する必要があります。  このパラメーターは、vbc.exe コンパイラの [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) スイッチに相当します。|  
|`OptionInfer`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、変数の型の推論が可能になります。|  
|`OptionStrict`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、暗黙の型変換を制限するために、厳密な型指定規則が適用されます。  このパラメーターは、vbc.exe コンパイラの [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) スイッチに相当します。|  
|`OptionStrictType`|省略可能な `String` 型のパラメーターです。<br /><br /> 警告を生成する厳密な型指定規則を指定します。  現在サポートされているのは "custom" だけです。  このパラメーターは、vbc.exe コンパイラの [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) スイッチに相当します。|  
|`OutputAssembly`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 出力ファイルの名前を指定します。  このパラメーターは、vbc.exe コンパイラの [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) スイッチに相当します。|  
|`Platform`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルで対象とするプロセッサ プラットフォームを指定します。  このパラメーターの値には、`x86`、`x64`、`Itanium`、または `anycpu` を指定できます。  既定値は `anycpu` です。  このパラメーターは、vbc.exe コンパイラの [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) スイッチに相当します。|  
|`References`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> タスクで、指定したアイテムから現在のプロジェクトに、パブリック型の情報をインポートする場合に指定します。  このパラメーターは、vbc.exe コンパイラの [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) スイッチに相当します。|  
|`RemoveIntegerChecks`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、整数のオーバーフローのエラー チェックが無効になります。  既定値 `false` です。  このパラメーターは、vbc.exe コンパイラの [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) スイッチに相当します。|  
|`Resources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> .NET Framework リソースを出力ファイルに埋め込みます。  このパラメーターは、vbc.exe コンパイラの [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) スイッチに相当します。|  
|`ResponseFiles`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> このタスク用のコマンドが格納されている応答ファイルを指定します。  このパラメーターは、vbc.exe コンパイラの [@ \(応答ファイルの指定\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) オプションに相当します。|  
|`RootNamespace`|省略可能な `String` 型のパラメーターです。<br /><br /> すべての型宣言のルート名前空間を指定します。  このパラメーターは、vbc.exe コンパイラの [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) スイッチに相当します。|  
|`SdkPath`|省略可能な `String` 型のパラメーターです。<br /><br /> mscorlib.dll および microsoft.visualbasic.dll の位置を指定します。  このパラメーターは、vbc.exe コンパイラの [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) スイッチに相当します。|  
|`Sources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` 型のパラメーターです。<br /><br /> 1 つ以上の [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ソース ファイルを指定します。|  
|`TargetCompactFramework`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、[!INCLUDE[Compact](../extensibility/includes/compact_md.md)] がこのタスクのターゲットになります。  このパラメーターは、vbc.exe コンパイラの [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) スイッチに相当します。|  
|`TargetType`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルのファイル形式を指定します。  このパラメーターに指定できる値は、コード ライブラリを作成するための `library`、コンソール アプリケーションを作成するための `exe`、モジュールを作成するための `module`、および、Windows プログラムを作成するための `winexe` のいずれかです。  既定値は `library` です。  このパラメーターは、vbc.exe コンパイラの [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) スイッチに相当します。|  
|`Timeout`|省略可能な `Int32` 型のパラメーターです。<br /><br /> タスク実行を終了するまでの時間をミリ秒単位で指定します。  既定値は `Int.MaxValue` であり、タイムアウト期限がないことを示します。|  
|`ToolPath`|省略可能な `String` 型のパラメーターです。<br /><br /> 基になる実行可能ファイル \(vbc.exe\) を読み込む場所を指定します。  このパラメーターを指定しないと、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] を実行しているフレームワークのバージョンに対応する SDK インストール パスが使用されます。|  
|`TreatWarningsAsErrors`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> `true` に設定すると、すべての警告はエラーとして扱われます。  詳細については、「[\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)」を参照してください。|  
|`UseHostCompilerIfAvailable`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> タスクでインプロセス コンパイラ オブジェクトを使用するよう指定します \(可能な場合\)。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によってのみ使用されます。|  
|`Utf8Output`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> コンパイラ出力を UTF\-8 エンコーディングでログに記録します。  このパラメーターは、vbc.exe コンパイラの [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) スイッチに相当します。|  
|`Verbosity`|省略可能な `String` 型のパラメーターです。<br /><br /> コンパイラ出力の詳細度を指定します。  詳細度には、`Quiet`、`Normal` \(既定\)、または `Verbose` を指定できます。|  
|`WarningsAsErrors`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーとして扱う警告の一覧を指定します。  詳細については、「[\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)」を参照してください。<br /><br /> このパラメーターは、`TreatWarningsAsErrors` パラメーターをオーバーライドします。|  
|`WarningsNotAsErrors`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーとして扱わない警告の一覧を指定します。  詳細については、「[\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)」を参照してください。<br /><br /> このパラメーターは、`TreatWarningsAsErrors` パラメーターを `true` に設定した場合にのみ有効です。|  
|`Win32Icon`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルにファイル エクスプローラーの目的の外観を与えるアセンブリに .ico ファイルを挿入します。  このパラメーターは、vbc.exe コンパイラの [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) スイッチに相当します。|  
|`Win32Resources`|省略可能な `String` 型のパラメーターです。<br /><br /> Win32 リソース ファイル \(.res\) を出力ファイルに挿入します。  このパラメーターは、vbc.exe コンパイラの [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) スイッチに相当します。|  
  
## 解説  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.ToolTaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.ToolTask> クラスから継承されます。  これらの追加のパラメーターの一覧とその説明については、「[ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md)」を参照してください。  
  
## 使用例  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロジェクトをコンパイルする例を次に示します。  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [タスク](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)