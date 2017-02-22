---
title: "C++ デバッグ構成のプロジェクト設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".pdb ファイル, デバッグ ビルドのプロジェクト設定"
  - "/DEBUG リンカー オプション"
  - "/MAP リンカー オプション"
  - "/MAPINFO リンカー オプション"
  - "/PDB リンカー オプション"
  - "/PDBSTRIPPED リンカー オプション"
  - "/Z7 コンパイラ オプション [C++]"
  - "/Zd コンパイラ オプション [C++]"
  - "/ZI コンパイラ オプション [C++]"
  - "デバッグ ビルド, プロジェクト設定"
  - "デバッグ構成, C++"
  - "DEBUG リンカー オプション"
  - "-DEBUG リンカー オプション"
  - "デバッグ [C++], デバッガー設定"
  - "MAP リンカー オプション"
  - "-MAP リンカー オプション"
  - "マップ ファイル, プロジェクト設定"
  - "MAPINFO リンカー オプション"
  - "-MAPINFO リンカー オプション"
  - "pdb ファイル, デバッグ ビルドのプロジェクト設定"
  - "PDB リンカー オプション"
  - "-PDB リンカー オプション"
  - "PDBSTRIPPED リンカー オプション"
  - "-PDBSTRIPPED リンカー オプション"
  - "プロジェクト構成, デバッグ"
  - "プロジェクト設定 [Visual Studio]"
  - "プロジェクト設定 [Visual Studio], デバッグ構成"
  - "プロジェクト [Visual Studio], デバッグ構成"
  - "Z7 コンパイラ オプション [C++]"
  - "-Z7 コンパイラ オプション [C++]"
  - "Zd コンパイラ オプション [C++]"
  - "-Zd コンパイラ オプション [C++]"
  - "ZI コンパイラ オプション [C++]"
  - "-Zl コンパイラ オプション [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C++ デバッグ構成のプロジェクト設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「[方法 : デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md)」で説明したように、C または Visual C\+\+ デバッグ構成のプロジェクト設定は **\[プロパティ ページ\]** ダイアログ ボックスで変更できます。  次の表は、**\[プロパティ ページ\]** ダイアログ ボックスのデバッガー関連の設定の場所を示しています。  
  
