---
title: ライブ ASP.NET Azure アプリの Visual Studio のデバッグ |Microsoft ドキュメント
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 0382f720e73504147c5f38ba61b5407db039a487
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>スナップショットのデバッガーを使用してライブの ASP.NET Azure アプリをデバッグします。

スナップショット デバッガーで関心のあるコードを実行するときに、実稼働環境でアプリのスナップショットを取得します。 スナップショットを取得するようにデバッガーに指示するには、コードでスナップショットとログポイントを設定します。 デバッガーでは、実稼働アプリケーションのトラフィックに影響を与えることなく、問題を正確に確認できます。 スナップショット デバッガーは、実稼働環境で発生する問題の解決にかかる時間を大幅に短縮するのに役立ちます。

Snappoints と logpoints は、ブレークポイントに似ていますが、snappoints、ブレークポイントとは異なり、アプリケーションを停止しない場合にヒットします。 通常、スナップショットをキャプチャする、snappoint で 10 ~ 20 ミリ秒がかかります。 

スナップショット コレクションは、Azure App Service で実行されている次の Web アプリで利用できます。

- .NET Framework 4.6.1 以降で実行されている ASP.NET アプリケーション。
- Windows の .NET Core 2.0 以降で実行されている ASP.NET Core アプリケーション。

さらに、スナップショットのデバッガーは、Visual Studio 2017 Enterprise 15.5 またはそれ以降のバージョンと基本的な以上の App Service プランのできるだけです。 

このチュートリアルでは説明します。

> [!div class="checklist"]
> * スナップショットのデバッガーを起動します。
> * Snappoint を設定し、スナップショットの表示
> * 設定、logpoint

## <a name="start-the-snapshot-debugger"></a>スナップショットのデバッガーを起動します。

