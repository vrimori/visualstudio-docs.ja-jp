---
title: "ライブ ASP.NET Azure アプリの Visual Studio のデバッグ |Microsoft ドキュメント"
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 32d58ec27d54b1b9c731747b01ad1f59d1d222b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>スナップショットのデバッガーを使用してライブの ASP.NET Azure アプリをデバッグします。

スナップショット デバッガーは、興味のあるコードを実行するときに、実稼働環境でアプリのスナップショットを取得します。 スナップショットを取得するようにデバッガーに指示するには、コードでスナップショットとログポイントを設定します。 デバッガーでは、実稼働アプリケーションのトラフィックに影響を与えることなく、問題を正確に確認できます。 スナップショット デバッガーは、実稼働環境で発生する問題の解決にかかる時間を大幅に短縮するのに役立ちます。

Snappoints と logpoints ブレークポイントに似ています。 ブレークポイントとは異なり snappoints 停止しないでください。 アプリケーション ヒット時です。 通常、スナップショットをキャプチャする、snappoint で 10 ~ 20 ミリ秒がかかります。 

スナップショット コレクションは、Azure App Service で実行されている次の Web アプリで利用できます。

- .NET Framework 4.6.1 以降で実行されている ASP.NET アプリケーション。
- Windows の .NET Core 2.0 以降で実行されている ASP.NET Core アプリケーション。

さらに、スナップショットのデバッガーは、Visual Studio 2017 Enterprise 15.5 またはそれ以降のバージョンと基本的な以上の App Service プランのできるだけです。 

## <a name="start-the-snapshot-debugger"></a>スナップショットのデバッガーを起動します。