> [!WARNING]
>  C\+\+ で記述されている Windows ストア アプリおよびコンポーネントの **\[構成プロパティ\]\/\[デバッグ\]** カテゴリのデバッグ プロジェクト設定は異なります。  Windows デベロッパー センターで「[デバッグ セッションの開始 \(VB、C\#、C\+\+、および XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)」を参照してください。  
  
 使用するデバッガーは **\[起動するデバッガー\]** ボックスで指定します。  選択したデバッガーによって、表示されるプロパティが異なります。  
  
 各デバッグ プロパティ設定は自動的に作成され、ソリューションを保存するたびに、ソリューションの "ユーザー単位の" ファイル \(.vcxproj.user\) に保存されます。  
  
### \[構成プロパティ\] フォルダー \(\[デバッグ\] カテゴリ\)  
  
|**設定値**|**説明**|  
|-------------|------------|  
|**\[起動するデバッガー\]**|実行するデバッガーを指定します。次の中から選択します。<br /><br /> -   **\[ローカル Windows デバッガー\]**<br />-   **\[リモート Windows デバッガー\]**<br />-   **\[Web ブラウザー デバッガー\]**<br />-   **\[Web Service デバッガー\]**|  
|**\[コマンド\]** \(\[ローカル Windows デバッガー\] の場合\)|ローカル コンピューターでデバッグするプログラムを起動するコマンドを指定します。|  
|**\[リモート コマンド\]** \(\[リモート Windows デバッガー\] の場合\)|リモート コンピューター上の .exe のパスを指定します。  リモート コンピューターでパスを入力するようにパスを入力します。|  
|**\[コマンド引数\]** \(\[ローカル Windows デバッガー\] と \[リモート Windows デバッガー\] の場合\)|-   上で指定したコマンドの引数を指定します。<br /><br /> このボックスでは、次のリダイレクト演算子を使用できます。<br /><br /> \< `file`<br /> 標準入力を file から読み取ります。<br /><br /> \> `file`<br /> 標準出力を file に書き込みます。<br /><br /> \>\> `file`<br /> 標準出力を file に追加します。<br /><br /> 2\> `file`<br /> 標準エラー出力を file に書き込みます。<br /><br /> 2\>\> `file`<br /> 標準エラー出力を file に追加します。<br /><br /> 2\> &1<br /> 標準エラー出力 \(2\) を標準出力 \(1\) と同じ位置に出力します。<br /><br /> 1\> &2<br /> 標準出力 \(1\) を標準エラー出力 \(2\) と同じ位置に出力します。<br /><br /> ほとんどの場合、これらの演算子はコンソール アプリケーションでのみ有効です。|  
|**\[作業ディレクトリ\]**|デバッグするプログラムの作業ディレクトリを、EXE ファイルがあるプロジェクト ディレクトリを基準とした相対パスで指定します。  この設定を空白のままにした場合、作業ディレクトリはプロジェクト ディレクトリになります。  リモート デバッグの場合、プロジェクト ディレクトリはリモート サーバーにあります。|  
|**\[アタッチ\]** \(\[ローカル Windows デバッガー\] と \[リモート Windows デバッガー\] の場合\)|アプリケーションを起動するか、またはアプリケーションにアタッチするかを指定します。  既定の設定は \[いいえ\] です。|  
|**\[リモート サーバー名\]** \(リモート Windows デバッガーの場合\)|アプリケーションをデバッグするコンピューター \(自分のコンピューター以外\) の名前を指定します。<br /><br /> RemoteMachine ビルド マクロには、このプロパティの値を設定します。詳細については、「[ビルドのコマンドとプロパティのマクロ](/visual-cpp/ide/common-macros-for-build-commands-and-properties)」を参照してください。|  
|**\[接続\]** \(リモート Windows デバッガーの場合\)|リモート デバッグ用の接続の種類を、標準の接続と認証を使用しない接続の間で切り替えます。  **\[リモート サーバー名\]** ボックスでリモート コンピューター名を指定します。  接続の種類には、次のようなものがあります。<br /><br /> -   **Windows 認証を使用したリモート接続**<br />-   **認証を使用しないリモート接続 \(ネイティブのみ\)**<br /><br /> **メモ** 認証を使用しないリモート デバッグを行うと、セキュリティ違反に対してリモート コンピューターが脆弱になる可能性があります。  Windows 認証モードの方がより安全です。<br /><br /> 詳細については、「[リモート デバッグのセットアップ](../debugger/remote-debugging.md)」を参照してください。|  
|**\[HTTP URL\]** \(\[Web Service デバッガー\] と \[Web ブラウザー デバッガー\] の場合\)|デバッグするプロジェクトが存在する URL を指定します。|  
|**\[デバッガーのタイプ\]**|使用するデバッガーの種類を指定します。**\[ネイティブのみ\]**、**\[マネージのみ\]**、**\[GPU のみ\]**、**\[混合\]**、**\[自動\]** \(既定\)、または **\[スクリプト\]** を選択します。<br /><br /> -   **\[ネイティブのみ\]** は、アンマネージ C\+\+ コードに使用します。<br />-   **\[マネージのみ\]** は、共通言語ランタイムで実行されるコード \(マネージ コード\) に使用します。<br />-   **\[混合\]** を選択すると、マネージ コードとアンマネージ コードのデバッガーが起動します。<br />-   **\[自動\]** を選択すると、コンパイラと EXE の情報に基づいてデバッガーの種類が決まります。<br />-   **\[スクリプト\]** を選択すると、スクリプトのデバッガーが起動します。<br />-   **\[GPU のみ\]** は、GPU デバイスまたは DirectX リファレンス ラスターライザーで実行される C\+\+ AMP コードに使用します。  「[GPU コードのデバッグ](../debugger/debugging-gpu-code.md)」を参照してください。|  
|**\[環境\]** \(\[ローカル Windows デバッガー\] の場合\)|デバッグするプログラムの環境変数を指定します。  標準的な環境変数の構文 \(`PATH="%SystemRoot%\..."` など\) を使用してください。  各変数は、**\[マージ環境\]** の設定に基づいて、システム環境をオーバーライドするか、システム環境にマージされます。  設定列内でクリックすると、"... の編集" が表示されます。  そのリンクをクリックして、環境変数を編集します。|  
|**\[マージ環境\]** \(\[ローカル Windows デバッガー\] の場合\)|**\[環境\]** ボックスで指定した変数を、オペレーティング システムによって定義されている環境にマージするかどうかを決定します。  既定の設定は \[はい\] です。|  
|**\[SQL デバッグ\]** \(\[MPI クラスター デバッガー\] を除くすべて\)|SQL プロシージャのデバッグを [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] アプリケーションから有効にします。  既定の設定は \[いいえ\] です。|  
|**\[デバッグ アクセラレータの種類\]** \(GPU デバッグの場合のみ\)|デバッグに使用する GPU デバイスを指定します。  互換性のある GPU デバイス用のデバイス ドライバーをインストールするとその他のオプションが追加されます。  既定の設定は \[GPU \- ソフトウェア エミュレーター\] です。|  
|**\[GPU 既定のブレークポイントの動作\]** \(GPU デバッグの場合のみ\)|ブレークポイント イベントを SIMD ワープの各スレッドごとに発生させるかどうかを指定します。  既定の設定では、1 ワープごとに 1 回、ブレークポイント イベントが発生します。|  
|**\[AMP の既定のアクセラレータ\]** \(GPU デバッグの場合のみ\)|GPU コードをデバッグする際、既定の AMP のアクセラレータを指定します。  問題の原因がコードではなく、ハードウェアやドライバーにあるかどうかを調査するには、**\[WARP software accelerator\] \(WARP ソフトウェア アクセラレータ\)** を選択します。|  
|**\[配置ディレクトリ\]** \(リモート Windows デバッガーの場合\)|起動前にプロジェクト出力がコピーされるリモート コンピューター上のパスを指定します。  このパスとして、リモート コンピューター上のネットワーク共有、またはリモート コンピューター上のフォルダーへのパスを指定できます。  既定の設定は空で、プロジェクト出力はネットワーク共有にコピーされます。  ファイルの配置を有効にするには、\[構成マネージャー\] ダイアログ ボックスで **\[配置\]** チェック ボックスをオンにする必要もあります。  詳細については、「[方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。|  
|**\[配置する追加ファイル\]** \(リモート Windows デバッガーの場合\)|配置ディレクトリのプロパティを設定している場合、配置ディレクトリにコピーする追加ファイルのセミコロン区切りのリストを指定します。  既定の設定は空で、配置ディレクトリにコピーされる追加ファイルはありません。  ファイルの配置を有効にするには、\[構成マネージャー\] ダイアログ ボックスで **\[配置\]** チェック ボックスをオンにする必要もあります。  詳細については、「[方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。|  
|**\[Visual C\+\+ デバッグ ランタイム ライブラリの配置\]** \(リモート Windows デバッガーの場合\)|配置ディレクトリのプロパティを設定している場合、現在のプラットフォーム用の Visual C\+\+ デバッグ ランタイム ライブラリをネットワーク共有にコピーする必要があるかどうかを指定します。  既定の設定は \[はい\] です。|  
  
### C\/C\+\+ フォルダー \(\[全般\] カテゴリ\)  
  
|設定|説明|  
|--------|--------|  
|**\[デバッグ情報の形式\]** \([\/Z7、\/Zi、\/ZI \(デバッグ情報の形式\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|プロジェクトに作成するデバッグ情報の種類を指定します。<br /><br /> 既定のオプション \(\/ZI\) では、プログラム データベース \(PDB\) がエディット コンティニュ互換形式で作成されます。  詳細については、「[\/Z7、\/Zd、\/Zi、\/ZI \(デバッグ情報の形式\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)」を参照してください。|  
  
### \[C\/C\+\+\] フォルダー \(\[最適化\] カテゴリ\)  
  
|設定|説明|  
|--------|--------|  
|**\[最適化\]**|コンパイラが生成したコードを最適化するかどうかを指定します。  最適化すると、実行されるコードが変更されます。  最適化したコードはソース コードと一致しなくなります。  したがって、デバッグは困難です。<br /><br /> 既定のオプション \(**\[無効 \(\/0d\)\]**\) では、最適化は行われません。  最適化を行わずにコードを開発し、実行環境用のコードを作成するときに最適化をオンにできます。|  
  
### \[リンカー\] フォルダー \(\[デバッグ\] カテゴリ\)  
  
|設定値|説明|  
|---------|--------|  
|**\[デバッグ情報を作成\]** \([\/DEBUG \(デバッグ情報の生成\)](/visual-cpp/build/reference/debug-generate-debug-info)\)|デバッグ情報を含めるようにリンカーに指示します。デバッグ情報の形式は、\/Z7、\/Zd、Zi、または \/ZI で指定されます。|  
|**\[プログラム データベース ファイルの生成\]** \([\/PDB:name](/visual-cpp/build/reference/pdb-use-program-database)\)|PDB ファイルの名前を指定します。  \[デバッグ情報の形式\] で ZI または \/Zi を選択する必要があります。|  
|**\[プライベート シンボルの削除\]** \([\/PDBSTRIPPED \(プライベート シンボルの除去\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|PDB ファイルのプライベート シンボルを含めない場合は、このボックスに PDB ファイルの名前を指定します。  PDB ファイルを生成するいずれかのコンパイラ オプションまたはリンカー オプションを使ってプログラム イメージをビルドするときにこのオプションを指定すると、2 番目のプログラム データベース \(PDB\) ファイルが作成されます \(コンパイラ オプションまたはリンカー オプションの例: \/DEBUG、\/Z7、\/Zd、  \/Zi など\)。  2 番目の PDB ファイルでは、顧客に提供しないシンボルが省かれています。  詳細については、「[\/PDBSTRIPPED \(プライベート シンボルの除去\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)」を参照してください。|  
|**\[マップ ファイルの作成\]** \([\/MAP \(マップ ファイルの生成\)](/visual-cpp/build/reference/map-generate-mapfile)\)|リンク中にマップ ファイルを生成するようにリンカーに指示します。  既定の設定は \[いいえ\] です。  詳細については、「[\/MAP \(マップ ファイルの生成\)](/visual-cpp/build/reference/map-generate-mapfile)」を参照してください。|  
|**\[マップ ファイル名\]** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*name*\)|\[マップ ファイルの作成\] を選択する場合は、このボックスにマップ ファイルを指定できます。  詳細については、「[\/MAP \(マップ ファイルの生成\)](/visual-cpp/build/reference/map-generate-mapfile)」を参照してください。|  
|**\[マップファイルのエクスポート\]** \([\/MAPINFO \(マップ ファイルに含める情報\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|エクスポートされた関数をマップ ファイルに含めます。  既定の設定は \[いいえ\] です。  詳細については、「[\/MAPINFO \(マップ ファイルに含める情報\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)」を参照してください。|  
|**\[デバッグできるアセンブリ\]** \([\/MAPINFO \(マップ ファイルに含める情報\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|リンカーの \/ASSEMBLYDEBUG オプションの設定を指定します。  次の値を指定できます。<br /><br /> -   **\[デバッグできる属性が作成されませんでした。\]**。<br />-   **\[ランタイム トラッキングおよび最適化の無効 \(\/ASSEMBLYDEBUG\)\]**。  これが既定の設定です。<br />-   **\[ランタイム トラッキングおよび最適化の有効を無効にする \(\/ASSEMBLYDEBUG:無効\)\]**。<br />-   **\[\<親またはプロジェクトの既定値から継承\>\]**。<br />-   詳細については、「[\/ASSEMBLYDEBUG \(DebuggableAttribute の追加\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)」を参照してください。|  
  
 \[構成プロパティ\] フォルダー \(\[デバッグ\] カテゴリ\) 内のこれらの設定は、Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings インターフェイスを使用してプログラムで変更できます。  詳細については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>」を参照してください。  
  
## 参照  
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)   
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [Visual C\+\+ プロジェクトの作成および管理](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(DebuggableAttribute の追加\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [ビルドのコマンドとプロパティのマクロ](/visual-cpp/ide/common-macros-for-build-commands-and-properties)