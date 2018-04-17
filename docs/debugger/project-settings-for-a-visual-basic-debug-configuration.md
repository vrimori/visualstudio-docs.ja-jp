---
title: プロジェクトの Visual Basic デバッグ構成の設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 727e36da37c38d57013071d1d5013c27b8a95b87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Visual Basic デバッグ構成のプロジェクト設定
プロジェクト設定を変更することができます、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]のデバッグ構成、**プロパティ ページ**ウィンドウで説明したよう[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)です。 次の表は、デバッガー関連の設定を検索する場所を示して、**プロパティ ページ**ウィンドウです。  
  
> [!WARNING]
>  このトピックは UWP アプリには適用されません。 参照してください[(VB、c#、C++ および XAML) は、デバッグ セッションを開始](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>[デバッグ] タブ  
  
|設定|説明|  
|-------------|-----------------|  
|**構成**|アプリケーションをコンパイルするためのモードを設定します。 中から選択**アクティブ (Debug)**、**デバッグ**、**リリース**、**すべて構成**です。|  
|**開始アクション**|[デバッグ] メニューの [開始] を選択したときに発生するアクションを指定します。<br /><br /> -   **プロジェクトを開始**既定値は、デバッグのスタートアップ プロジェクトを起動します。 <br />-   **外部プログラムの開始**れないプログラムを起動してアタッチすることができますの一部、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。<br />-   **URL でブラウザーを起動**Web アプリケーションをデバッグすることができます。|  
|**コマンドライン引数**|デバッグするプログラムのコマンド ライン引数を指定します。 コマンド名は、[外部プログラムの開始] に指定されたプログラム名です。 [開始動作] を [URL の開始] に設定した場合、コマンド ライン引数は無視されます。|  
|**作業ディレクトリ**|デバッグするプログラムの作業ディレクトリを指定します。 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、作業ディレクトリはアプリケーションが起動されるディレクトリです。 既定の作業ディレクトリは、\bin\Debug または \bin\Release、現在の構成に応じてです。|  
|**リモート コンピューターを使用します。**|このチェック ボックスがオンの場合、リモート デバッグは有効です。 デバッグの目的で、アプリケーションが実行されるリモート コンピューターの名前を入力する ボックスで、または[Msvsmon サーバー名](../debugger/remote-debugging.md)です。 リモート コンピューター上の EXE ファイルの場所は、[ビルド] タブの [出力パス] プロパティで指定します。また、EXE ファイルがリモート コンピューターの共有ディレクトリにあることも必要です。|  
|**アンマネージ コードのデバッグ**|マネージ アプリケーションからネイティブ (アンマネージ) Win32 コードの呼び出しをデバッグできます。 これは、[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] プロジェクトで [デバッガーのタイプ] に [混合] を選択するのと同じ効果があります。|  
|**SQL Server のデバッグ**|SQL Server データベース オブジェクトのデバッグを許可します。|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>[コンパイル] タブ : [詳細コンパイル オプション] ボタンをクリックします。  
  
|設定|説明|  
|-------------|-----------------|  
|**最適化を有効にする**|このオプションはオフにしておくことをお勧めします。 最適化を有効にすると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に表示されるソース コードとは異なるコードが実行されるため、デバッグが困難になります。 コードが最適化されている場合、"マイ コードのみ" でデバッグするときに、既定でシンボルが読み込まれません。|  
|**デバッグ情報を作成**|既定で、デバッグ バージョンとリリース バージョンの両方に定義されます。この設定 (/debug コンパイラ オプションに相当します) に基づいて、ビルド時にデバッグ情報が作成されます。 デバッガーでは、この情報を使って変数名やその他の情報を見やすい形式でデバッグ時に表示します。 この情報を設定せずにプログラムをコンパイルすると、デバッガーの機能は制限されます。 詳細については、次を参照してください。 [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug)です。|  
|**定数 DEBUG を定義します。**|出力関数の条件付きコンパイルを有効にこのシンボルを定義する、 [Debug クラス](/dotnet/api/system.diagnostics.debug)です。 このシンボルを定義すると、クラスのメソッドをデバッグ出力を生成、[出力ウィンドウ](../ide/reference/output-window.md)します。 このシンボルを定義しない場合、Debug クラスのメソッドはコンパイルされず、出力も生成されません。 このシンボルは、デバッグ バージョンに定義します。リリース バージョンには定義しません。 リリース バージョンにこのシンボルを定義すると、不要なコードのためにプログラムの実行速度が低下します。|  
|**定数 TRACE を定義します。**|出力関数の条件付きコンパイルを有効にこのシンボルを定義する、 [Trace クラス](/dotnet/api/system.diagnostics.trace.aspx)です。 このシンボルを定義すると、Trace クラスのメソッド出力を生成、[出力ウィンドウ](../ide/reference/output-window.md)します。 このシンボルを定義しない場合、Trace クラスのメソッドはコンパイルされず、出力も生成されません。 このシンボルは、既定で、デバッグ バージョンとリリース バージョンの両方に定義されます。|  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)