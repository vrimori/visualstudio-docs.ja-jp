---
title: Visual Studio 2017 のデバッガーの新機能については |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: cdb56a12f2f9fb6838579165bbe374e4dfbdca47
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542438"
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>デバッガーの新機能については [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

デバッガーには、これらの新機能が含まれています。

- 15.5 の新機能、**スナップショット デバッガー**興味のあるコードを実行するときに、運用環境でのアプリのスナップショットを取得します。 スナップショットを取得するようにデバッガーに指示するには、コードでスナップショットとログポイントを設定します。 デバッガーでは、実稼働アプリケーションのトラフィックに影響を与えることなく、問題を正確に確認できます。 スナップショット デバッガーは、実稼働環境で発生する問題の解決にかかる時間を大幅に短縮するのに役立ちます。

    スナップショット コレクションは、Azure App Service で実行されている次の Web アプリで利用できます。

    * .NET Framework 4.6.1 以降で実行されている ASP.NET アプリケーション。
    * Windows の .NET Core 2.0 以降で実行されている ASP.NET Core アプリケーション。

    詳細については、次を参照してください。[スナップショット デバッガーを使用して、ライブ ASP.NET アプリのデバッグ](../debugger/debug-live-azure-applications.md)します。

- Visual Studio Enterprise でのみ、15.5 の新**IntelliTrace ステップ バック**ステップ イベント、アプリケーションのすべてのブレークポイントとデバッガーのスナップショットを自動的に取得します。 記録されたスナップショットにより、前のブレークポイントまたはステップに戻り、過去の時点でのアプリケーションの状態を確認できるようになります。 IntelliTrace ステップ バックでは、以前のアプリケーションの状態を確認したいが、デバッグの再開や必要なアプリ状態の再作成は必要でない場合に時間を節約できます。

    スナップショット間を移動して表示するには、デバッグ ツールバーの **[前に戻る]** ボタンと **[次へ進む]** ボタンを使用します。 これらのボタンを使用して、**[診断ツール]** ウィンドウの **[イベント]** タブに表示されるイベント間を移動します。

    ![下位と転送 ボタンをステップ](../debugger/media/intellitrace-step-back-icons-description.png  "戻ると転送ボタン")

    詳細については、次を参照してください。、 [IntelliTrace を使用して前のアプリ状態を検査](../debugger/view-historical-application-state.md)ページ。

- **例外ヘルパー**例外処理アシスタントを置き換えるし、エラーが発生した非モーダル ダイアログ ボックスが表示されます。 **例外ヘルパー** 、内部例外、(該当する場合)、デバッガーによって追加の分析にすばやくアクセスしにすぐにアクセスを提供します、**例外設定**例外。 例外ヘルパーを表示することによってブロックされている場合浮動ビューにドラッグできます。

    たとえば、 **NullReferenceException**を null 参照 (余分な情報) を持つ変数が表示されます。

    ![デバッガーの例外ヘルパー](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    詳細については、「[Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/)」 (Visual Studio で新しい例外ヘルパーを使用する) のブログの投稿を参照してください。

- 選択して、デバッガーで一時停止中のコード行を実行して、**ここまで実行**(アイコンが表示のコード行を合わせたとき)、緑色の矢印アイコン。 これにより、一時的なブレークポイントを設定する必要があります。

    ![デバッガーのクリックで実行](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- 例外で条件を設定することができます、**例外設定** ダイアログ ボックス (を使用してこれを行う、**条件を編集する**アイコンを右クリック メニューを使用して例外設定 ダイアログ ボックスで、例外です。)現在サポートされている条件には、例外の追加または除外モジュール名が含まれます。

    ![例外条件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- プロセスにアタッチ ダイアログ ボックスにはより迅速にアタッチする必要のあるプロセスを特定するのに役立つ新しい検索機能が含まれています。

    ![検索では、プロセスにアタッチ](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

これらの新機能の詳細については、次を参照してください。、[のリリース ノート[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデバッグ](../debugger/index.md)
- [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)