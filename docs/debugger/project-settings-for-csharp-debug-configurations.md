---
title: プロジェクトの c# デバッグ構成の設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.openlocfilehash: 65b30c1dc0b4306c7104b4d0b3dcd38a2cc55b1d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="project-settings-for--c-debug-configurations"></a>C# デバッグ構成のプロジェクト設定
C# デバッグ構成のプロジェクト設定を変更することができます、**プロパティ ページ**ウィンドウで説明したよう[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)です。 次の表は、デバッガー関連の設定を検索する場所を示して、**プロパティ ページ**ウィンドウです。  
  
> [!WARNING]
>  このトピックは UWP アプリには適用されません。 参照してください[(VB、c#、C++ および XAML) は、デバッグ セッションを開始](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> [デバッグ] タブ  
  
|**設定**|**説明**|  
|-----------------|---------------------|  
|**構成**|アプリケーションをコンパイルするためのモードを設定します。 中から選択**アクティブ (Debug)**、**デバッグ**、**リリース**、**すべて構成**です。|  
|**開始アクション**|[デバッグ] メニューの [開始] を選択したときに発生するアクションを指定します。<br /><br /> -   **プロジェクトを開始**既定値は、デバッグのスタートアップ プロジェクトを起動します。 詳細については、次を参照してください。[スタートアップ プロジェクトの選択](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd)です。<br />-   **外部プログラムの開始**れないプログラムを起動してアタッチすることができますの一部、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 詳細については、次を参照してください。[実行中のプログラムへのアタッチ](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)です。<br />-   **URL でブラウザーを起動**Web アプリケーションをデバッグすることができます。|  
|**コマンド ライン引数**|デバッグするプログラムのコマンド ライン引数を指定します。 コマンド名は、[外部プログラムの開始] に指定されたプログラム名です。 [開始動作] が [URL の開始] に設定されている場合、コマンド ライン引数は指定できません。|  
|**作業ディレクトリ**|デバッグするプログラムの作業ディレクトリを指定します。 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] では、作業ディレクトリはアプリケーションが起動されるディレクトリであり、既定では \bin\debug です。|  
|**リモート コンピューターの使用**|デバッグの目的で、アプリケーションが実行されるリモート コンピューターの名前または[Msvsmon サーバー名](../debugger/remote-debugging.md)です。 リモート コンピューター上の EXE ファイルの場所は、[構成プロパティ] フォルダー、[ビルド] カテゴリ内の [出力パス] プロパティで指定します。 また、EXE ファイルがリモート コンピューターの共有ディレクトリにあることも必要です。|
|**アンマネージ コード デバッグを有効にする**|マネージ アプリケーションからネイティブ (アンマネージ) Win32 コードの呼び出しをデバッグできます。|  
|**SQL Server デバッグを有効にする**|SQL Server データベース オブジェクトのデバッグを許可します。|  
  
##  <a name="BKMK_Build_tab"></a> [ビルド] タブ  
  
|設定|説明|  
|-------------|-----------------|  
|**条件付きコンパイル シンボル:**|定数 DEBUG および定数 TRACE をここで定義します。<br /><br /> これらの定数の条件付きコンパイルを有効にする、 [Debug クラス](/dotnet/api/system.diagnostics.debug)と[Trace クラス](/dotnet/api/system.diagnostics.trace)です。 これらの定数が定義されているデバッグし、Trace クラスのメソッドへの出力を生成する、[出力ウィンドウ](../ide/reference/output-window.md)します。 これらの定数を定義しない場合、Debug クラスと Trace クラスのメソッドはコンパイルされず、出力も生成されません。<br /><br /> デバッグは通常、プログラムのデバッグ バージョンで定義され、リリース バージョンで定義されていません。<br />トレースは通常、デバッグとリリースの両方のバージョンで定義します。|  
|**コードの最適化**|デバッグ バージョンでは、最適化されたコードにだけ現れるバグを見つけた場合に限って、この設定をオンにすることをお勧めします。 最適化されたコードは、命令がソース ウィンドウのステートメントに直接対応していないため、デバッグが困難です。|  
|**[出力パス]**|通常は、デバッグ用の bin\Debug に設定します。|

> [!NOTE]
> 検索するデバッグ オプションの詳細についての**詳細**ボタンをクリックしを参照してください[ビルドの詳細設定 ダイアログ ボックス (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md)です。 シンボル (.pdb) ファイルをポータブル形式は、.NET Core の最新のクロスプラット フォーム形式です。 
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)