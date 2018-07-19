---
title: ライブの ASP.NET Azure アプリをデバッグします。
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 5207af86d850dca3e4dfde515237452c293788ea
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281551"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>スナップショット デバッガーを使用して、ライブの ASP.NET Azure アプリをデバッグします。

スナップショット デバッガーで関心があるコードを実行するときに、運用環境でのアプリのスナップショットを取得します。 スナップショットを取得するようにデバッガーに指示するには、コードでスナップショットとログポイントを設定します。 デバッガーでは、実稼働アプリケーションのトラフィックに影響を与えることなく、問題を正確に確認できます。 スナップショット デバッガーは、実稼働環境で発生する問題の解決にかかる時間を大幅に短縮するのに役立ちます。

スナップ ポイントとログポイント、ブレークポイントに似ていますが、ブレークポイントとは異なり、スナップ ポイントが、アプリケーションを停止しない場合にヒットします。 通常、スナップ ポイントでスナップショットをキャプチャすると、10 ~ 20 ミリ秒がかかります。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * スナップショット デバッガーを起動します
> * スナップ ポイントを設定し、スナップショットの表示
> * ログポイントを設定します。

## <a name="prerequisites"></a>前提条件

* スナップショット デバッガーは、Visual Studio 2017 Enterprise バージョン 15.5 以降で使用できるのみ、 **ASP.NET および web 開発ワークロード**します。 ASP.NET Core, も必要があります、します。**NET Core 開発**ワークロードをインストールします。

    インストールされていない場合は、インストール[Visual Studio 2017 Enterprise バージョン 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)またはそれ以降。 以前の Visual Studio 2017 のインストールから更新する場合、Visual Studio インストーラーを実行しスナップショット デバッガーのコンポーネントを確認、 **ASP.NET および web 開発ワークロード**します。

* Basic 以上の Azure App Service プランです。

* スナップショット コレクションは、Azure App Service で実行されている次の Web アプリで利用できます。

    * .NET Framework 4.6.1 以降で実行されている ASP.NET アプリケーション。
    * Windows の .NET Core 2.0 以降で実行されている ASP.NET Core アプリケーション。

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>プロジェクトを開き、スナップショット デバッガーを起動します

1. スナップショット デバッグするには、プロジェクトを開きます。

    > [!IMPORTANT]
    > スナップショットのデバッグを開く必要があります、**ソース コードの同じバージョン**Azure App Service に公開されています。

