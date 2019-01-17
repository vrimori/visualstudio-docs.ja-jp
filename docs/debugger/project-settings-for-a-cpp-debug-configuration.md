---
title: C++ のデバッグ構成のプロジェクト設定
ms.custom: seodec18
ms.date: 11/26/2018
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 4351553d5df55dd5dceeffe542ff542a9487d6e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957911"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ デバッグ構成のプロジェクト設定
C または C++ デバッグ構成でのプロジェクトの設定を変更することができます、**プロパティ ページ** ダイアログ ボックスで説明したよう[方法。デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md). 次の表は、**[プロパティ ページ]** ダイアログ ボックスのデバッガー関連の設定の場所を示しています。  
  
> [!NOTE]
>  デバッグ プロジェクト設定、**構成プロパティ/デバッグ**カテゴリは UWP アプリ、C++ で記述されたコンポーネントは異なります。 参照してください[(VB、c#、C++ および XAML) は、デバッグ セッションを開始](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)します。  
  
 各デバッグ プロパティ設定が自動的に書き込まれ、「ユーザーごと」のファイルに保存 (. vcxproj.user) ソリューションを保存するときに、ソリューション。  

 使用するデバッガーを指定、**起動するデバッガー**リスト ボックスで、次の表で説明します。 選択したデバッガーによって、表示されるプロパティが異なります。  
    
## <a name="configuration-properties-folder-debugging-category"></a>[構成プロパティ] フォルダー ([デバッグ] カテゴリ)  
  
| **設定** | **説明** |
| - | - |
| **[起動するデバッガー]** | 実行するデバッガーを指定します。次の中から選択します。<br /><br /> -   **ローカル Windows デバッガー**<br />-   **リモート Windows デバッガー**<br />-   **Web ブラウザー デバッガー**<br />-   **Web Service デバッガー** |
| **[コマンド]** (ローカル Windows デバッガー) | ローカル コンピューターでデバッグするプログラムを起動するコマンドを指定します。 |
| **[リモート コマンド]** (リモート Windows デバッガー) | リモート コンピューター上の .exe のパスを指定します。 リモート コンピューターでパスを入力するようにパスを入力します。 |
| **コマンド引数**(ローカル Windows デバッガー)<br /><br /> **リモート コマンド引数**(リモート Windows デバッガー) | - 上で指定したコマンドの引数を指定します。<br /><br /> このボックスでは、次のリダイレクト演算子を使用できます。<br /><br /> < `file`<br /> 標準入力を file から読み取ります。<br /><br /> > `file`<br /> 標準出力を file に書き込みます。<br /><br /> >> `file`<br /> 標準出力を file に追加します。<br /><br /> 2> `file`<br /> 標準エラー出力を file に書き込みます。<br /><br /> 2>> `file`<br /> 標準エラー出力を file に追加します。<br /><br /> 2> &1<br /> 標準エラー出力 (2) を標準出力 (1) と同じ位置に出力します。<br /><br /> 1> &2<br /> 標準出力 (1) を標準エラー出力 (2) と同じ位置に出力します。<br /><br /> ほとんどの場合、これらの演算子はコンソール アプリケーションでのみ有効です。 |
| **作業ディレクトリ** | デバッグするプログラムの作業ディレクトリを、EXE ファイルがあるプロジェクト ディレクトリを基準とした相対パスで指定します。 この設定を空白のままにした場合、作業ディレクトリはプロジェクト ディレクトリになります。 リモート デバッグなど、プロジェクト ディレクトリは、リモート サーバー上です。 |
| **[アタッチ]** (ローカル Windows デバッガーとリモート Windows デバッガー) | アプリケーションを起動するか、またはアプリケーションにアタッチするかを指定します。 既定の設定は [いいえ] です。 |
| **[リモート サーバー名]** (リモート Windows デバッガー) | アプリケーションをデバッグするコンピューター (自分のコンピューター以外) の名前を指定します。<br /><br /> RemoteMachine ビルド マクロには、このプロパティの値を設定します。詳細については、[ビルドのコマンドとプロパティのマクロ](/cpp/ide/common-macros-for-build-commands-and-properties)に関するページを参照してください。 |
| **[接続]** (リモート Windows デバッガー) | リモート デバッグ用の接続の種類を、標準の接続と認証を使用しない接続の間で切り替えます。 **[リモート サーバー名]** ボックスでリモート コンピューター名を指定します。 接続の種類には、次のようなものがあります。<br /><br /> -   **Windows 認証でリモート接続する**<br />-   **認証なしでリモート接続する**<br /><br /> **メモ** 認証を使用しないリモート デバッグを行うと、セキュリティ違反に対してリモート コンピューターが脆弱になる可能性があります。 Windows 認証モードの方がより安全です。<br /><br /> 詳細については、「[Remote debugging setup](../debugger/remote-debugging.md)」 (リモート デバッグの設定) を参照してください。 |
| **[HTTP URL]** (Web Service デバッガーと Web ブラウザー デバッガー) | デバッグするプロジェクトが存在する URL を指定します。 |
| **[デバッガーのタイプ]** | 使用するデバッガーの種類を指定します。**ネイティブのみ**、**マネージのみ**、 **GPU のみ**、 **Mixed**、**自動**(既定)、または**スクリプト**.<br /><br /> -   **[ネイティブのみ]** は、アンマネージ C++ コードに使用します。<br />-   **[マネージドのみ]** は、共通言語ランタイムで実行されるコード (マネージド コード) に使用します。<br />-   **[混合]** を選択すると、マネージド コードとアンマネージド コードのデバッガーが起動します。<br />-   **[自動]** を選択すると、コンパイラと EXE の情報に基づいてデバッガーの種類が決まります。<br />-   **[スクリプト]** を選択すると、スクリプトのデバッガーが起動します。<br />-   **[GPU のみ]** は、GPU デバイスまたは DirectX リファレンス ラスターライザーで実行される C++ AMP コードに使用します。 参照してください[デバッグ GPU コード](../debugger/debugging-gpu-code.md)します。 |
| **環境**(ローカル Windows デバッガーおよびリモート Windows デバッガー) | デバッグするプログラムの環境変数を指定します。 標準的な環境変数の構文を使用して (たとえば、 `PATH="%SystemRoot%\..."`)。 各変数は、**[マージ環境]** の設定に応じて、システム環境をオーバーライドするか、システム環境にマージされます。 [設定] 列をクリックすると、「…」が表示されます。 環境変数を編集するには、そのリンクを選択します。 |
| **[マージ環境]** (ローカル Windows デバッガー) | **[環境]** ボックスで指定した変数を、オペレーティング システムによって定義されている環境にマージするかどうかを決定します。 既定の設定は [はい] です。 |
| **[SQL デバッグ]** (MPI クラスター デバッガーを除くすべて) | SQL プロシージャのデバッグを [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] アプリケーションから有効にします。 既定の設定は [いいえ] です。 |
| **[デバッグ アクセラレータの種類]** (GPU デバッグのみ) | デバッグに使用する GPU デバイスを指定します。 互換性のある GPU デバイス用のデバイス ドライバーをインストールするとその他のオプションが追加されます。 既定の設定は **[GPU - ソフトウェア エミュレーター]** です。 |
| **[GPU 既定のブレークポイントの動作]** (GPU デバッグのみ) | ブレークポイント イベントを SIMD ワープの各スレッドごとに発生させるかどうかを指定します。 既定の設定では、1 ワープごとに 1 回、ブレークポイント イベントが発生します。 |
| **[AMP の既定のアクセラレータ]** | GPU コードをデバッグする際、既定の AMP のアクセラレータを指定します。 問題の原因がコードではなく、ハードウェアやドライバーにあるかどうかを調査するには、**[WARP ソフトウェアのアクセラレータ]** を選択します。 |
| **[配置ディレクトリ]** (リモート Windows デバッガー) | 起動前にプロジェクト出力がコピーされるリモート コンピューター上のパスを指定します。 このパスとして、リモート コンピューター上のネットワーク共有、またはリモート コンピューター上のフォルダーへのパスを指定できます。 既定の設定は空で、プロジェクト出力はネットワーク共有にコピーされます。 ファイルの配置を有効にするには、[構成マネージャー] ダイアログ ボックスで **[配置]** チェック ボックスをオンにする必要もあります。 詳細については、「[方法 :構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。 |
| **[配置する追加ファイル]** (リモート Windows デバッガー) | 配置ディレクトリのプロパティが設定されている場合、配置ディレクトリにコピーする追加ファイルのセミコロン区切りのリストになります。 既定の設定は空で、配置ディレクトリにコピーされる追加ファイルはありません。 ファイルの配置を有効にするには、[構成マネージャー] ダイアログ ボックスで **[配置]** チェック ボックスをオンにする必要もあります。 詳細については、「[方法 :構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。 |
| **[Visual C++ デバッグ ランタイム ライブラリの配置]** (リモート Windows デバッガー) | 配置ディレクトリのプロパティを設定している場合、現在のプラットフォーム用の Visual C++ デバッグ ランタイム ライブラリをネットワーク共有にコピーする必要があるかどうかを指定します。 既定の設定は [はい] です。 |
  
## <a name="cc-folder-general-category"></a>C/C++ フォルダー ([全般] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**[デバッグ情報の形式]** ([/Z7、/Zd、Zi、/ZI](/cpp/build/reference/z7-zi-zi-debug-information-format))|プロジェクトに作成するデバッグ情報の種類を指定します。<br /><br /> 既定のオプション (/ZI) では、プログラム データベース (PDB) がエディット コンティニュ互換形式で作成されます。 詳細については、[/Z7、/Zd、/Zi、/ZI (デバッグ情報の形式)](/cpp/build/reference/z7-zi-zi-debug-information-format) に関するページを参照してください。|  
  
## <a name="cc-folder-optimization-category"></a>[C/C++] フォルダー ([最適化] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**Optimization**|コンパイラが生成したコードを最適化するかどうかを指定します。 最適化すると、実行されるコードが変更されます。 最適化されたコードには、これにより、デバッグをより困難なソース コードと一致しません。<br /><br /> 既定のオプション (**[無効 (/0d)]**) では、最適化は行われません。 最適化を行わずにコードを開発し、実行環境用のコードを作成するときに最適化をオンにできます。|  
  
## <a name="linker-folder-debugging-category"></a>[リンカー] フォルダー ([デバッグ] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**[デバッグ情報を作成]** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|デバッグ情報を含めるようにリンカーに指示します。デバッグ情報の形式は、[/Z7、/Zd、Zi、または /ZI](/cpp/build/reference/z7-zi-zi-debug-information-format) で指定されます。|  
|**[プログラム データベース ファイルの生成]** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|このボックスで、プログラム データベース (PDB) ファイルの名前を指定します。 [デバッグ情報の形式] で ZI または /Zi を選択する必要があります。|  
|**[プライベート シンボルの削除]** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB ファイルのプライベート シンボルを含めない場合は、このボックスに PDB ファイルの名前を指定します。 このオプションでは、/DEBUG、/Z7、/Zd などの PDB ファイルを生成するオプションのコンパイラやリンカーと、プログラム イメージをビルドするときに、2 番目の PDB ファイルが作成されます。 /Zi など)。 2 番目の PDB ファイルでは、顧客に提供しないシンボルが省かれています。 詳細については、「[/PDBSTRIPPED (プライベート シンボルの除去)](/cpp/build/reference/pdbstripped-strip-private-symbols)」を参照してください。|  
|**[マップ ファイルの作成]** ([/MAP](/cpp/build/reference/map-generate-mapfile))|リンク中にマップ ファイルを生成するようにリンカーに指示します。 既定の設定は [いいえ] です。 詳細については、「[/MAP (マップ ファイルの生成)](/cpp/build/reference/map-generate-mapfile)」を参照してください。|  
|**マップ ファイル名**([/map:](/cpp/build/reference/map-generate-mapfile)*名前*)|[マップ ファイルの作成] を選択する場合は、このボックスにマップ ファイルを指定できます。 詳細については、「[/MAP (マップ ファイルの生成)](/cpp/build/reference/map-generate-mapfile)」を参照してください。|  
|**[マップファイルのエクスポート]** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|エクスポートされた関数をマップ ファイルに含めます。 既定の設定は [いいえ] です。 詳細については、次を参照してください。 [/MAPINFO (マップ ファイルに含める情報)](/cpp/build/reference/mapinfo-include-information-in-mapfile)します。|  
|**[デバッグできるアセンブリ]** ([/ASSEMBLYDEBUG](/cpp/build/reference/mapinfo-include-information-in-mapfile))|リンカーの /ASSEMBLYDEBUG オプションの設定を指定します。 指定できる値は次のとおりです。<br /><br /> -   **[デバッグできる属性が作成されませんでした]**。<br />-   **[ランタイム トラッキングおよび最適化の無効 (/ASSEMBLYDEBUG)]**。 これが既定の設定です。<br />-   **[ランタイム トラッキングおよび最適化の有効を無効にする (/ASSEMBLYDEBUG:DISABLE)]**。<br />-   **[\<親またはプロジェクトの既定値から継承>]**。<br />詳細については、「[/ASSEMBLYDEBUG (DebuggableAttribute の追加)](/cpp/build/reference/assemblydebug-add-debuggableattribute)」を参照してください。|  
  
 [構成プロパティ] フォルダー ([デバッグ] カテゴリ) 内のこれらの設定は、Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings インターフェイスを使用してプログラムで変更できます。 詳細については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>」を参照してください。

## <a name="other-project-settings"></a>他のプロジェクト設定

Visual Studio プロジェクトは、スタティック ライブラリと Dll などのプロジェクトの種類をデバッグするには、正しいファイルを検索できる必要があります。 ソース コードが利用できる場合は、デバッグが簡単にする、同じソリューションを個別のプロジェクトでスタティック ライブラリと Dll を追加できます。 このプロジェクトの種類を作成する方法の詳細については、次を参照してください。[の作成とダイナミック リンク ライブラリ (DLL) を使用して](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)と[スタティック ライブラリを使用して、作成する](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp)します。 使用可能なソース コードを作成することできますも新しい Visual Studio プロジェクトを選択して**ファイル** > **新規** > **既存コードからプロジェクト**します。

外部プロジェクトにある Dll をデバッグするを参照してください。 [DLL のデバッグ プロジェクト](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal)します。 DLL プロジェクトのデバッグがない呼び出し元のアプリケーションのプロジェクトにアクセスを参照して必要な場合[DLL プロジェクトからデバッグする方法について](../debugger/how-to-debug-from-a-dll-project.md)します。
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [Visual C プロジェクト作成および管理](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ASSEMBLYDEBUG (DebuggableAttribute の追加)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [ビルドのコマンドとプロパティの共通マクロ](/cpp/ide/common-macros-for-build-commands-and-properties)