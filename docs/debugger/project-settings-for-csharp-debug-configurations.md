---
title: プロジェクトの設定、C#構成のデバッグ |Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6de7bfd547516b227063c0d3143b508bcbd9ddfd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059273"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# デバッグ構成のプロジェクト設定

変更することができますC#プロジェクトのデバッグ設定で、 [[デバッグ] タブ](#debug-tab)と[ビルド タブ](#build-tab)のプロジェクトのプロパティ ページ。 

プロジェクトを選択すると、プロパティ ページを開くには、**ソリューション エクスプ ローラー**を選び、**プロパティ**アイコン、またはプロジェクトを右クリックし、選択**プロパティ**します。

詳細については、[デバッグ構成とリリース構成](how-to-set-debug-and-release-configurations.md)に関するページを参照してください。 

>[!IMPORTANT]
>これらの設定は、.NET Core、ASP.NET、または UWP アプリに適用されません。 UWP アプリのデバッグの設定を構成するを参照してください。 [UWP アプリのデバッグ セッションを開始](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)します。  
  
## <a name="debug-tab"></a>[デバッグ] タブ  
  
|設定|説明|
|-------------------------------------| - |
| **構成** | アプリを構築するためのモードを設定します。 選択**アクティブ (Debug)**、**デバッグ**、**リリース**、または**すべて構成**ドロップダウン リストから。 |
| **開始動作** | 選択すると、アクションを指定します**開始**デバッグ構成でします。<br />既定値は - **[プロジェクトの開始]** で、デバッグのスタートアップ プロジェクトを起動します。 詳細については、次を参照してください。[スタートアップ プロジェクトを選択](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))します。<br />- **外部プログラムの開始**始まりはないアプリにアタッチの一部を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 詳細については、次を参照してください。 [、デバッガーでプロセスを実行中にアタッチ](attach-to-running-processes-with-the-visual-studio-debugger.md)します。<br />- **URL でブラウザーを起動**web アプリをデバッグすることができます。 |
| **開始オプション** > **コマンドライン引数** | デバッグ中のアプリ用のコマンドライン引数を指定します。 コマンド名で指定したアプリ名は、**外部プログラムの開始**します。 |
| **開始オプション** > **作業ディレクトリ** | アプリのデバッグ中の作業ディレクトリを指定します。 C#、作業ディレクトリは*\bin\debug*既定。
| **開始オプション** > **リモート コンピューターの使用**|リモート デバッグでは、このオプションを選択し、リモート デバッグ ターゲットの名前を入力または[Msvsmon サーバー名](../debugger/remote-debugging.md)します。 <br />リモート コンピューター上のアプリの場所が指定された、**出力パス**プロパティを**ビルド**タブ。また、EXE ファイルがリモート コンピューターの共有ディレクトリにあることも必要です。 
| **デバッガー エンジン** > **アンマネージ コード デバッグを有効にします。** | 管理対象アプリからネイティブ (アンマネージ) Win32 コードへの呼び出しをデバッグします。 |
| **デバッガー エンジン** > **を有効にする SQL Server のデバッグ** | SQL Server データベース オブジェクトをデバッグします。 |
  
## <a name="build-tab"></a>[ビルド] タブ  
  
|設定|説明|  
|-------------|-----------------|  
|**一般的な** > **条件付きコンパイル シンボル**|選択されている場合は、デバッグとトレースの定数を定義します。<br /><br /> これらの定数により、[Debug クラス](/dotnet/api/system.diagnostics.debug)と [Trace クラス](/dotnet/api/system.diagnostics.trace)の条件付きコンパイルが有効になります。 これらの定数を定義すると、Debug クラスと Trace クラスのメソッドによって[出力ウィンドウ](../ide/reference/output-window.md)に出力が生成されます。 これらの定数を定義しない場合、Debug クラスと Trace クラスのメソッドはコンパイルされず、出力も生成されません。<br /><br />通常、デバッグはビルドのデバッグ バージョンで定義され、リリース バージョンで定義されていません。 トレースは、デバッグとリリースの両方のバージョンで定義されます。|  
|**一般的な** > **コードの最適化**|バグは、最適化されたコードでのみが表示されたら、しない限り、この設定はデバッグ ビルドには選択されていないままにします。 最適化されたコードは、命令がソース コード内のステートメントに直接対応していないためにをデバッグするに難しくなります。|  
|**出力** > **出力パス**|通常は、デバッグ用の *bin\Debug* に設定します。|
|**高度な**ボタン|高度なデバッグ オプションについては、次を参照してください。[ビルドの詳細設定 ダイアログ ボックス (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)します。 シンボルの移植可能な形式 (*.pdb*) ファイルは、.NET Core アプリの最近使用したクロス プラットフォーム形式。 
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)