1. Cloud Explorer で (**ビュー > Cloud Explorer**) で、プロジェクトに配置する Azure App Service を右クリックし、選択**スナップショット デバッガーのアタッチ**します。

   ![スナップショット デバッガーを起動します。](../debugger/media/snapshot-launch.png)

    選択した最初の時刻**スナップショット デバッガーのアタッチ**、Azure App Service でのスナップショット デバッガー サイト拡張機能をインストールするように求められます。 このインストールでは、Azure App Service の再起動が必要です。

   Visual Studio はデバッグ モードのスナップショットが開始されました。

    > [!NOTE]
    > Application Insights サイト拡張機能では、スナップショットのデバッグもサポートしています。 「期限切れの拡張機能をサイト」のエラー メッセージが発生した場合は、次を参照してください。[トラブルシューティングのヒントやスナップショットのデバッグに関する既知の問題](../debugger/debug-live-azure-apps-troubleshooting.md)の詳細をアップグレードします。

   ![スナップショットのデバッグ モード](../debugger/media/snapshot-message.png)

   **モジュール**ウィンドウは、すべてのモジュールが読み込まれるときに、Azure App Service を示します (選択**デバッグ/Windows/モジュール**をこのウィンドウを開きます)。

   ![[モジュール] ウィンドウを確認してください。](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定、スナップ ポイント

1. コード エディターで、スナップ ポイントを設定する対象のコード行の横にある左側の余白をクリックします。 これはコードが実行されますがわかっていることを確認します。

   ![設定、スナップ ポイント](../debugger/media/snapshot-set-snappoint.png)

2. クリックして**コレクションの開始**スナップ ポイントを有効にします。

   ![オンにする、スナップ ポイント](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > スナップショットを表示するときにステップすることはできませんが、異なるコード行で実行するコードに複数個のスナップ ポイントを配置することができます。 場合は、コード内の複数のスナップ ポイントにある場合は、スナップショット デバッガーにより同じエンド ユーザー セッションから、対応するスナップショットがあることを確認します。 スナップショット デバッガーは多くのユーザーがアプリのヒットがある場合でも、します。

## <a name="take-a-snapshot"></a>スナップショットを取得します。

スナップ ポイントがオンにすると、スナップ ポイントが配置されているコードの行が実行されるたびにスナップショットがキャプチャされます。 サーバー上の実際の要求によって、この実行可能性があります。 ヒットし、web サイトのブラウザー ビューに移動し、アクションを実行する、スナップ ポイントを強制的に、スナップ ポイントにヒットするが必要です。

## <a name="inspect-snapshot-data"></a>スナップショット データを検査します。

1. スナップ ポイントをヒットすると、スナップショットが診断ツール ウィンドウに表示されます。 このウィンドウを開くには、次のように選択します。**デバッグ/Windows/診断ツールの表示**します。

   ![開く、スナップ ポイント](../debugger/media/snapshot-diagsession-window.png)

1. コード エディターでスナップショットを開くスナップ ポイントをダブルクリックします。

   ![スナップショット データを検査します。](../debugger/media/snapshot-inspect-data.png)

   データヒントを表示するには、使用して変数をポイントすると、このビューから、 **[ローカル]**、**ウォッチ**と**呼び出し履歴**windows、およびも式を評価します。

    Web サイト自体はまだ存在していると、エンドユーザーに影響はありません。 既定でスナップ ポイントごとに 1 つだけスナップショットが取得: スナップショットがキャプチャされた後、スナップ ポイントがオフにします。 場合は、スナップ ポイントにある別のスナップショットをキャプチャするを再度有効にできます、スナップ ポイントをクリックして**コレクションの更新**します。

アプリへの複数のスナップ ポイントを追加しをオンにすることができます、**コレクションの更新**ボタンをクリックします。

**ヘルプが必要ですか。** 参照してください、[既知の問題のトラブルシューティングと](../debugger/debug-live-azure-apps-troubleshooting.md)と[スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)ページ。

## <a name="set-a-conditional-snappoint"></a>条件付きのスナップ ポイントを設定します。

アプリの特定の状態を再作成が困難である場合は、条件付きのスナップ ポイントの使用に役立つかどうかを検討してください。 条件付きのスナップ ポイント ヘルプは、アプリが、変数が検査する特定の値を持っている場合など、目的の状態になるまでのスナップショットを回避します。 ヒット カウントまたは、フィルター、式を使用する条件を設定できます。

#### <a name="to-create-a-conditional-snappoint"></a>条件付きのスナップ ポイントを作成するには

1. スナップ ポイント アイコン (白抜きの球) を右クリックし **設定**します。

   ![設定を選択します。](../debugger/media/snapshot-snappoint-settings.png)

1. スナップ ポイントの設定 ウィンドウで式を入力します。

   ![式を入力します。](../debugger/media/snapshot-snappoint-conditions.png)

   上の図で、スナップショットののみ、スナップ ポイントの作成時に`visitor.FirstName == "Dan"`します。

## <a name="set-a-logpoint"></a>ログポイントを設定します。

スナップショットを作成、スナップ ポイントがヒットしたときにだけでなく、メッセージを記録するスナップ ポイントを構成することも (つまり、ログポイントを作成します)。 ログポイントを設定するには、アプリを再デプロイしなくてもします。 ログポイントでは、ほとんどが実行され、影響や、実行中のアプリケーションに副作用がありません。

#### <a name="to-create-a-logpoint"></a>ログポイントを作成するには

1. スナップ ポイント (青色の六角形) アイコンを右クリックし、選択**設定**します。

1. スナップ ポイントの設定 ウィンドウで次のように選択します。**アクション**します。

    ![作成、個のログポイント](../debugger/media/snapshot-logpoint.png)

1. メッセージ フィールドに、ログに記録する新しいログ メッセージを入力できます。 中かっこ内に配置することによってログ メッセージに変数を評価することもできます。

    選択した場合**出力ウィンドウに送信**、ログポイントをヒットすると、診断ツール ウィンドウで、メッセージが表示されます。

    ![Diagsession ウィンドウでデータを個のログポイント](../debugger/media/snapshot-logpoint-output.png)

    選択した場合**アプリケーション ログに送信**、ログポイントにヒットしたときに、メッセージの表示を任意の場所からのメッセージを確認できます`System.Diagnostics.Trace`(または`ILogger`で .NET Core) など[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、スナップショット デバッガーを使用する方法を学習できました。 この機能の詳細を確認することがあります。

> [!div class="nextstepaction"]
> [スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)
