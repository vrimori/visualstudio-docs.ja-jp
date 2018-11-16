---
title: プロジェクトの C++ デバッグ構成の設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404bbc753b2729ad5ec7625fa01803b8a6bdf5c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800797"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ デバッグ構成のプロジェクト設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C または C++ デバッグ構成でのプロジェクトの設定を変更することができます、**プロパティ ページ** ダイアログ ボックスで説明したよう[方法: デバッグ設定とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)します。 次の表は、デバッガー関連の設定を検索する場所を示して、**プロパティ ページ** ダイアログ ボックス。  
  
> [!WARNING]
>  デバッグ プロジェクト設定、**構成プロパティ/デバッグ**Windows ストア アプリおよび C++ で記述されたコンポーネントのカテゴリは異なります。 参照してください[(VB、c#、C++ および XAML) は、デバッグ セッションを開始](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)Windows デベロッパー センターでします。  
  
 使用するデバッガーを指定、**起動するデバッガー**ボックスの一覧。 選択したデバッガーによって、表示されるプロパティが異なります。  
  
 各デバッグ プロパティ設定は自動的に作成され、ソリューションを保存するたびに、ソリューションの "ユーザー単位の" ファイル (.vcxproj.user) に保存されます。  
  
### <a name="configuration-properties-folder-debugging-category"></a>[構成プロパティ] フォルダー ([デバッグ] カテゴリ)  
  
|**設定**|**説明**|  
|-----------------|---------------------|  
|**起動するデバッガー**|実行するデバッガーを指定します。次の中から選択します。<br /><br /> -   **ローカル Windows デバッガー**<br />-   **リモート Windows デバッガー**<br />-   **Web ブラウザー デバッガー**<br />-   **Web Service デバッガー**|  
|**コマンド**(ローカル Windows デバッガー)|ローカル コンピューターでデバッグするプログラムを起動するコマンドを指定します。|  
|**リモート コマンド**(リモート Windows デバッガー)|リモート コンピューター上の .exe のパスを指定します。 リモート コンピューターでパスを入力するようにパスを入力します。|  
|**コマンド引数**(ローカル Windows デバッガーおよびリモート Windows デバッガー)|-指定したコマンドの引数を指定します。<br /><br /> このボックスでは、次のリダイレクト演算子を使用できます。<br /><br /> < `file`<br /> 標準入力を file から読み取ります。<br /><br /> > `file`<br /> 標準出力を file に書き込みます。<br /><br /> >> `file`<br /> 標準出力を file に追加します。<br /><br /> 2> `file`<br /> 標準エラー出力を file に書き込みます。<br /><br /> 2>> `file`<br /> 標準エラー出力を file に追加します。<br /><br /> 2> &1<br /> 標準エラー出力 (2) を標準出力 (1) と同じ位置に出力します。<br /><br /> 1> &2<br /> 標準出力 (1) を標準エラー出力 (2) と同じ位置に出力します。<br /><br /> ほとんどの場合、これらの演算子はコンソール アプリケーションでのみ有効です。|  
|**作業ディレクトリ**|デバッグするプログラムの作業ディレクトリを、EXE ファイルがあるプロジェクト ディレクトリを基準とした相対パスで指定します。 この設定を空白のままにした場合、作業ディレクトリはプロジェクト ディレクトリになります。 リモート デバッグの場合、プロジェクト ディレクトリはリモート サーバーにあります。|  
|**アタッチ**(ローカル Windows デバッガーおよびリモート Windows デバッガー)|アプリケーションを起動するか、またはアプリケーションにアタッチするかを指定します。 既定の設定は [いいえ] です。|  
|**リモート サーバー名**(リモート Windows デバッガー)|アプリケーションをデバッグするコンピューター (自分のコンピューター以外) の名前を指定します。<br /><br /> このプロパティの値に設定されている RemoteMachine ビルド マクロ詳細については、次を参照してください。[ビルドのコマンドとプロパティのマクロの](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)します。|  
|**接続**(リモート Windows デバッガー)|リモート デバッグ用の接続の種類を、標準の接続と認証を使用しない接続の間で切り替えます。 リモート コンピューター名を指定、**リモート サーバー名**ボックス。 接続の種類には、次のようなものがあります。<br /><br /> -   **Windows 認証でリモート接続**<br />-   **認証なし (ネイティブのみ) でリモート接続します。**<br /><br /> **注**認証なしでのリモート デバッグしまう可能性があります、リモート コンピューターのセキュリティ違反に対する脆弱性。 Windows 認証モードの方がより安全です。<br /><br /> 詳細については、次を参照してください。[リモート デバッグのセットアップ](../debugger/remote-debugging.md)します。|  
|**HTTP URL** (Web Service デバッガーと Web ブラウザー デバッガー)|デバッグするプロジェクトが存在する URL を指定します。|  
|**[デバッガーのタイプ]**|使用するデバッガーの種類を指定します:**ネイティブのみ**、**マネージのみ**、 **GPU のみ**、 **Mixed**、**自動**(既定)、または**スクリプト**します。<br /><br /> -   **ネイティブのみ**アンマネージの C++ コードです。<br />-   **マネージのみ**は共通言語ランタイム (マネージ コード) で実行されるコード。<br />-   **混合**マネージおよびアンマネージ コードでデバッガーを起動します。<br />-   **自動**コンパイラと EXE の情報に基づいてデバッガーの種類を決定します。<br />-   **スクリプト**スクリプトのデバッガーを起動します。<br />-   **GPU のみ**は、GPU デバイスまたは DirectX リファレンス ラスタライザーをで実行される C++ AMP コード。 参照してください[GPU コードのデバッグ](../debugger/debugging-gpu-code.md)します。|  
|**環境**(ローカル Windows デバッガー)|デバッグするプログラムの環境変数を指定します。 標準的な環境変数の構文を使用して (たとえば、 `PATH="%SystemRoot%\..."`)。 これらの変数、システム環境をオーバーライドするかに応じて、システム環境にマージは、**マージ環境**設定します。 設定列内でクリックすると、"... の編集" が表示されます。 そのリンクをクリックして、環境変数を編集します。|  
|**マージ環境**(ローカル Windows デバッガー)|かどうか、変数がで指定された、**環境**ボックスは、オペレーティング システムで定義されている環境と統合されます。 既定の設定は [はい] です。|  
|**SQL デバッグ**(MPI クラスター デバッガー) を除くすべて|SQL プロシージャのデバッグを [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] アプリケーションから有効にします。 既定の設定は [いいえ] です。|  
|**デバッグ アクセラレータの種類**(GPU デバッグの場合のみ)|デバッグに使用する GPU デバイスを指定します。 互換性のある GPU デバイス用のデバイス ドライバーをインストールするとその他のオプションが追加されます。 既定の設定は [GPU - ソフトウェア エミュレーター] です。|  
|**GPU 既定のブレークポイントの動作**(GPU デバッグの場合のみ)|ブレークポイント イベントを SIMD ワープの各スレッドごとに発生させるかどうかを指定します。 既定の設定では、1 ワープごとに 1 回、ブレークポイント イベントが発生します。|  
|**Amp の既定のアクセラレータ**(GPU デバッグの場合のみ)|GPU コードをデバッグする際、既定の AMP のアクセラレータを指定します。 選択**WARP ソフトウェア アクセラレータ**ハードウェアまたはコードではなく、ドライバーによって問題の原因がどうかを調査します。|  
|**配置ディレクトリ**(リモート Windows デバッガー)|起動前にプロジェクト出力がコピーされるリモート コンピューター上のパスを指定します。 このパスとして、リモート コンピューター上のネットワーク共有、またはリモート コンピューター上のフォルダーへのパスを指定できます。 既定の設定は空で、プロジェクト出力はネットワーク共有にコピーされます。 ファイルの展開を有効にする必要がありますも選択する、**デプロイ**Configuration Manager ダイアログ ボックスのチェック ボックス。 詳細については、「[How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md)」(方法 : 構成を作成および編集する) を参照してください。|  
|**配置する追加ファイル**(リモート Windows デバッガー)|配置ディレクトリのプロパティを設定している場合、配置ディレクトリにコピーする追加ファイルのセミコロン区切りのリストを指定します。 既定の設定は空で、配置ディレクトリにコピーされる追加ファイルはありません。 ファイルの展開を有効にする必要がありますも選択する、**デプロイ**Configuration Manager ダイアログ ボックスのチェック ボックス。 詳細については、「[How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md)」(方法 : 構成を作成および編集する) を参照してください。|  
|**Visual C デバッグ ランタイム ライブラリの配置**(リモート Windows デバッガー)|配置ディレクトリのプロパティを設定している場合、現在のプラットフォーム用の Visual C++ デバッグ ランタイム ライブラリをネットワーク共有にコピーする必要があるかどうかを指定します。 既定の設定は [はい] です。|  
  
### <a name="cc-folder-general-category"></a>C/C++ フォルダー ([全般] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**デバッグ情報の形式**([/Z7、/zi、/ZI](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|プロジェクトに作成するデバッグ情報の種類を指定します。<br /><br /> 既定のオプション (/ZI) では、プログラム データベース (PDB) がエディット コンティニュ互換形式で作成されます。 詳細については、次を参照してください。 [/Z7、/Zd、/Zi、/ZI (デバッグ情報の形式)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)します。|  
  
### <a name="cc-folder-optimization-category"></a>[C/C++] フォルダー ([最適化] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**Optimization**|コンパイラが生成したコードを最適化するかどうかを指定します。 最適化すると、実行されるコードが変更されます。 最適化したコードはソース コードと一致しなくなります。 したがって、デバッグは困難です。<br /><br /> 既定のオプション (**無効 (/0 d**) の最適化を抑制します。 最適化を行わずにコードを開発し、実行環境用のコードを作成するときに最適化をオンにできます。|  
  
### <a name="linker-folder-debugging-category"></a>[リンカー] フォルダー ([デバッグ] カテゴリ)  
  
|設定|説明|  
|-------------|-----------------|  
|**デバッグ情報の生成**([/debug](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|デバッグ情報を含めるようにリンカーに指示します。デバッグ情報の形式は、/Z7、/Zd、Zi、または /ZI で指定されます。|  
|**プログラム データベース ファイルの生成**([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|PDB ファイルの名前を指定します。 [デバッグ情報の形式] で ZI または /Zi を選択する必要があります。|  
|**プライベート シンボルの除去**([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|PDB ファイルのプライベート シンボルを含めない場合は、このボックスに PDB ファイルの名前を指定します。 PDB ファイルを生成するいずれかのコンパイラ オプションまたはリンカー オプションを使ってプログラム イメージをビルドするときにこのオプションを指定すると、2 番目のプログラム データベース (PDB) ファイルが作成されます (コンパイラ オプションまたはリンカー オプションの例: /DEBUG、/Z7、/Zd、 /Zi など)。 2 番目の PDB ファイルでは、顧客に提供しないシンボルが省かれています。 詳細については、「[/PDBSTRIPPED (プライベート シンボルの除去)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55)」を参照してください。|  
|**マップ ファイルを生成**([/map](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|リンク中にマップ ファイルを生成するようにリンカーに指示します。 既定の設定は [いいえ] です。 詳細については、「[/MAP (マップ ファイルの生成)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)」を参照してください。|  
|**マップ ファイル名**([/map:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*名前*)|[マップ ファイルの作成] を選択する場合は、このボックスにマップ ファイルを指定できます。 詳細については、「[/MAP (マップ ファイルの生成)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)」を参照してください。|  
|**マップ ファイルのエクスポート**([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|エクスポートされた関数をマップ ファイルに含めます。 既定の設定は [いいえ] です。 詳細については、次を参照してください。 [/MAPINFO (マップ ファイルに含める情報)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b)します。|  
|**デバッグできるアセンブリ**([/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|リンカーの /ASSEMBLYDEBUG オプションの設定を指定します。 次の値を指定できます。<br /><br /> -   **デバッグできる属性が作成しない**します。<br />-   **ランタイム トラッキングおよび最適化の無効 (/ASSEMBLYDEBUG)** します。 これが既定の設定です。<br />-   **なしのランタイム トラッキングおよび有効にする optimizations(/ASSEMBLYDEBUG:DISABLE)** します。<br />-   **\<親またはプロジェクトの既定値から継承 >** します。<br />詳細については、次を参照してください。 [/ASSEMBLYDEBUG (DebuggableAttribute の追加)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)します。|  
  
 [構成プロパティ] フォルダー ([デバッグ] カテゴリ) 内のこれらの設定は、Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings インターフェイスを使用してプログラムで変更できます。 詳細については、「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings> 」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [Visual C++ プロジェクトの作成および管理](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ASSEMBLYDEBUG (DebuggableAttribute の追加)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [ビルドのコマンドとプロパティの共通マクロ](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