1. インストール[Visual Studio 2017 Enterprise バージョン 15.5](https://www.visualstudio.com/downloads/)またはそれ以降。 以前の Visual Studio 2017 のインストールを更新する場合は、Visual Studio インストーラーを実行し、ASP.NET と web 開発ワークロード内のスナップショットのデバッガー コンポーネントを確認します。

2. スナップショット デバッグするには、プロジェクトを開きます。 

    > [!IMPORTANT] 
    > スナップショット デバッグするには、開く必要があります、**ソース コードの同じバージョン**Azure App Service で公開されています。 

3. Cloud Explorer で (選択**ビュー > Cloud Explorer**)、プロジェクトを配置する Azure App Service を右クリックし、選択、**スナップショット デバッガーのアタッチ**スナップショット デバッガーを起動します。

   ![スナップショットのデバッガーを起動して](../debugger/media/snapshot-launch.png "スナップショット デバッガーの起動")

    選択した最初の時間**スナップショット デバッガーのアタッチ**、Azure App Service にスナップショット デバッガーをインストールするように求められます。 このインストールでは、Azure App Service の再起動が必要です。 

   Visual Studio はデバッグ モードのスナップショットが開始されました。

   ![デバッグ モードのスナップショット](../debugger/media/snapshot-message.png "デバッグ モードのスナップショット")

   **モジュール**ウィンドウは、Azure App Service のすべてのモジュールが読み込まれるときに示します (選択**デバッグ/Windows/モジュール**をこのウィンドウを開きます)。

   ![[モジュール] ウィンドウを確認して](../debugger/media/snapshot-modules.png "[モジュール] ウィンドウのチェック")

## <a name="set-a-snappoint"></a>設定、snappoint

1. コード エディターで、snappoint を設定する対象のコード行の横にある左側の余白をクリックします。 これはコードが実行されますがわかっていることを確認してください。

   ![設定、snappoint](../debugger/media/snapshot-set-snappoint.png "snappoint の設定")

2. をクリックして**収集を開始**snappoint オンにします。  

   ![オンに、snappoint](../debugger/media/snapshot-start-collection.png "snappoint オン")

    > [!TIP]
    > スナップショットを表示するときにステップすることはできませんが、次のコードの異なる行で実行するようにコードに複数 snappoints を配置することができます。 コードで複数 snappoints があれば、スナップショット デバッガーによりが対応するスナップショット同じのエンド ユーザー セッションから複数のユーザーがアプリをヒットがある場合でもなります。

## <a name="take-a-snapshot"></a>スナップショットを取得します。

Snappoint がオンにすると、snappoint が配置されたコードの行が実行されるたびに、スナップショットがキャプチャされます。 この実行は、サーバー上の実際の要求によって発生することができます。 にヒットする、snappoint を強制するには、もの web サイトと take、snappoint にヒットするが発生するすべてのアクションが必要なブラウザー ビューに移動することができます。

## <a name="inspect-snapshot-data"></a>スナップショット データを検査します。

1. ヒットした場合、snappoint は、スナップショットが診断ツール ウィンドウに表示されます。 選択**デバッグ/Windows/診断ツールを表示する**をこのウィンドウを開きます。

   ![開く、snappoint](../debugger/media/snapshot-diagsession-window.png "snappoint を開く")

1. 開くには、コード エディターで、スナップショット snappoint をダブルクリックします。

   ![スナップショット データを検査](../debugger/media/snapshot-inspect-data.png "スナップショット データを検査します。")

   データヒントを表示するを使用して変数をポイントすると、このビューから、**ローカル**、**ウォッチ**、および**呼び出し履歴**windows も式の評価とします。

    自体、web サイトは引き続き live エンドユーザーは影響を受けません。既定では snappoint ごとに 1 つだけスナップショットが取得: スナップショットがキャプチャされた後、snappoint がオフにします。 場合は、snappoint で別のスナップショットをキャプチャするには、オンにできます、snappoint 戻る をクリックして**コレクションの更新**です。

複数 snappoints をアプリに追加してオンにすると、**コレクションの更新**ボタンをクリックします。

**ヘルプが必要ですか。** 参照してください、[トラブルシューティングと既知の問題](../debugger/debug-live-azure-apps-troubleshooting.md)と[スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)ページ。

## <a name="set-a-conditional-snappoint"></a>条件付き snappoint を設定します。

アプリで特定の状態を再作成するが困難である場合は、条件付き snappoint の使用が役立つかどうかを検討してください。 条件付き snappoints を使用すると、該当する変数が特定の値を持つなど、アプリが目的の状態になるまで、スナップショットを作成しないようにします。 、フィルター、式を使用する条件を設定したり、ヒット カウントすることができます。

#### <a name="to-create-a-conditional-snappoint"></a>条件付き snappoint を作成するには

1. Snappoint アイコン (中空のボール) を右クリックして選択**設定**です。

   ![設定を選択](../debugger/media/snapshot-snappoint-settings.png "設定の選択")

1. Snappoint 設定 ウィンドウで式を入力します。

   ![式を入力する](../debugger/media/snapshot-snappoint-conditions.png "式を入力します。")

   前の図では、スナップショットののみ、snappoint の作成時に`visitor.FirstName == "Dan"`です。

## <a name="set-a-logpoint"></a>設定、logpoint

Snappoint にヒットしたときに、スナップショットを作成、だけでなく、メッセージを記録する snappoint を構成することも (つまり、作成、logpoint)。 アプリを再デプロイしなくても logpoints を設定することができます。 Logpoints では、ほとんどが実行され、影響や、実行中のアプリケーションに副作用がありません。

#### <a name="to-create-a-logpoint"></a>Logpoint を作成するには

1. Snappoint アイコン (青の六角形) を右クリックして選択**設定**です。

1. Snappoint 設定ウィンドウで、選択**アクション**です。

    ![作成、logpoint](../debugger/media/snapshot-logpoint.png "logpoint を作成します。")

1. [メッセージ] フィールドでは、ログに記録する、新しいログ メッセージを入力できます。 中かっこ内に配置することによって、ログ メッセージに変数を評価することもできます。

    選択した場合**出力ウィンドウに送る**logpoint をヒットすると、診断ツール ウィンドウにメッセージを表示したときに、します。

    ![[.Diagsession] ウィンドウで Logpoint データ](../debugger/media/snapshot-logpoint-output.png ".diagsession ウィンドウに Logpoint データ")

    選択した場合**アプリケーション ログを送信**、logpoint にヒットすると、メッセージの表示を任意の場所からのメッセージを表示できること`System.Diagnostics.Trace`(または`ILogger`.NET Core で) など[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)です。

## <a name="next-steps"></a>次の手順

- スナップショットの表示中に変数を検査する方法については、次を参照してください。 [Debbuger 機能のツアー](../debugger/debugger-feature-tour.md)です。
- ビュー、[スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)です。
- ビュー[ヒントとスナップショットのデバッグに関する既知の問題のトラブルシューティング](../debugger/debug-live-azure-apps-troubleshooting.md)です。
- アプリで例外が発生すると、Application Insights のスナップショットを表示する場合は、ことを行うことができます。 詳細については、次を参照してください。[アプリ用 .NET での例外でのスナップショットをデバッグ](/azure/application-insights/app-insights-snapshot-debugger)です。 Application Insights には、Azure App Service に加えて Service Fabric アプリがサポートされています。
