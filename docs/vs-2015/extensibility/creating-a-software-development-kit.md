---
title: ソフトウェア開発キットの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7c3ff7a3a8c872c4b624c8d2956a6802a0ab139
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723674"
---
# <a name="creating-a-software-development-kit"></a>ソフトウェア開発キットを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ソフトウェア開発キット (SDK) は、Visual Studio での 1 つの項目として参照できる Api のコレクションです。 **参照マネージャー**  ダイアログ ボックスに、プロジェクトに関連するすべての Sdk が一覧表示されます。 SDK をプロジェクトに追加するときに、Api は Visual Studio で使用できます。  
  
 Sdk の 2 種類あります。  
  
- プラットフォーム Sdk は、プラットフォームのアプリを開発するための必須コンポーネントです。 たとえば、 [!INCLUDE[win81](../includes/win81-md.md)] SDK が開発に必要な[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]アプリ。  
  
- 拡張機能 Sdk は、オプション コンポーネントをプラットフォームを拡張ものの、そのプラットフォームのアプリを開発するために必須です。  
  
  次のセクションでは、Sdk、platform SDK を作成する方法の一般的なインフラストラクチャを記述して、拡張機能 SDK。  
  
- [プラットフォーム Sdk](#PlatformSDKs)  
  
- [拡張機能 Sdk](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> プラットフォーム Sdk  
 プラットフォーム Sdk は、プラットフォームのアプリを開発する必要があります。 たとえば、 [!INCLUDE[win81](../includes/win81-md.md)] SDK がアプリの開発に必要な[!INCLUDE[win81](../includes/win81-md.md)]します。  
  
### <a name="installation"></a>インストール  
 すべてのプラットフォーム Sdk は、hklm \software\microsoft\microsoft Sdk にインストールされます\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK ルート]。 したがって、 [!INCLUDE[win81](../includes/win81-md.md)] hklm \software\microsoft\microsoft SDKs\Windows\v8.1 で SDK がインストールされています。  
  
### <a name="layout"></a>レイアウト  
 プラットフォーム Sdk は、次のレイアウトが完成します。  
  
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
|参照フォルダー|に対してコーディングすることがある Api が含まれているバイナリが含まれています。 Windows メタデータ (WinMD) ファイルまたはアセンブリに含めることができます。|  
|DesignTime フォルダー|事前実行/デバッグ時にのみ必要なファイルが含まれています。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物などが該当<br /><br /> \DesignTime フォルダーに XML ドキュメントを配置する場合は、理想的には、引き続き XML ドキュメントの参照を Visual Studio での参照ファイルの横に配置されます。 たとえば、XML ドキュメントを参照 \References を\\[config]\\[arch]\sample.dll \References になります\\[config]\\[arch]\sample.xml、およびそのドキュメントのローカライズされたバージョンに \Referencesなります\\[config]\\[arch]\\[locale]\sample.xml します。|  
|構成フォルダー|3 つのフォルダーが存在することができます。 デバッグ、製品版と CommonConfiguration します。 SDK の作成者は、SDK コンシューマーが対象とする構成に関係なく、同じ SDK ファイルのセットを使用する必要がある場合 CommonConfiguration の下にファイルを配置できます。|  
|フォルダーのアーキテクチャ|サポートされているアーキテクチャの任意のフォルダーが存在できます。 Visual Studio には、次のアーキテクチャがサポートされています。 x86、x64、ARM、および neutral です。 注: Win32 が x86 にマップされ、AnyCPU がニュートラルにマップされます。<br /><br /> MSBuild は、プラットフォーム Sdk の \CommonConfiguration\neutral 下でのみ検索されます。|  
|SDKManifest.xml|このファイルは、Visual Studio が SDK を使用する方法について説明します。 SDK のマニフェストを見て[!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** オブジェクト ブラウザーが、参照リストに表示される値。<br /><br /> **PlatformIdentity:** この属性が存在するように指示 Visual Studio および MSBuild SDK がプラットフォームの SDK であること、およびそこから追加された参照をコピーすることはできませんローカルです。<br /><br /> **TargetFramework:** させるのみを対象の値で指定されている同じフレームワークをプロジェクトを Visual Studio によってこの属性が使用されます属性は、SDK を使用できます。<br /><br /> **MinVSVersion:** を適用する Sdk のみを使用する Visual Studio によってこの属性が使用されます。<br /><br /> **参照:** この属性は、コントロールを含む参照のみを指定する必要があります。 参照がコントロールを格納するかどうかを指定する方法については、以下を参照してください。|  
  
##  <a name="ExtensionSDKs"></a> 拡張機能 Sdk  
 次のセクションでは、拡張機能 SDK を展開するために必要がありますについて説明します。  
  
### <a name="installation"></a>インストール  
 拡張機能 Sdk は、レジストリ キーを指定せず、特定のユーザーまたはすべてのユーザーに対してインストールできます。 すべてのユーザー用の SDK をインストールするには、次のパスを使用します。  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 ユーザー固有のインストールでは、次のパスを使用します。  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 別の場所を使用する場合は、次の 2 つのいずれかを行う必要があります。  
  
1.  レジストリ キーで指定します。  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     値を持つ (既定値) のサブキーを追加および`<path to SDK><SDKName><SDKVersion>`します。  
  
2.  MSBuild プロパティを追加`SDKReferenceDirectoryRoot`をプロジェクト ファイル。 このプロパティの値を参照する、拡張 Sdk が存在するディレクトリの半コロン区切りのリストです。  
  
### <a name="installation-layout"></a>インストール レイアウト  
 拡張 Sdk には、次のインストールのレイアウトがあります。  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: SDK は、SDK ルートへのパスに対応するフォルダー名から派生する拡張機能のバージョンと名前。 MSBuild では、この id を使用して、ディスク上の SDK を検索し、Visual Studio でこの id が表示されます、**プロパティ**ウィンドウと**参照マネージャー**ダイアログ。  
  
2.  [参照] フォルダー: Api が含まれているバイナリ。 Windows メタデータ (WinMD) ファイルまたはアセンブリを指定できます。  
  
3.  Redist フォルダー: ファイルをランタイム/デバッグが必要であり、ユーザーのアプリケーションの一部としてパッケージ化する必要があります。 \Redist 下にあるすべてのバイナリを配置する必要があります\\< config\>\\< arch\>、バイナリ名に次の形式に一意性を確保する必要があります: **\<会社 >.\<製品 >。\<目的 >。\<拡張機能 >** します。 たとえば、Microsoft.Cpp.Build.dll です。 その他の Sdk (たとえば、javascript、css、pri、xaml、png、jpg ファイル) からファイル名と名前が衝突したを持つすべてのファイルを \redist の下に配置する\\< config\>\\< arch\> \\< sdkname\>\ XAML に関連付けられているファイルを除くを制御します。 これらのファイルを \redist の下に配置する必要があります\\< config\>\\< arch\>\\< componentname\>\\します。  
  
4.  DesignTime フォルダー: 前の実行/デバッグのみで必要なファイルは、時間し、ユーザーのアプリケーションの一部としてパッケージ化することはできません。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物などを指定できます。 ネイティブ プロジェクトで消費する必要がありますを指定することが想定されている任意の SDK、 *SDKName*.props ファイル。 この種類のファイルのサンプルを次に示します。  
  
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
  
     XML のリファレンス ドキュメントは、参照ファイルの横に配置されます。 たとえば、XML の参照ドキュメント、 **\References\\< config\>\\< arch\>\sample.dll**アセンブリが**\References\\< config\>\\< arch\>\sample.xml**でそのドキュメントのローカライズされたバージョンは**\References\\< config\>\\<arch\>\\< ロケール\>\sample.xml**します。  
  
5.  構成フォルダー: 3 つのサブフォルダー: デバッグ、製品版、および CommonConfiguration します。 SDK の作成者は、SDK コンシューマーの対象となる構成に関係なく、同じ SDK ファイルのセットを使用する必要がありますと CommonConfiguration の下にファイルを配置できます。  
  
6.  アーキテクチャ フォルダー: 次のアーキテクチャがサポートされています: x86、x64、ARM、中立です。 Win32 は、x86 にマップされ、AnyCPU がニュートラルにマップされます。  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
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
  
 次の一覧は、ファイルの要素を示しています。  
  
1.  DisplayName: 参照マネージャー、ソリューション エクスプ ローラー、オブジェクト ブラウザー、および Visual Studio のユーザー インターフェイスの他の場所に表示される値。  
  
2.  ProductFamilyName: 全体的な SDK 製品名。 たとえば、 [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK の名前は"Microsoft.WinJS.1.0"と"Microsoft.WinJS.2.0"、"Microsoft.WinJS"SDK の製品ファミリの同じファミリに属しています。 この属性は、その接続を作成するには、Visual Studio および MSBuild を使用できます。 この属性が存在しない場合、SDK の名前は、製品ファミリ名として使用されます。  
  
3.  対応する FrameworkIdentity: は、かかるアプリのマニフェストにこの属性の値が挿入されて 1 つまたは複数の Windows コンポーネント ライブラリの依存関係を指定します。 この属性は、Windows コンポーネント ライブラリにのみ適用されます。  
  
4.  TargetFramework: 参照マネージャーと、ツールボックスで使用できる Sdk を指定します。 これは、ターゲット フレームワークのモニカーのセミコロン区切りのリストなど".NET Framework、バージョン = v2.0; .NET Framework、バージョン = v4.5.1"。 同じターゲット フレームワークのいくつかのバージョンが指定されている場合、参照マネージャーは、フィルタ リングするための指定された最低バージョンを使用します。 たとえば場合、".NET Framework、バージョン = v2.0; .NET Framework、バージョン = v4.5.1"参照マネージャーを使用して、指定".NET Framework、バージョン = v2.0"。 特定のターゲット フレームワーク プロファイルが指定されている場合のみそのプロファイルが使用されます参照マネージャーによってフィルタ リングするためです。 たとえば、"Silverlight、バージョン = v4.0、プロファイル WindowsPhone ="が指定されている参照マネージャーは、Windows Phone プロファイルのみに基づくフィルター処理完全な Silverlight 4.0 Framework をターゲットとするプロジェクトでは、SDK 参照マネージャーでは表示されません。  
  
5.  MinVSVersion: 最小 Visual Studio のバージョン。  
  
6.  MaxPlatformVerson: 拡張機能 SDK を使うことはできませんのプラットフォームのバージョンを指定する最大のターゲット プラットフォームのバージョンを使用する必要があります。 たとえば、Windows 8 のプロジェクトでのみ Microsoft Visual C ランタイム パッケージ v11.0 を参照する必要があります。 したがって、Windows 8 プロジェクトの MaxPlatformVersion は 8.0 です。 つまり、Windows 8.1 プロジェクトの場合、参照マネージャーが Microsoft Visual C ランタイム パッケージをフィルター処理、MSBuild は、エラーをスローします。 ときに、[!INCLUDE[win81](../includes/win81-md.md)]プロジェクトでは、それを参照します。 注: この要素は、以降でサポート[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]します。  
  
7.  AppliesTo:、該当する Visual Studio プロジェクトの種類を指定することで、参照マネージャーで使用できる Sdk を指定します。 9 個の値が認識されます。 WindowsAppContainer、Visualc++、VB、CSharp、WindowsXAML、JavaScript、マネージ、およびネイティブです。 SDK の作成者が使用でき、("+')、または ("&#124;") ではなく、("!")演算子を正確に、SDK に適用されるプロジェクトの種類のスコープを指定します。  
  
     WindowsAppContainer 識別用のプロジェクト[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]アプリ。  
  
8.  SupportPrefer32Bit: サポートされる値は"True"および"False"。 既定では"True です"。 MSBuild エラーが返されます、値が"False"に設定されている場合[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]プロジェクト (またはデスクトップ プロジェクトの場合の警告)、SDK を参照するプロジェクトがある Prefer32Bit が有効になっている場合。 Prefer32Bit の詳細については、次を参照してください。[ビルド ページは、プロジェクト デザイナー (c#)](../ide/reference/build-page-project-designer-csharp.md)または[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)します。  
  
9. SupportedArchitectures: セミコロンで区切り、SDK は、サポートされるアーキテクチャのリストです。 MSBuild では、使用中のプロジェクトで対象となる SDK のアーキテクチャがサポートされていない場合に警告が表示されます。 この属性が指定されていない場合 MSBuild にはこの種類の警告が表示されません。  
  
10. SupportsMultipleVersions: この属性設定されている場合**エラー**または**警告**MSBuild では、同じプロジェクトが同じ SDK ファミリの複数のバージョンを参照できないことを示します。 この属性が存在しないかに設定されている場合**許可**MSBuild は、この種類のエラーまたは警告を表示しません。  
  
11. AppX: は、ディスク上の Windows コンポーネント ライブラリ用のアプリ パッケージへのパスを指定します。 この値は、ローカル デバッグ中に、Windows コンポーネント ライブラリの登録コンポーネントに渡されます。 ファイル名の名前付け規則は**\<会社 >.\<製品 >。\<アーキテクチャ >。\<Configuration >。\<バージョン > .appx**します。 Windows コンポーネント ライブラリには適用されない場合の構成とアーキテクチャには、属性名および属性値の省略可能です。 この値は、Windows コンポーネント ライブラリにのみ適用されます。  
  
12. CopyRedistToSubDirectory: は、アプリ パッケージのルートに対する相対 \redist フォルダーの下のファイルをコピーする必要がありますを指定します (つまり、**パッケージの場所**アプリ パッケージの作成ウィザードで選択した) とランタイムのレイアウト ルート。 既定の場所は、f5 キーを押してレイアウト、アプリ パッケージのルートです。  
  
13. DependsOn: この SDK が依存する Sdk を定義する SDK の id の一覧。 この属性は、参照マネージャーの詳細ウィンドウに表示されます。  
  
14. 詳細情報: ヘルプと詳細情報を提供する web ページへの URL。 この値は、右側のウィンドウ参照マネージャーの詳細情報のリンクで使用されます。  
  
15. 登録の種類: は、アプリ マニフェストで WinMD 登録を指定し、DLL の対応する実装がありますが、ネイティブ WinMD が必要です。  
  
16. ファイル参照。 または、コントロールを含む、ネイティブ Winmd を参照のみ指定。 参照がコントロールを格納するかどうかを指定する方法については、次を参照してください。[ツールボックス項目の場所を指定する](#ToolboxItems)以下。  
  
##  <a name="ToolboxItems"></a> ツールボックス項目の場所を指定します。  
 SDKManifest.xml スキーマの ToolBoxItems 要素は、プラットフォームと拡張機能 Sdk の両方で、カテゴリとツールボックス項目の場所を指定します。 次の例では、別の場所を指定する方法を示します。 これは、WinMD または DLL のいずれかの参照に適用されます。  
  
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
  
4.  Blend と Visual Studio では、さまざまなカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Blend と Visual Studio の異なる方法で特定の制御を列挙します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  特定のコントロールを列挙し、すべてのコントロール グループのみまたは Visual Studio の一般的なパスの下に配置します。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  特定のコントロールを列挙し、なくて ChooseItems で特定のセットのみを表示、ツールボックスにされています。  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: C++ を使用して、SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [チュートリアル: c# または Visual Basic を使用して、SDK の作成](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)

