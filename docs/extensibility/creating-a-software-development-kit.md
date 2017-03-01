---
title: "ソフトウェア開発キットを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1d5ea891137bff643ebfcb67cd739aefeb74c2df
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-software-development-kit"></a>ソフトウェア開発キットを作成します。
ソフトウェア開発キット (SDK) には、Visual Studio での&1; つのアイテムとして参照できるように Api を集めたものです。 **参照マネージャー**  ダイアログ ボックスには、プロジェクトに関連するすべての Sdk が一覧表示します。 SDK をプロジェクトに追加すると、Api は Visual Studio で利用可能にします。  
  
 Sdk の&2; 種類があります。  
  
-   プラットフォーム Sdk は、プラットフォームのアプリを開発するための必須コンポーネントです。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK が開発に必要な[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリです。  
  
-   拡張 Sdk には、オプションのコンポーネントのプラットフォームを拡張するけれども、そのプラットフォームのアプリの開発に必須ですが。  
  
 次のセクションでは、Sdk およびプラットフォーム SDK を作成する方法の一般的なインフラストラクチャをについて説明し、拡張機能 SDK。  
  
-   [プラットフォーム Sdk](#PlatformSDKs)  
  
-   [拡張機能 Sdk](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a>プラットフォーム Sdk  
 プラットフォームのアプリを開発するには、プラットフォーム Sdk が必要です。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK がアプリの開発に必要な[!INCLUDE[win81](../debugger/includes/win81_md.md)]です。  
  
### <a name="installation"></a>インストール  
 すべてのプラットフォーム Sdk は、hklm \software\microsoft\microsoft Sdk にインストールされます\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK ルート] です。 したがって、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] hklm \software\microsoft\microsoft SDKs\Windows\v8.1 に SDK がインストールされています。  
  
### <a name="layout"></a>レイアウト  
 プラットフォーム Sdk には、次のレイアウトがあります。  
  
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
|参照フォルダー|に対してコーディングできる Api が含まれているバイナリが含まれています。 これらは、Windows メタデータ (WinMD) ファイルまたはアセンブリを含めることができます。|  
|デザイン モード フォルダー|前実行/デバッグ時にのみ必要なファイルが含まれています。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物、およびなどが該当<br /><br /> \DesignTime フォルダーに XML ドキュメントを配置する場合は、理想的が XML ドキュメントの参照には、Visual Studio での参照ファイルと一緒に配置される継続されます。 たとえば、XML ドキュメントを参照 \References を\\[構成]\\[arch]\sample.dll \References になります\\[構成]\\[arch]\sample.xml、およびそのドキュメントのローカライズされたバージョンに \References なります\\[config]\\[アーキテクチャ]\\[locale]\sample.xml します。|  
|[構成] フォルダー|フォルダーが&3; つだけが存在することができます。 デバッグ、製品版および CommonConfiguration です。 SDK の作成者は、SDK のコンシューマーを対象とする構成に関係なく、同じ SDK ファイルのセットを使用する必要がある場合 CommonConfiguration の下にファイルを配置できます。|  
|アーキテクチャ フォルダー|サポートされるアーキテクチャの任意のフォルダーが存在できます。 Visual Studio には、次のアーキテクチャがサポートされています。 x86、x64、ARM、および依存しません。 注: Win32 が x86 にマップされ、[anycpu] がニュートラルにマップします。<br /><br /> MSBuild は、プラットフォーム Sdk の \CommonConfiguration\neutral 下でのみ検索されます。|  
|Sdkmanifest.xml 内|このファイルは、Visual Studio が SDK を使用する方法について説明します。 SDK のマニフェストを見て[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **DisplayName:**オブジェクト ブラウザーが参照リストに表示される値。<br /><br /> **PlatformIdentity:**この属性が存在指示 Visual Studio および MSBuild の SDK がプラットフォームの SDK であること、およびこれから追加された参照がコピーされるべきではないローカルにします。<br /><br /> **TargetFramework:**のみを対象とこの値で指定されている同じフレームワークをプロジェクトすることを確認する Visual Studio によってこの属性が使用される属性は、SDK を使用することができます。<br /><br /> **MinVSVersion:**を適用する Sdk のみを使用する Visual Studio によってこの属性を使用します。<br /><br /> **参照:**この属性は、コントロールを含む参照のみを指定する必要があります。 参照がコントロールを格納しているかどうかを指定する方法については、以下を参照してください。|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a>拡張機能 Sdk  
 次のセクションでは、拡張機能 SDK を展開するために必要なものについて説明します。  
  
### <a name="installation"></a>インストール  
 拡張 Sdk は、レジストリ キーを指定せず、特定のユーザーまたはすべてのユーザーに対してインストールできます。 すべてのユーザー用の SDK をインストールするには、次のパスを使用します。  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 ユーザー固有のインストールでは、次のパスを使用します。  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 別の場所を使用する場合は、次の&2; つのいずれかを行う必要があります。  
  
1.  レジストリ キーで指定します。  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     値を持つ (既定値) のサブキーを追加および`<path to SDK><SDKName><SDKVersion>`です。  
  
2.  MSBuild プロパティの追加`SDKReferenceDirectoryRoot`をプロジェクト ファイルです。 このプロパティの値は、参照する、拡張 Sdk が存在するディレクトリの semi コロン区切りのリストです。  
  
### <a name="installation-layout"></a>インストール先のレイアウト  
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
  
1.  \\<>\>\\<>\>: 名前とバージョンの SDK のルートに SDK がパスに対応するフォルダー名から派生した拡張機能です。 MSBuild では、この id を使用して、ディスク上の SDK を検索して、Visual Studio では、この id を表示する、**プロパティ**ウィンドウと**参照マネージャー**ダイアログ。  
  
2.  参照フォルダー: Api が含まれているバイナリです。 Windows メタデータ (WinMD) ファイルまたはアセンブリを指定できます。  
  
3.  Redist フォルダー: ファイルにはランタイム/デバッグのために必要なユーザーのアプリケーションの一部としてパッケージ化する必要があります。 \Redist の下にあるすべてのバイナリを配置する必要があります\\<>\>\\<>\>であり、バイナリ名の一意性を確保するのには、次の形式を持つこと: **\<会社 >.\<製品 > します。\<目的 > します。\<extension>**. たとえば、Microsoft.Cpp.Build.dll です。 名前衝突する可能性があります (たとえば、javascript、css、pri、xaml、png、jpg ファイル) その他の Sdk からのファイル名を持つすべてのファイルを \redist の下に配置する必要があります\\<>\>\\<>\>\\<>\>\ XAML に関連付けられているファイルは除外を制御します。 これらのファイルを \redist の下に配置する必要があります\\<>\>\\<>\>\\<>\>\\します。  
  
4.  デザイン時フォルダー: 前の実行/デバッグだけに必要なファイルを選択して同時ユーザーのアプリケーションの一部としてパッケージ化するべきではありません。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物、およびなどを指定できます。 ネイティブ プロジェクトで使用する必要がありますがある、任意の SDK、 *SDKName*.props ファイルです。 この種類のファイルのサンプルを次に示します。  
  
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
  
     XML のリファレンス ドキュメントは、参照ファイルと一緒に配置されます。 XML リファレンスのドキュメントなど、 **\References\\<>\>\\<>\>\sample.dll**アセンブリが**\References\\<>\>\\<>\>\sample.xml**、およびそのドキュメントのローカライズされたバージョンが**\References\\<>\>\\<>\>\\<>\>\sample.xml**します。  
  
5.  [構成] フォルダー:&3; つのサブフォルダー: デバッグ、量販店、および CommonConfiguration です。 SDK の作成者は、SDK のコンシューマーの対象となる構成に関係なく、同じ SDK ファイルのセットを使用する必要がある場合 CommonConfiguration の下にファイルを配置できます。  
  
6.  アーキテクチャ フォルダー: 次のアーキテクチャがサポートされている。 x86、x64、ARM、中立です。 Win32 は、x86 にマップし、[anycpu] がニュートラル マップします。  
  
### <a name="sdkmanifestxml"></a>Sdkmanifest.xml 内  
 このファイルは、Visual Studio が SDK を使用する方法について説明します。 次に例を示します。  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 次の一覧は、ファイルの要素を示しています。  
  
1.  DisplayName: 参照マネージャー、ソリューション エクスプ ローラー、オブジェクト ブラウザー、および Visual Studio のユーザー インターフェイスでは、他の場所に表示される値。  
  
2.  ProductFamilyName: 全体的な SDK 製品名。 たとえば、 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK が SDK の製品ファミリ、"Microsoft.WinJS"の同じファミリに属している"Microsoft.WinJS.1.0"と"Microsoft.WinJS.2.0"という名前です。 この属性は、その接続を作成するには、Visual Studio および MSBuild を使用します。 この属性が存在しない場合、SDK の名前は、製品ファミリ名として使用されます。  
  
3.  FrameworkIdentity: は、この属性の値は、コンシューマー側アプリケーションのマニフェストに挿入されて&1; つまたは複数の Windows コンポーネント ライブラリの依存関係を指定します。 この属性は、Windows コンポーネント ライブラリにのみ適用されます。  
  
4.  TargetFramework: 参照マネージャーと、ツールボックスで使用できる Sdk を指定します。 これは、ターゲット フレームワーク モニカーのセミコロン区切りのリストなど".NET Framework、バージョン = v2.0; .NET Framework、バージョン = v4.5.1"です。 同じターゲット フレームワークのいくつかのバージョンを指定する場合、参照マネージャーは、フィルタ リングのため指定された最下位のバージョンを使用します。 たとえば場合、".NET Framework、バージョン = v2.0; .NET Framework、バージョン v4.5.1 ="参照マネージャーを使用して、指定".NET Framework、バージョン = v2.0"です。 特定のターゲット フレームワーク プロファイルが指定されている場合のみそのプロファイルが使用されます参照マネージャーでフィルタ リングのためです。 たとえばときに、"、Silverlight バージョン v4.0、プロファイルの = = WindowsPhone"が指定されている参照マネージャーが Windows Phone プロファイルのみをフィルター処理完全版の Silverlight 4.0 Framework を対象とするプロジェクトでは、SDK 参照マネージャーでは表示されません。  
  
5.  MinVSVersion: 最小バージョンの Visual Studio です。  
  
6.  MaxPlatformVerson: 拡張機能 SDK を使うことはできませんプラットフォームのバージョンを指定する最大のターゲット プラットフォームのバージョンを使用する必要があります。 たとえば、Microsoft Visual C ランタイム パッケージ v11.0 は、Windows 8 プロジェクトでのみ参照する必要があります。 したがって、Windows 8 プロジェクトの MaxPlatformVersion は 8.0 です。 つまり参照マネージャーが Windows 8.1 プロジェクトでは、Microsoft Visual C ランタイム パッケージをフィルター処理され、MSBuild はエラーをスロー時に、[!INCLUDE[win81](../debugger/includes/win81_md.md)]プロジェクトでは、それを参照します。 注: この要素は、以降でサポート[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]します。  
  
7.  AppliesTo: では、適用可能な Visual Studio プロジェクトの種類を指定することで、参照マネージャーで使用できる Sdk を指定します。 9 個の値が認識されます。 WindowsAppContainer、Visualc++、VB、CSharp、WindowsXAML、JavaScript、管理、およびネイティブです。 SDK の作成者が使用でき、("+')、または ("|") ではなく、("!")演算子を正確に、SDK に適用されるプロジェクトの種類のスコープを指定します。  
  
     WindowsAppContainer のプロジェクトを識別する[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリです。  
  
8.  SupportPrefer32Bit: サポートされている値は"True"および"False"です。 既定では"True です"。 MSBuild エラーが返されます値が"False"に設定されている場合[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]プロジェクト (またはデスクトップ プロジェクトの警告)、SDK を参照するプロジェクトに有効になっている Prefer32Bit がある場合。 Prefer32Bit の詳細については、次を参照してください。[ビルド ページは、プロジェクト デザイナー (c#)](../ide/reference/build-page-project-designer-csharp.md)または[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)します。  
  
9. SupportedArchitectures: セミコロンで区切られた、SDK をサポートするアーキテクチャの一覧です。 MSBuild では、利用するプロジェクトで対象となる SDK アーキテクチャがサポートされていない場合に警告が表示されます。 この属性が指定されていない場合は、MSBuild は決してこの種類の警告を表示します。  
  
10. SupportsMultipleVersions: にこの属性が設定されている場合は、**エラー**または**警告**MSBuild では、同じプロジェクトが同じ SDK ファミリの複数のバージョンを参照できないことを示します。 この属性が存在しないかに設定されている場合**許可**MSBuild は、この種類のエラーまたは警告を表示しません。  
  
11. AppX: は、ディスク上の Windows コンポーネント ライブラリのアプリ パッケージのパスを指定します。 この値は、ローカル デバッグ時に、Windows コンポーネント ライブラリの登録のコンポーネントに渡されます。 ファイル名の名前付け規則は**\<会社 >.\<製品 > します。\<アーキテクチャ > します。\<構成 > します。\<バージョン >.appx**します。 Windows コンポーネント ライブラリには適用されない場合の構成とアーキテクチャには、属性名と属性値省略可能です。 この値は、Windows コンポーネント ライブラリにのみ適用されます。  
  
12. CopyRedistToSubDirectory: アプリ パッケージのルートに対する相対 \redist フォルダーの下にあるファイルをコピーするかを指定する (つまり、**パッケージの場所**アプリ パッケージの作成ウィザードで選択された) とランタイムのレイアウトのルートです。 既定の場所は、アプリ パッケージと f5 キーを押してレイアウトのルートです。  
  
13. DependsOn: この SDK が依存する Sdk を定義する SDK id の一覧です。 この属性は、参照マネージャーの詳細ウィンドウに表示されます。  
  
14. 詳細情報: ヘルプと詳細情報を提供する web ページの URL。 この値は、参照マネージャー の右側のウィンドウで 詳細 リンクで使用されます。  
  
15. 登録の種類: は WinMD 登録をアプリ マニフェストで指定し、対応する実装 DLL ネイティブ WinMD で必要です。  
  
16. ファイル参照: は、ネイティブ Winmd コントロールが含まれている参照のみを指定します。 参照がコントロールを格納しているかどうかを指定する方法については、次を参照してください。[ツールボックス項目の場所を指定する](#ToolboxItems)以下です。  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>ツールボックス項目の場所を指定します。  
 Sdkmanifest.xml 内のスキーマの ToolBoxItems 要素は、プラットフォームと拡張機能 Sdk の両方で、カテゴリとツールボックス項目の場所を指定します。 次の例では、別の場所を指定する方法を示します。 これは、WinMD または DLL のいずれかの参照に適用します。  
  
1.  既定のツールボックス カテゴリにコントロールを配置します。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  特定のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  特定のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Blend および Visual Studio では、別のカテゴリ名の下にあるコントロールを配置します。  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Blend と Visual Studio の異なる方法で特定の制御を列挙します。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  特定のコントロールを列挙し、Visual Studio の共通パスの下、またはすべてのコントロール グループにのみに配置します。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  特定のコントロールを列挙し、ChooseItems にせずに特定のセットのみを表示、ツールボックスにあるものです。  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: C++ を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [チュートリアル: c# または Visual Basic を使用して SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)
