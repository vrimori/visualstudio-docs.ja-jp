---
title: ソフトウェア開発キットの作成 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea506479226ed8585296208064bd3533cf0a5783
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922843"
---
# <a name="create-a-software-development-kit"></a>ソフトウェア開発キットを作成します。
ソフトウェア開発キット (SDK) は、Visual Studio での 1 つの項目として参照できる Api のコレクションです。 **参照マネージャー**  ダイアログ ボックスに、プロジェクトに関連するすべての Sdk が一覧表示されます。 SDK をプロジェクトに追加するときに、Api は Visual Studio で使用できます。  

 Sdk の 2 種類あります。  

- プラットフォーム Sdk は、プラットフォームのアプリを開発するための必須コンポーネントです。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK が開発に必要な[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリ。  

- 拡張機能 Sdk は、オプション コンポーネントをプラットフォームを拡張ものの、そのプラットフォームのアプリを開発するために必須です。  

  次のセクションでは、Sdk、platform SDK を作成する方法の一般的なインフラストラクチャを記述して、拡張機能 SDK。  

- [プラットフォーム Sdk](#PlatformSDKs)  

- [拡張機能 Sdk](#ExtensionSDKs)  

##  <a name="PlatformSDKs"></a> プラットフォーム Sdk  
 プラットフォーム Sdk は、プラットフォームのアプリを開発する必要があります。 たとえば、 [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK がアプリの開発に必要な[!INCLUDE[win81](../debugger/includes/win81_md.md)]します。  

### <a name="installation"></a>インストール  
 すべてのプラットフォーム Sdk のインストールで*hklm \software\microsoft\microsoft Sdk\\[TPI] \v [TPV]\\ @InstallationFolder = [SDK ルート]*。 したがって、[!INCLUDE[win81](../debugger/includes/win81_md.md)]で SDK がインストールされている*hklm \software\microsoft\microsoft SDKs\Windows\v8.1*します。  

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


| ノード | 説明 |
|------------------------| - |
| *参照*フォルダー | に対してコーディングすることがある Api が含まれているバイナリが含まれています。 Windows メタデータ (WinMD) ファイルまたはアセンブリに含めることができます。 |
| *デザイン時*フォルダー | 事前実行/デバッグ時にのみ必要なファイルが含まれています。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物などが該当<br /><br /> XML ドキュメントを配置する場合は、理想的には、 *\DesignTime*フォルダーでは XML ドキュメントの参照では引き続き Visual Studio での参照ファイルと一緒に配置します。 XML ドキュメントなどの参照を<em>\References\\[config]\\[arch]\sample.dll</em>なります*\References\\[config]\\[arch]\sample.xml*、そのドキュメントのローカライズ版であり*\References\\[config]\\[arch]\\[locale]\sample.xml*します。 |
| *構成*フォルダー | のみの 3 つのフォルダーがあります。*デバッグ*、*小売*と*CommonConfiguration*します。 SDK の作成者は、の下にファイルを配置できる*CommonConfiguration*かどうか同じ SDK ファイルのセットが使用されることを SDK コンシューマーが対象とする構成に関係なく。 |
| *アーキテクチャ*フォルダー | サポートされている任意*アーキテクチャ*フォルダーが存在することができます。 Visual Studio には、次のアーキテクチャがサポートされています。 x86、x64、ARM、および neutral です。 メモ:Win32 は、x86 にマップされ、AnyCPU がニュートラルにマップされます。<br /><br /> 次の MSBuild のみ*\CommonConfiguration\neutral*プラットフォーム Sdk の場合。 |
| *SDKManifest.xml* | このファイルは、Visual Studio が SDK を使用する方法について説明します。 SDK のマニフェストを見て[!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **表示名:** オブジェクト ブラウザーが、参照リストに表示される値。<br /><br /> **PlatformIdentity:** この属性の存在では、Visual Studio および MSBuild SDK、platform SDK、およびそこから追加された参照をコピーすることはできませんをローカルにように指示します。<br /><br /> **TargetFramework:** この属性は、これの値で指定されている同じフレームワークを対象のプロジェクトのみを確実に Visual Studio によって使用されます属性は、SDK を使用できます。<br /><br /> **MinVSVersion:** この属性は、それに適用する Sdk のみを使用する Visual Studio によって使用されます。<br /><br /> **参照:** この属性は、コントロールを含む参照のみを指定する必要があります。 参照がコントロールを格納するかどうかを指定する方法については、以下を参照してください。 |

##  <a name="ExtensionSDKs"></a> 拡張機能 Sdk  
 次のセクションでは、拡張機能 SDK を展開するために必要がありますについて説明します。  

### <a name="installation"></a>インストール  
 拡張機能 Sdk は、レジストリ キーを指定せず、特定のユーザーまたはすべてのユーザーに対してインストールできます。 すべてのユーザー用の SDK をインストールするには、次のパスを使用します。  

 *% プログラム Files%\Microsoft Sdk\<ターゲット プラットフォーム > \v<platform version number>\ExtensionSDKs*  

 ユーザー固有のインストールでは、次のパスを使用します。  

 *%USERPROFILE%\AppData\Local\Microsoft Sdk\<ターゲット プラットフォーム > \v<platform version number>\ExtensionSDKs*  

 別の場所を使用する場合は、次の 2 つのいずれかを行う必要があります。  

1.  レジストリ キーで指定します。  

     **Hklm \software\microsoft\microsoft Sdk\<ターゲット プラットフォーム > \v<platform version number>\ExtensionSDKs\<SDKName >\<SDKVersion >**\  

     値を持つ (既定値) のサブキーを追加および`<path to SDK><SDKName><SDKVersion>`します。  

2.  MSBuild プロパティを追加`SDKReferenceDirectoryRoot`をプロジェクト ファイル。 このプロパティの値を参照する、拡張 Sdk が存在するディレクトリのセミコロンで区切られたリストです。  

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

1. \\< SDKName\>\\< SDKVersion\>: SDK は、SDK ルートへのパスに対応するフォルダー名から派生する拡張機能のバージョンと名前。 MSBuild では、この id を使用して、ディスク上の SDK を検索し、Visual Studio でこの id が表示されます、**プロパティ**ウィンドウと**参照マネージャー**ダイアログ。  

2. *参照*フォルダー: Api が含まれているバイナリ。 Windows メタデータ (WinMD) ファイルまたはアセンブリを指定できます。  

3. *再頒布可能パッケージ*フォルダー: ファイルをランタイム/デバッグが必要であり、ユーザーのアプリケーションの一部としてパッケージ化する必要があります。 下にあるすべてのバイナリを配置する必要があります*\redist\\< config\>\\< arch\>*、バイナリ名に次の形式に一意性を確保する必要があります: *]* \<会社 >。\<製品 >。\<目的 >。\<拡張機能 ><em>します。たとえば、*Microsoft.Cpp.Build.dll</em>します。 下にあるその他の Sdk (たとえば、javascript、css、pri、xaml、png、jpg ファイル) からファイル名と名前が衝突したを持つすべてのファイルを配置する必要があります<em>\redist\\< config\>\\< arch\> \\< sdkname\> \* XAML に関連付けられているファイルを除くを制御します。これらのファイルを下に配置する必要があります * \redist\\< config\>\\< arch\>\\< componentname\>\\</em>します。  

4. *デザイン時*フォルダー: 前の実行/デバッグのみで必要なファイルは、時間し、ユーザーのアプリケーションの一部としてパッケージ化することはできません。 XML ドキュメント、ライブラリ、ヘッダー、ツールボックスのデザイン時のバイナリ、MSBuild の成果物などを指定できます。 ネイティブ プロジェクトで消費する必要がありますを指定することが想定されている任意の SDK、 *SDKName.props*ファイル。 この種類のファイルのサンプルを次に示します。  

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

    XML のリファレンス ドキュメントは、参照ファイルの横に配置されます。 たとえば、XML の参照ドキュメント、 *\References\\< config\>\\< arch\>\sample.dll*アセンブリが*\References\\< config\>\\< arch\>\sample.xml*でそのドキュメントのローカライズされたバージョンは*\References\\< config\>\\<arch\>\\< ロケール\>\sample.xml*します。  

5. *構成*フォルダー: 3 つのサブフォルダー。*デバッグ*、*小売*、および*CommonConfiguration*します。 SDK の作成者は、の下にファイルを配置できる*CommonConfiguration*と SDK ファイルの同じセットが使用されることを SDK コンシューマーの対象となる構成に関係なく。  

6. *アーキテクチャ*フォルダー: 次のアーキテクチャがサポートされています: x86、x64、ARM、中立です。 Win32 は、x86 にマップされ、AnyCPU がニュートラルにマップされます。  

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
MoreInfo = "https://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  

 次の一覧は、ファイルの要素を示しています。  

1. DisplayName: 参照マネージャー、ソリューション エクスプ ローラー、オブジェクト ブラウザー、および Visual Studio のユーザー インターフェイスの他の場所に表示される値。  

2. ProductFamilyName:全体的な SDK の製品の名前。 たとえば、 [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK の名前は"Microsoft.WinJS.1.0"と"Microsoft.WinJS.2.0"、"Microsoft.WinJS"SDK の製品ファミリの同じファミリに属しています。 この属性は、その接続を作成するには、Visual Studio および MSBuild を使用できます。 この属性が存在しない場合、SDK の名前は、製品ファミリ名として使用されます。  

3. 対応する FrameworkIdentity:使用のアプリのマニフェストにこの属性の値が挿入されて 1 つまたは複数の Windows コンポーネント ライブラリの依存関係を指定します。 この属性は、Windows コンポーネント ライブラリにのみ適用されます。  

4. TargetFramework:参照マネージャーと、ツールボックスで使用できる Sdk を指定します。 これは、ターゲット フレームワークのモニカーのセミコロン区切りのリストなど".NET Framework、バージョン = v2.0; .NET Framework、バージョン = v4.5.1"。 同じターゲット フレームワークのいくつかのバージョンが指定されている場合、参照マネージャーは、フィルタ リングするための指定された最低バージョンを使用します。 たとえば場合、".NET Framework、バージョン = v2.0; .NET Framework、バージョン = v4.5.1"参照マネージャーを使用して、指定".NET Framework、バージョン = v2.0"。 特定のターゲット フレームワーク プロファイルが指定されている場合のみそのプロファイルが使用されます参照マネージャーによってフィルタ リングするためです。 たとえば、"Silverlight、バージョン = v4.0、プロファイル WindowsPhone ="が指定されている参照マネージャーは、Windows Phone プロファイルのみに基づくフィルター処理完全な Silverlight 4.0 Framework をターゲットとするプロジェクトでは、SDK 参照マネージャーでは表示されません。  

5. MinVSVersion:Visual Studio の最小バージョン。  

6. MaxPlatformVerson:最大のターゲット プラットフォームのバージョンはプラットフォームのバージョンに対して、拡張機能 SDK を使うことはできませんを指定するためにする必要があります。 たとえば、Windows 8 のプロジェクトでのみ Microsoft Visual C ランタイム パッケージ v11.0 を参照する必要があります。 したがって、Windows 8 プロジェクトの MaxPlatformVersion は 8.0 です。 つまり、Windows 8.1 プロジェクトの場合、参照マネージャーが Microsoft Visual C ランタイム パッケージをフィルター処理、MSBuild は、エラーをスローします。 ときに、[!INCLUDE[win81](../debugger/includes/win81_md.md)]プロジェクトでは、それを参照します。 注: この要素は、以降でサポート[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]します。  

7. AppliesTo:適用可能な Visual Studio プロジェクトの種類を指定することで、参照マネージャーで使用できる Sdk を指定します。 9 個の値が認識されます。WindowsAppContainer、Visualc++、VB、CSharp、WindowsXAML、JavaScript、管理、およびネイティブです。 SDK の作成者が使用でき、("+')、または ("&#124;") ではなく、("!")演算子を正確に、SDK に適用されるプロジェクトの種類のスコープを指定します。  

    WindowsAppContainer 識別用のプロジェクト[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]アプリ。  

8. SupportPrefer32Bit:サポートされる値は"True"および"False"。 既定では"True です"。 MSBuild エラーが返されます、値が"False"に設定されている場合[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]プロジェクト (またはデスクトップ プロジェクトの場合の警告)、SDK を参照するプロジェクトがある Prefer32Bit が有効になっている場合。 Prefer32Bit の詳細については、次を参照してください。[ビルド ページで、プロジェクト デザイナー (c#)](../ide/reference/build-page-project-designer-csharp.md)または[コンパイル ページで、プロジェクト デザイナー (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)します。  

9. SupportedArchitectures:セミコロン区切りの SDK は、サポートされるアーキテクチャのリスト。 MSBuild では、使用中のプロジェクトで対象となる SDK のアーキテクチャがサポートされていない場合に警告が表示されます。 この属性が指定されていない場合 MSBuild にはこの種類の警告が表示されません。  

10. SupportsMultipleVersions:この属性設定されている場合**エラー**または**警告**MSBuild では、同じプロジェクトが同じ SDK ファミリの複数のバージョンを参照できないことを示します。 この属性が存在しないかに設定されている場合**許可**MSBuild は、この種類のエラーまたは警告を表示しません。  

11. AppX:ディスク上の Windows コンポーネント ライブラリ用のアプリ パッケージへのパスを指定します。 この値は、ローカル デバッグ中に、Windows コンポーネント ライブラリの登録コンポーネントに渡されます。 ファイル名の名前付け規則は*\<会社 >.\<製品 >。\<アーキテクチャ >。\<Configuration >。\<バージョン > .appx*します。 Windows コンポーネント ライブラリには適用されない場合の構成とアーキテクチャには、属性名および属性値の省略可能です。 この値は、Windows コンポーネント ライブラリにのみ適用されます。  

12. CopyRedistToSubDirectory:場所を指定します、ファイルの下、 *\redist*アプリ パッケージのルート フォルダーをコピーする必要があります (つまり、**パッケージの場所**でを選択して、**アプリ パッケージの作成**ウィザード) とランタイムのレイアウト ルート。 既定の場所は、アプリ パッケージのルートと**F5**レイアウト。  

13. DependsOn:この SDK が依存する Sdk を定義する SDK の id の一覧。 この属性は、参照マネージャーの詳細ウィンドウに表示されます。  

14. 詳細情報:ヘルプと詳細情報を提供する web ページの URL。 この値は、右側のウィンドウ参照マネージャーの詳細情報のリンクで使用されます。  

15. 登録の種類:WinMD 登録をアプリ マニフェストで指定して、DLL の対応する実装がありますが、ネイティブ winmd 必要です。  

16. ファイル参照。または、コントロールを含む、ネイティブ Winmd を参照のみを指定します。 参照がコントロールを格納するかどうかを指定する方法については、次を参照してください。[ツールボックス アイテムの場所を指定](#ToolboxItems)以下。  

##  <a name="ToolboxItems"></a> ツールボックス アイテムの場所を指定します。  
 ToolBoxItems 要素、 *SDKManifest.xml*スキーマの両方のプラットフォームと拡張機能 Sdk カテゴリとツールボックス項目の場所を指定します。 次の例では、別の場所を指定する方法を示します。 これは、WinMD または DLL のいずれかの参照に適用されます。  

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
 [チュートリアル: C++ を使用して、SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [チュートリアル: C# または Visual Basic を使用して、SDK を作成します。](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)