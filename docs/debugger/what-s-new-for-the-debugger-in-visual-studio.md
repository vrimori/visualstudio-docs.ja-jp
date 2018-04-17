---
title: Visual Studio 2017 のデバッガーの新機能 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0bcd44da88279f042469356a97bce7f369e1190
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>デバッガーの新機能します。 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

デバッガーには、これらの新機能が含まれています。

- 15.5 の新機能、**スナップショット デバッガー**興味のあるコードを実行するときに、実稼働環境でアプリのスナップショットを取得します。 スナップショットを取得するようにデバッガーに指示するには、コードでスナップショットとログポイントを設定します。 デバッガーでは、実稼働アプリケーションのトラフィックに影響を与えることなく、問題を正確に確認できます。 スナップショット デバッガーは、実稼働環境で発生する問題の解決にかかる時間を大幅に短縮するのに役立ちます。

    スナップショット コレクションは、Azure App Service で実行されている次の Web アプリで利用できます。

    * .NET Framework 4.6.1 以降で実行されている ASP.NET アプリケーション。
    * Windows の .NET Core 2.0 以降で実行されている ASP.NET Core アプリケーション。

    詳細については、次を参照してください。[スナップショット デバッガーを使用してライブの ASP.NET アプリのデバッグ](../debugger/debug-live-azure-applications.md)です。

- Visual Studio Enterprise でのみ、15.5 で新しい**IntelliTrace ステップ ライトバック**手順イベント、アプリケーションのすべてのブレークポイントとデバッガーのスナップショットを自動的に取得します。 記録されたスナップショットにより、前のブレークポイントまたはステップに戻り、過去の時点でのアプリケーションの状態を確認できるようになります。 IntelliTrace ステップ バックでは、以前のアプリケーションの状態を確認したいが、デバッグの再開や必要なアプリ状態の再作成は必要でない場合に時間を節約できます。

    スナップショット間を移動して表示するには、デバッグ ツールバーの **[前に戻る]** ボタンと **[次へ進む]** ボタンを使用します。 これらのボタンを使用して、**[診断ツール]** ウィンドウの **[イベント]** タブに表示されるイベント間を移動します。

    ![ステップ後退と転送ボタン](../debugger/media/intellitrace-step-back-icons-description.png  "旧バージョンとステップと転送ボタン")

    詳細については、「[IntelliTrace ステップ バックを使用してスナップショットを表示する](../debugger/how-to-use-intellitrace-step-back.md)」のページ参照してください。

- **例外ヘルパー**置換、例外処理アシスタントと、エラーが発生した非モーダル ダイアログ ボックスに表示されます。 **例外ヘルパー**簡単にアクセスするには、内部例外、(使用可能な場合)、デバッガーによってさらに分析および即時アクセスを提供、**例外設定**例外。 例外ヘルパーはブロックして表示する必要がある場合浮動ビューにドラッグできます。

    たとえば、 **NullReferenceException**を null 参照 (追加情報) を持つ変数が表示されます。

    ![デバッガーの例外ヘルパー](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    詳細については、「[Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/)」 (Visual Studio で新しい例外ヘルパーを使用する) のブログの投稿を参照してください。

- コードを選択すると、デバッガーで一時停止中に行を実行できます、**ここまで実行**緑色の矢印アイコン (アイコンが表示、コード行にポインターを置いたときに)。 これにより、一時的なブレークポイントを設定する必要があります。

    ![デバッガーの実行 をクリックを](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- 例外に条件を設定することができます、**例外設定** ダイアログ ボックス (を使用してこれを行う、**条件の編集**アイコンを右クリック メニューを使用してまたは例外設定 ダイアログ ボックスで、例外です。)現在サポートされている条件には、例外のるまたは除外するには、モジュール名が含まれます。

    ![例外条件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- プロセスにアタッチ ダイアログ ボックスに、プロセスにアタッチする必要のあるをすばやく識別するのに役立つ新しい検索機能が含まれています。

    ![検索プロセスにアタッチする](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

これらの新機能の詳細については、次を参照してください。、[のリリース ノート[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag)です。
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)