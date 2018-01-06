---
title: "ソフトウェア開発キットの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4ea17b02cfa2e987c4a3c02acddf838001b4ae2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-software-development-kit"></a>ソフトウェア開発キットを作成する
ソフトウェア開発キット (SDK) は、Visual Studio での 1 つのアイテムとして参照できる Api のコレクションです。 **参照マネージャー**  ダイアログ ボックスに、プロジェクトに関連するすべての Sdk が一覧表示されます。 SDK をプロジェクトに追加するときに Api は Visual Studio で使用できます。  
  
 Sdk の 2 つの種類があります。  
  
-   プラットフォーム Sdk は、プラットフォームのアプリを開発するための必須コンポーネントです。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK は、開発に必要な[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリ。  
  
-   拡張機能 Sdk は、プラットフォームを拡張するけれども、そのプラットフォームのアプリを開発するために必須です省略可能なコンポーネントです。  
  
 次のセクションでは、Sdk と、プラットフォーム SDK を作成する方法の一般的なインフラストラクチャをについて説明し、拡張機能 SDK。  
  
-   [プラットフォーム Sdk](#PlatformSDKs)  
  
-   [拡張機能 Sdk](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a>プラットフォーム Sdk  
 プラットフォームのアプリを開発するには、プラットフォーム Sdk が必要です。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK が用のアプリの開発に必要な[!INCLUDE[win81](../debugger/includes/win81_md.md)]します。  
  
### <a name="installation"></a>インストール  
 Hklm \software\microsoft\microsoft Sdk ですべてのプラットフォーム Sdk がインストールされる\\[TPI] \v [TPV]\\ @InstallationFolder [SDK ルート] を = です。 したがって、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] hklm \software\microsoft\microsoft SDKs\Windows\v8.1 で SDK がインストールされています。  
  
### <a name="layout"></a>レイアウト  
 プラットフォーム Sdk は、次のレイアウトが得られます。  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|ノード|説明|  
|----------|-----------------|  
|参照フォルダー|に対してコーディングできる Api が含まれているバイナリが含まれています。 Windows メタデータ (WinMD) ファイルまたはアセンブリが該当します。|  
|DesignTime フォルダー|前の実行/デバッグ時にのみ必要なファイルが含まれています。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時バイナリ、MSBuild の成果物などが該当<br /><br /> XML ドキュメントは、理想的には、フォルダーに配置する、\DesignTime が、XML ドキュメントの参照には引き続き Visual Studio での参照ファイルと一緒に配置します。 たとえば、XML ドキュメントを参照 \References を\\[config]\\[arch]\sample.dll \References になります\\[config]\\[arch]\sample.xml、およびそのドキュメントのローカライズ版なります \References\\[config]\\[アーキテクチャ]\\[locale]\sample.xml です。|  
|[構成] フォルダー|3 つのフォルダーが存在することができます。 デバッグ、小売および CommonConfiguration です。 SDK の作成者は、SDK のコンシューマーが対象とする構成に関係なく、同じ SDK ファイルのセットを使用する必要がある場合 CommonConfiguration の下にファイルを配置できます。|  
|アーキテクチャのフォルダー|サポートされるアーキテクチャの任意のフォルダーが存在できます。 Visual Studio には、次のアーキテクチャがサポートされています。 x86、x64、ARM、および neutral です。 注: Win32 が x86 にマップされ、AnyCPU がニュートラルにマップします。<br /><br /> MSBuild は、プラットフォーム Sdk を \CommonConfiguration\neutral 下でのみ検索します。|  
|Sdkmanifest.xml 内|このファイルは、Visual Studio が SDK を使用する方法について説明します。 SDK マニフェストを見て[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:**オブジェクト ブラウザーが、参照一覧に表示される値。<br /><br /> **PlatformIdentity:**この属性の存在に指示 Visual Studio および MSBuild の SDK がプラットフォーム SDK であること、およびそこから追加された参照がコピーされるべきではありませんローカルです。<br /><br /> **TargetFramework:**のみを対象との値で指定されている同じフレームワークをプロジェクトすることを確認する Visual Studio によってこの属性が使用される属性は、SDK を使用できます。<br /><br /> **MinVSVersion:**に適用する Sdk のみを使用する Visual Studio によってこの属性を使用します。<br /><br /> **参照:**この属性は、コントロールを含む参照のみを指定する必要があります。 参照がコントロールを含むかどうかを指定する方法の詳細については、後述します。|  
  
##  <a name="ExtensionSDKs"></a>拡張機能 Sdk  
 次のセクションでは、拡張機能 SDK を展開するために必要なものについて説明します。  
  
### <a name="installation"></a>インストール  
 拡張機能 Sdk は、レジストリ キーを指定せず、特定のユーザーまたはすべてのユーザーに対してインストールできます。 すべてのユーザー用の SDK をインストールするには、次のパスを使用します。  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 ユーザー固有のインストールでは、次のパスを使用します。  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 別の場所を使用する場合は、次の 2 つのいずれかを行う必要があります。  
  
1.  レジストリ キーで指定します。  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     値を持つ (既定値) のサブキーを追加および`<path to SDK><SDKName><SDKVersion>`です。  
  
2.  MSBuild プロパティの追加`SDKReferenceDirectoryRoot`をプロジェクト ファイルです。 このプロパティの値を参照する、拡張 Sdk が存在するディレクトリの半コロン区切りのリストです。  
  
### <a name="installation-layout"></a>インストール レイアウト  
 拡張 Sdk には、次のインストール レイアウトがあります。  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< sdk 名\>\\< SDKVersion\>: SDK のルートに SDK は、パスに対応するフォルダー名から派生した拡張機能のバージョンと名前。 MSBuild では、この id を使用して、ディスク上の SDK を検索し、Visual Studio でこの id を表示する、**プロパティ**ウィンドウと**参照マネージャー**ダイアログ。  
  
2.  参照フォルダー: Api が含まれているバイナリです。 これらは、Windows メタデータ (WinMD) ファイルまたはアセンブリがあります。  
  
3.  Redist フォルダー: ファイルをランタイム/デバッグが必要であり、ユーザーのアプリケーションの一部としてパッケージ化を取得する必要があります。 \Redist 下にあるすべてのバイナリを配置する必要があります\\< config\>\\< arch\>があり、一意性を確保するのには、次の形式は、バイナリ名: **\<会社 >.\<製品 >。\<目的 >。\<拡張子 >**です。 たとえば、Microsoft.Cpp.Build.dll です。 名前衝突する可能性があります (たとえば、javascript、css、pri、xaml、png、jpg ファイル) その他の Sdk からのファイル名を持つすべてのファイルを \redist の下に配置する必要があります\\< config\>\\< arch\> \\< sdk 名\>\ XAML に関連付けられているファイルを除くを制御します。 これらのファイルを \redist の下に配置する必要があります\\< config\>\\< arch\>\\< componentname\>\\です。  
  
4.  DesignTime フォルダー: 前の実行/デバッグのみで必要なファイルは、時間し、ユーザーのアプリケーションの一部としてパッケージ化することはできません。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時バイナリ、MSBuild の成果物などを指定できます。 ネイティブ プロジェクトによる消費を持っていなければなりませんためのものでは、すべての SDK、 *sdk 名*.props ファイル。 この種類のファイルのサンプルを次に示します。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML のリファレンス ドキュメントは、参照ファイルと一緒に配置されます。 たとえばの参照の XML ドキュメント、 **\References\\< config\>\\< arch\>\sample.dll**アセンブリが**\References\\< config\>\\< arch\>\sample.xml**、そのドキュメントのローカライズ版は**\References\\< config\>\\<arch\>\\< ロケール\>\sample.xml**です。  
  
5.  構成フォルダー: 3 つのサブフォルダー: デバッグ、量販店、および CommonConfiguration です。 SDK の作成者は、SDK のコンシューマーの対象となる構成に関係なく、同じ SDK ファイルのセットを使用する必要がある場合 CommonConfiguration の下にファイルを配置できます。  
  
6.  アーキテクチャ フォルダー: 次のアーキテクチャがサポートされる: x86、x64、ARM、ニュートラルです。 Win32 は、x86 にマップされ、AnyCPU がニュートラルにマップします。  
  
### <a name="sdkmanifestxml"></a>Sdkmanifest.xml 内  
 このファイルは、Visual Studio が SDK を使用する方法について説明します。 次に例を示します。  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 ファイルの要素を次に示します。  
  
1.  DisplayName: 参照マネージャー、ソリューション エクスプ ローラー、オブジェクト ブラウザー、および Visual Studio のユーザー インターフェイスでは、他の場所に表示される値。  
  
2.  ProductFamilyName: 全体的な SDK 製品名。 たとえば、 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] "Microsoft.WinJS.1.0"と"Microsoft.WinJS.2.0"、"microsoft. winjs"、SDK 製品ファミリの同じファミリに属している、SDK がという名前です。 この属性は、その接続を作成するには、Visual Studio および MSBuild を使用します。 この属性が存在しない場合、SDK 名では、製品ファミリ名として使用されます。  
  
3.  FrameworkIdentity: は、この属性の値は、使用のアプリのマニフェストに格納 1 つまたは複数の Windows コンポーネント ライブラリの依存関係を指定します。 この属性は、Windows コンポーネント ライブラリにのみ適用されます。  
  
4.  TargetFramework: 参照マネージャーと、ツールボックスで使用可能な Sdk を指定します。 これは、ターゲット フレームワーク モニカーのセミコロン区切りのリストなど".NET Framework, version = v2.0; .NET Framework, version = v4.5.1"です。 同じターゲット フレームワークのいくつかのバージョンが指定されている場合、参照マネージャーは、フィルタ リングするための指定された最低バージョンを使用します。 たとえば場合、".NET Framework, version = v2.0; .NET Framework, version = v4.5.1"を指定すると、参照マネージャーが使用されます".NET Framework, version v2.0 を ="です。 特定のターゲット フレームワーク プロファイルが指定されている場合そのプロファイルにのみ使用されます参照マネージャーによってフィルタ リングのため。 たとえば、"、Silverlight バージョン v4.0、プロファイルを = WindowsPhone を ="が指定されている; Windows Phone のプロファイルのみでフィルターが参照マネージャー完全な Silverlight 4.0 Framework を対象とするプロジェクトでは、SDK 参照マネージャーでは表示されません。  
  
5.  MinVSVersion: 最小バージョンの Visual Studio です。  
  
6.  MaxPlatformVerson: 拡張機能 SDK を使うことはできません、プラットフォームのバージョンを指定する最大のターゲット プラットフォーム バージョンを使用してください。 たとえば、Microsoft Visual C ランタイム パッケージ v11.0 は、Windows 8 プロジェクトでのみ参照必要があります。 したがって、Windows 8 プロジェクトの MaxPlatformVersion が 8.0 が。 つまり、参照マネージャーが、Windows 8.1 プロジェクトの Microsoft Visual C ランタイム パッケージをフィルター処理、MSBuild はエラーをスロー時に、[!INCLUDE[win81](../debugger/includes/win81_md.md)]プロジェクトでは、それを参照します。 注: この要素は、以降ではサポート[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]です。  
  
7.  AppliesTo: は、適用可能な Visual Studio プロジェクトの種類を指定することによって、参照マネージャーで使用できる、Sdk を指定します。 9 個の値が認識されます。 WindowsAppContainer、Visualc++、VB、CSharp、WindowsXAML、JavaScript、管理、およびネイティブです。 SDK の作成者が使用できると ("+')、または ("&#124;)、されません ("!")演算子を正確に SDK に適用されるプロジェクトの種類のスコープを指定します。  
  
     WindowsAppContainer 識別用のプロジェクト[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリ。  
  
8.  SupportPrefer32Bit: サポートされる値は"True"および"False"です。 既定値は、"True"です。 MSBuild でのエラーを返します、値が"False"に設定されている場合[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]プロジェクト (またはデスクトップ プロジェクトの警告)、SDK を参照するプロジェクトでは有効になっている Prefer32Bit 場合。 Prefer32Bit の詳細については、次を参照してください。[ビルド ページで、プロジェクト デザイナー (c#)](../ide/reference/build-page-project-designer-csharp.md)または[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)です。  
  
9. SupportedArchitectures: セミコロンで区切られた、SDK がサポートするアーキテクチャの一覧です。 MSBuild では、対象となる SDK アーキテクチャでは、使用するプロジェクトがサポートされていない場合に警告が表示されます。 この属性が指定されていない場合は、MSBuild は決してこの種類の警告を表示します。  
  
10. SupportsMultipleVersions: この属性に設定されている場合**エラー**または**警告**MSBuild では、同じプロジェクトが同じ SDK ファミリの複数のバージョンを参照できないことを示します。 この属性が存在しないかに設定されている場合**許可**MSBuild では、この種類のエラーまたは警告を表示します。  
  
11. AppX: は、ディスク上の Windows コンポーネント ライブラリ用のアプリ パッケージのパスを指定します。 この値は、ローカル デバッグ中に、Windows コンポーネント ライブラリの登録のコンポーネントに渡されます。 ファイル名の名前付け規則は**\<会社 >.\<製品 >。\<アーキテクチャ >。\<構成 >。\<バージョン > .appx**です。 Windows コンポーネント ライブラリには適用されない場合の構成とアーキテクチャには、属性の名前と属性の値に省略可能です。 この値は、Windows コンポーネント ライブラリにのみ適用されます。  
  
12. CopyRedistToSubDirectory: は、アプリ パッケージのルートに対する相対 \redist フォルダーの下のファイルをコピーするかを指定します (つまり、**パッケージの場所**アプリ パッケージの作成ウィザードで選択された) とランタイムのレイアウト ルート。 既定の場所は、f5 キーを押してレイアウト、アプリ パッケージのルートです。  
  
13. DependsOn: この SDK が依存する Sdk を定義する SDK の id の一覧。 この属性は、参照マネージャーの詳細ペインに表示されます。  
  
14. 詳細情報: ヘルプと詳細情報を提供する web ページの URL です。 この値は、参照マネージャーの右側のペインの詳細リンクで使用されます。  
  
15. 登録の種類: WinMD 登録アプリ マニフェストでを指定して対応する実装 DLL には、ネイティブ WinMD のために必要です。  
  
16. ネイティブ Winmd をまたはコントロールを含む参照のみのファイル参照: を指定します。 参照がコントロールを含むかどうかを指定する方法については、次を参照してください。[ツールボックス項目の場所を指定する](#ToolboxItems)以下です。  
  
##  <a name="ToolboxItems"></a>ツールボックス アイテムの場所を指定します。  
 Sdkmanifest.xml 内のスキーマの ToolBoxItems 要素は、プラットフォームと拡張機能 Sdk の両方で、カテゴリとツールボックス項目の場所を指定します。 次の例では、別の場所を指定する方法を示します。 これは、WinMD または DLL のいずれかの参照に適用します。  
  
1.  既定のツールボックス カテゴリのコントロールを配置します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  特定のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  特定のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Blend および Visual Studio では、別のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Blend および Visual Studio で異なる特定のコントロールを列挙します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  特定のコントロールを列挙し、Visual Studio の共通パスの下、またはすべてのコントロール グループにのみ配置します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  特定のコントロールを列挙し、ChooseItems にせずに特定のセットのみを表示、ツールボックスにあるものです。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>参照  
 [チュートリアル: C++ を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [チュートリアル: c# または Visual Basic を使用して、SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)