1. インストール[Visual Studio 2017 Enterprise バージョン 15.5](https://www.visualstudio.com/downloads/)またはそれ以降。 以前の Visual Studio 2017 のインストールを更新する場合は、Visual Studio インストーラーを実行し、ASP.NET と web 開発ワークロード内のスナップショットのデバッガー コンポーネントを確認します。

2. スナップショット デバッグするには、プロジェクトを開きます。 

    > [!IMPORTANT] 
    > スナップショットのデバッグ を開く必要があります、**ソース コードの同じバージョン**Azure App Service で公開されています。 

3. Cloud Explorer で (**ビュー > Cloud Explorer**) をプロジェクトを配置する Azure App Service を右クリックし、**スナップショット デバッガーのアタッチ**です。

   ![スナップショットのデバッガーを起動します。](../debugger/media/snapshot-launch.png)

    選択した最初の時間**スナップショット デバッガーのアタッチ**、Azure App Service でスナップショットのデバッガーのサイト拡張機能をインストールするように求められます。 このインストールでは、Azure App Service の再起動が必要です。 

   Visual Studio はデバッグ モードのスナップショットが開始されました。

    > [!NOTE]
    > Application Insights のサイト拡張機能は、スナップショットのデバッグもサポートします。 「サイト拡張機能の有効期限が切れて」のエラー メッセージが発生した場合は、次を参照してください。[ヒントとスナップショットのデバッグに関する既知の問題のトラブルシューティング](../debugger/debug-live-azure-apps-troubleshooting.md)の詳細をアップグレードするためです。

   ![デバッグ モードのスナップショット](../debugger/media/snapshot-message.png)

   **モジュール**ウィンドウは、Azure App Service のすべてのモジュールが読み込まれるときに示します (選択**デバッグ/Windows/モジュール**をこのウィンドウを開きます)。

   ![[モジュール] ウィンドウのチェック](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定、snappoint

1. コード エディターで、snappoint を設定する対象のコード行の横にある左側の余白をクリックします。 これはコードが実行されますがわかっていることを確認してください。

   ![設定、snappoint](../debugger/media/snapshot-set-snappoint.png)

2. をクリックして**収集を開始**snappoint オンにします。  

   ![オンに、snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > スナップショットを表示するときにステップすることはできませんが、次のコードの異なる行で実行するようにコードに複数 snappoints を配置することができます。 複数 snappoints、コードである場合は、スナップショットのデバッガーが対応するスナップショットが、同じのエンド ユーザー セッションであることを確認して行います。 スナップショットのデバッガーはこのアプリにヒットする多くのユーザーがある場合でも行われます。

## <a name="take-a-snapshot"></a>スナップショットを取得します。

Snappoint がオンにすると、snappoint が配置されたコードの行が実行されるたびに、スナップショットがキャプチャされます。 この実行は、サーバー上の実際の要求によって発生することができます。 ヒットし、web サイトのブラウザー ビューに移動し、アクションを実行する、snappoint を強制的にヒットする、snappoint が発生することが必要です。

## <a name="inspect-snapshot-data"></a>スナップショット データを検査します。

1. ヒットした場合、snappoint は、スナップショットが診断ツール ウィンドウに表示されます。 このウィンドウを開くには、選択**デバッグ/Windows/診断ツールを表示する**です。

   ![Snappoint を開く](../debugger/media/snapshot-diagsession-window.png)

1. 開くには、コード エディターで、スナップショット snappoint をダブルクリックします。

   ![スナップショット データを検査します。](../debugger/media/snapshot-inspect-data.png)

   データヒントを表示するを使用して変数をポイントすると、このビューから、**ローカル**、**ウォッチ**、および**呼び出し履歴**windows も式の評価とします。

    自体、web サイトがまだライブされ、エンドユーザーが影響されません。 既定では snappoint ごとに 1 つだけスナップショットが取得: スナップショットがキャプチャされた後、snappoint がオフにします。 場合は、snappoint で別のスナップショットをキャプチャするには、オンにできます、snappoint 戻る をクリックして**コレクションの更新**です。

複数 snappoints をアプリに追加してオンにすると、**コレクションの更新**ボタンをクリックします。

**ヘルプが必要ですか。** 参照してください、[トラブルシューティングと既知の問題](../debugger/debug-live-azure-apps-troubleshooting.md)と[スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)ページ。

## <a name="set-a-conditional-snappoint"></a>条件付き snappoint を設定します。

アプリで特定の状態を再作成するが困難である場合は、条件付き snappoint の使用が役立つかどうかを検討してください。 条件付き snappoints れないようにする、アプリが、変数が検査する特定の値を持っている場合など、目的の状態になるまで、スナップショットを作成します。 、フィルター、式を使用する条件を設定したり、ヒット カウントすることができます。

#### <a name="to-create-a-conditional-snappoint"></a>条件付き snappoint を作成するには

1. Snappoint アイコン (中空のボール) を右クリックして選択**設定**です。

   ![設定を選択します。](../debugger/media/snapshot-snappoint-settings.png)

1. Snappoint 設定 ウィンドウで式を入力します。

   ![式を入力します。](../debugger/media/snapshot-snappoint-conditions.png)

   前の図では、スナップショットののみ、snappoint の作成時に`visitor.FirstName == "Dan"`です。

## <a name="set-a-logpoint"></a>設定、logpoint

Snappoint にヒットしたときに、スナップショットを作成、だけでなく、メッセージを記録する snappoint を構成することも (つまり、作成、logpoint)。 アプリを再デプロイしなくても logpoints を設定することができます。 Logpoints では、ほとんどが実行され、影響や、実行中のアプリケーションに副作用がありません。

#### <a name="to-create-a-logpoint"></a>Logpoint を作成するには

1. Snappoint アイコン (青の六角形) を右クリックして選択**設定**です。

1. Snappoint 設定ウィンドウで、選択**アクション**です。

    ![Logpoint を作成します。](../debugger/media/snapshot-logpoint.png)

1. [メッセージ] フィールドでは、ログに記録する、新しいログ メッセージを入力できます。 中かっこ内に配置することによって、ログ メッセージに変数を評価することもできます。

    選択した場合**出力ウィンドウに送る**logpoint をヒットすると、診断ツール ウィンドウにメッセージを表示したときに、します。

    ![Diagsession ウィンドウで Logpoint データ](../debugger/media/snapshot-logpoint-output.png)

    選択した場合**アプリケーション ログを送信**、logpoint にヒットすると、メッセージの表示を任意の場所からのメッセージを表示できること`System.Diagnostics.Trace`(または`ILogger`.NET Core で) など[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、スナップショットのデバッガーを使用する方法を学びました。 この機能に関する詳細を読みたい場合があります。

> [!div class="nextstepaction"]
> [スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)
