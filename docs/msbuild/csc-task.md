---
title: "Csc タスク | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc タスク [MSBuild]"
  - "MSBuild、Csc タスク"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Csc タスク
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CSC.exe をラップし、実行可能ファイル (.exe ファイル)、ダイナミック リンク ライブラリ (.dll ファイル)、またはコード モジュール (.netmodule ファイル) を生成します。 CSC.exe の詳細については、次を参照してください。 [c# コンパイラ オプション](/dotnet/csharp/language-reference/compiler-options/index)します。  
  
## <a name="parameters"></a>パラメーター  
 `Csc` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`AdditionalLibPaths`|省略可能な `String[]` 型のパラメーターです。<br /><br /> 参照を検索する追加のディレクトリを指定します。 詳細については、次を参照してください。 [/lib (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option)します。|  
|`AddModules`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリを構成する 1 つ以上のモジュールを指定します。 詳細については、次を参照してください。 [/addmodule (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option)します。|  
|`AllowUnsafeBlocks`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, を使用するコードをコンパイル、 [安全でない](/dotnet/csharp/language-reference/keywords/unsafe) キーワードです。 詳細については、次を参照してください。 [/unsafe (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)します。|  
|`ApplicationConfiguration`|省略可能な `String` 型のパラメーターです。<br /><br /> アセンブリのバインディング設定を含む、アプリケーション構成ファイルを指定します。|  
|`BaseAddress`|省略可能な `String` 型のパラメーターです。<br /><br /> DLL を読み込む位置に推奨されるベース アドレスを指定します。 によって、DLL の既定のベース アドレスを設定、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 共通言語ランタイム。 詳細については、次を参照してください。 [/baseaddress (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)します。|  
|`CheckForOverflowUnderflow`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 整数データ型の境界をオーバーフローする算術演算、実行時に例外が発生するかどうかを指定します。 詳細については、次を参照してください。 [/checked (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)します。|  
|`CodePage`|省略可能な `Int32` 型のパラメーターです。<br /><br /> コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。 詳細については、次を参照してください。 [/codepage (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option)します。|  
|`DebugType`|省略可能な `String` 型のパラメーターです。<br /><br /> デバッグの種類を指定します。 `DebugType` できる `full` または `pdbonly`です。 既定値は `full`, 、実行中のプログラムにアタッチされているデバッガーを有効にします。 指定する `pdbonly` によりソース コードのデバッグと、デバッガーの起動時は、プログラムは実行中のプログラムが、デバッガーに接続されているときに、アセンブラーをのみ表示されます。<br /><br /> このパラメーターは、 `EmitDebugInformation` パラメーター。<br /><br /> 詳細については、次を参照してください。 [/debug (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)します。|  
|`DefineConstants`|省略可能な `String` 型のパラメーターです。<br /><br /> プリプロセッサ シンボルを定義します。 詳細については、次を参照してください。 [/define (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)します。|  
|`DelaySign`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、完全署名されたアセンブリを作成することを指定します。 場合 `false`, 、アセンブリの公開キーを配置する必要なだけを指定します。<br /><br /> このパラメーターも何も起こりませんいずれかで使用されていない限り、 `KeyFile` または `KeyContainer` パラメーター。<br /><br /> 詳細については、次を参照してください。 [/delaysign (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option)します。|  
|`DisabledWarnings`|省略可能な `String` 型のパラメーターです。<br /><br /> 無効にする警告の一覧を指定します。 詳細については、次を参照してください。 [/nowarn (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)します。|  
|`DocumentationFile`|省略可能な `String` 型のパラメーターです。<br /><br /> ドキュメント コメントを XML ファイルに出力します。 詳細については、次を参照してください。 [/doc (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)します。|  
|`EmitDebugInformation`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、タスクがデバッグ情報を生成し、プログラム データベース (.pdb) ファイルに格納します。 場合 `false`, 、タスクがデバッグ情報を出力しません。 既定値は `false` です。 詳細については、次を参照してください。 [/debug (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)します。|  
|`ErrorReport`|省略可能な `String` 型のパラメーターです。<br /><br /> C# で内部エラーを Microsoft に報告する便利な方法を提供します。 このパラメーターの値をとります。 `prompt`, 、`send`, 、または `none`です。 パラメーターが設定されている場合は、 `prompt`, 、内部コンパイラ エラーが発生したときに、プロンプトが表示されます。 プロンプトでは、電子的なバグの報告をマイクロソフトに送信することができます。 パラメーターが設定されている場合は、 `send`, 、バグのレポートが自動的に送信されます。 パラメーターが設定されている場合 `none`, 、コンパイラのテキスト出力にのみ、エラーを報告します。 既定値は `none` です。 詳細については、次を参照してください。 [/errorreport (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)します。|  
|`FileAlignment`|省略可能な `Int32` 型のパラメーターです。<br /><br /> 出力ファイル内のセクションのサイズを指定します。 詳細については、次を参照してください。 [/filealign (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)します。|  
|`GenerateFullPaths`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、コンパイラ出力のファイルへの絶対パスを指定します。 場合 `false`, 、ファイルの名前を指定します。 既定値は `false` です。 詳細については、次を参照してください。 [/fullpaths (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option)します。|  
|`KeyContainer`|省略可能な `String` 型のパラメーターです。<br /><br /> 暗号化キー コンテナーの名前を指定します。 詳細については、次を参照してください。 [/keycontainer (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option)します。|  
|`KeyFile`|省略可能な `String` 型のパラメーターです。<br /><br /> 暗号化キーを格納するファイル名を指定します。 詳細については、次を参照してください。 [/keyfile (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option)します。|  
|`LangVersion`|省略可能な `String` 型のパラメーターです。<br /><br /> 使用する言語のバージョンを指定します。 詳細については、次を参照してください。 [/langversion (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)します。|  
|`LinkResources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` パラメーター。<br /><br /> リンクの作成、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 出力ファイルにリソースのリソース ファイルは、出力ファイルに保存されません。<br /><br /> このパラメーターに渡された項目は省略可能なメタデータ エントリをという名前を持つこと `LogicalName` と `Access`です。 `LogicalName` 対応する、 `identifier` のパラメーター、 `/linkresource` 切り替えると `Access` に対応する `accessibility-modifier` パラメーター。 詳細については、次を参照してください。 [/linkresource (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)します。|  
|`MainEntryPoint`|省略可能な `String` 型のパラメーターです。<br /><br /> 場所を指定、 `Main` メソッドです。 詳細については、次を参照してください。 [/main (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)します。|  
|`ModuleAssemblyName`|省略可能な `String` 型のパラメーターです。<br /><br /> このモジュールの一部となるアセンブリの名前を指定します。|  
|`NoConfig`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、csc.rsp ファイルを使用してコンパイルしないようにコンパイラに指示します。 詳細については、次を参照してください。 [/noconfig (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option)します。|  
|`NoLogo`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、コンパイラの著作権情報の表示を中止します。 詳細については、次を参照してください。 [/nologo (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option)します。|  
|`NoStandardLib`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、全体の System 名前空間を定義するには、mscorlib.dll のインポートされません。 定義または独自の System 名前空間およびオブジェクトを作成する場合は、このパラメーターを使用します。 詳細については、次を参照してください。 [/nostdlib (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)します。|  
|`NoWin32Manifest`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、既定の Win32 マニフェストは含めないでください。|  
|`Optimize`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、最適化を有効します。 場合 `false`, 、最適化を無効にします。 詳細については、次を参照してください。 [/optimize (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)します。|  
|`OutputAssembly`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 出力ファイルの名前を指定します。 詳細については、次を参照してください。 [/out (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)します。|  
|`PdbFile`|省略可能な `String` 型のパラメーターです。<br /><br /> デバッグ情報ファイルの名前を指定します。 既定の名前は、.pdb 拡張子を持つ出力ファイルの名前です。|  
|`Platform`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルのターゲットとするプロセッサ プラットフォームを指定します。 このパラメーターの値をとります。 `x86`, 、`x64`, 、または `anycpu`です。 既定値は `anycpu` です。 詳細については、次を参照してください。 [/platform (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)します。|  
|`References`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` パラメーター。<br /><br /> パブリック型の情報を指定した項目から現在のプロジェクトにインポートするタスクさせます。 詳細については、次を参照してください。 [/reference (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)します。<br /><br /> 指定できます、 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 参照のエイリアスに、 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] メタデータを追加することでファイル `Aliases` を元の「参照」項目。 たとえば、CSC の次のコマンドラインで"LS1"エイリアスを設定します。<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> 使用します。<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` パラメーター。<br /><br /> 埋め込む、 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 出力ファイルにリソースです。<br /><br /> このパラメーターに渡された項目は省略可能なメタデータ エントリをという名前を持つこと `LogicalName` と `Access`です。 `LogicalName` 対応する、 `identifier` のパラメーター、 `/resource` 切り替えると `Access` に対応する `accessibility-modifier` パラメーター。 詳細については、次を参照してください。 [/resource (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)します。|  
|`ResponseFiles`|省略可能な `String` 型のパラメーターです。<br /><br /> このタスク用のコマンドを含む応答ファイルを指定します。 詳細については、次を参照してください。 [@ (応答ファイルの指定)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option)します。|  
|`Sources`|省略可能な <xref:Microsoft.Build.Framework.ITaskItem>`[]` パラメーター。<br /><br /> 1 つまたは複数指定 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ソース ファイルです。|  
|`TargetType`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルのファイル形式を指定します。 このパラメーターの値を持つことができます `library`, 、コード ライブラリを作成する `exe`, 、コンソール アプリケーションを作成する `module`, 、モジュールの場合、作成または `winexe`, 、Windows プログラムを作成します。 既定値は `library` です。 詳細については、次を参照してください。 [/target (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)します。|  
|`TreatWarningsAsErrors`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 場合 `true`, 、すべての警告をエラーとして扱います。 詳細については、次を参照してください。 [/warnaserror (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)します。|  
|`UseHostCompilerIfAvailable`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> 使用可能な場合は、インプロセス コンパイラ オブジェクトを使用してタスクを指示します。 のみ使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。|  
|`Utf8Output`|省略可能な `Boolean` 型のパラメーターです。<br /><br /> Utf-8 エンコーディングを使用してコンパイラ出力を記録します。 詳細については、次を参照してください。 [/utf8output (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option)します。|  
|`WarningLevel`|省略可能な `Int32` 型のパラメーターです。<br /><br /> 表示するコンパイラの警告レベルを指定します。 詳細については、次を参照してください。 [/warn (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)します。|  
|`WarningsAsErrors`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーとして扱う警告の一覧を指定します。 詳細については、次を参照してください。 [/warnaserror (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)します。<br /><br /> このパラメーターは、 `TreatWarningsAsErrors` パラメーター。|  
|`WarningsNotAsErrors`|省略可能な `String` 型のパラメーターです。<br /><br /> エラーとして扱わない警告の一覧を指定します。 詳細については、次を参照してください。 [/warnaserror (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)します。<br /><br /> このパラメーターは場合、 `TreatWarningsAsErrors` にパラメーターが設定されている `true`します。|  
|`Win32Icon`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイル エクスプ ローラーで必要な外観のようになると、アセンブリに .ico ファイルを挿入します。 詳細については、次を参照してください。 [/win32icon (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)します。|  
|`Win32Manifest`|省略可能な `String` 型のパラメーターです。<br /><br /> 含める Win32 マニフェストを指定します。|  
|`Win32Resource`|省略可能な `String` 型のパラメーターです。<br /><br /> 出力ファイルには、Win32 リソース (.res) ファイルを挿入します。 詳細については、次を参照してください。 [/win32res (c# コンパイラ オプション)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option)します。|  
  
## <a name="remarks"></a>コメント  
 このタスクがからパラメーターを継承する上記のパラメーターだけでなく、 `Microsoft.Build.Tasks.ManagedCompiler` から継承されるクラス、 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 自体クラスから継承、 <xref:Microsoft.Build.Utilities.ToolTask> クラスです。 これらの追加パラメーターとその説明の一覧は、次を参照してください。 [ToolTaskExtension 基本クラス](../msbuild/tooltaskextension-base-class.md)します。  
  
## <a name="example"></a>例  
 次の例では、 `Csc` のソース ファイルから実行可能ファイルをコンパイルするタスク、 `Compile` アイテム コレクションです。  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)