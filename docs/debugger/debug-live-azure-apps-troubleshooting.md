---
title: スナップショットのデバッグのトラブルシューティングと既知の問題 |Microsoft ドキュメント
ms.date: 11/07/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae5da4031ceb2716970b028fb15c11348df89c4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>スナップショットは、Visual Studio でデバッグするためのトラブルシューティングと既知の問題

このトピックで説明した手順を実行しても問題が解決しない場合にお問い合わせsnaphelp@microsoft.comです。

## <a name="issue-snappoint-does-not-turn-on"></a>問題点: Snappoint 入りません

警告アイコンを表示する場合は![Snappoint 警告アイコン](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Snappoint 警告アイコン")正規 snappoint アイコンではなく、snappoint とし、snappoint が入っていません。

![Snappoint の電源が入らない](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint が点灯していません。")

これらの手順を実行します。

1. ビルドし、配置、app.isua1 に使用されたソース コードの同じバージョンであることを確認します。 展開に適切なシンボルを読み込むことを確認してください。 これを行うには、表示、**モジュール**ウィンドウは、スナップショットのデバッグ中し、シンボル ファイルを示す列が .pdb ファイルをデバッグするモジュールを読み込むことを確認します。 スナップショット デバッガーが自動的にダウンロードして、実際の展開記号を使用して試してみることに注意してください。

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>問題点: シンボルが読み込まれないスナップショットを開く

次のウィンドウが表示されたら、シンボルが読み込まれませんでした。

![シンボルが読み込まれない](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "シンボルが読み込まれない")

これらの手順を実行します。

- クリックして、**シンボルの設定を変更しています.** このページにリンクします。 **デバッグ > シンボル**設定、シンボルのキャッシュ ディレクトリを追加します。 スナップショットのデバッグ シンボル パスが設定された後に再起動します。

   記号、またはプロジェクトで利用可能な .pdb ファイルは、アプリのサービスの展開と一致しなければなりません。 ほとんどの配置 (Visual Studio]、[CI/CD VSTS または Kudu での展開など) に沿って、シンボル ファイルをアプリ サービスに発行されます。 シンボルのキャッシュ ディレクトリを設定すると、これらのシンボルを使用する Visual Studio が有効になります。

   ![設定をシンボル](../debugger/media/snapshot-troubleshooting-symbol-settings.png "シンボルの設定")

- または、組織では、シンボル サーバーを使用してまたは別のパスのシンボルを削除は、シンボルの設定を使用して、展開に適切なシンボルを読み込みます。

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>問題点: Cloud Explorer で「スナップショット デバッガーのアタッチ」オプションが表示できません。

これらの手順を実行します。

- スナップショットのデバッガー コンポーネントがインストールされていることを確認してください。 Visual Studio インストーラー を開き、確認、**スナップショット デバッガー**コンポーネントを Azure のワークロードでします。
- アプリがサポートされていることを確認してください。 現時点では、ASP.NET だけ (4.6.1+) と Azure アプリのサービスに展開された ASP.NET Core (2.0 以降) アプリはサポートされています。

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>問題点: しか表示診断ツールでのスナップショットの調整

![Throttled snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "snappoint の調整")

これらの手順を実行します。

- スナップショットはごくわずかなメモリを消費するが、コミット チャージを持っています。 スナップショット デバッガー検出した場合、サーバーが大量のメモリ負荷の下では、スナップショットがかかりますされません。 スナップショットのデバッガー セッションを停止してから再試行では、既にキャプチャしたスナップショットを削除できます。

## <a name="known-issues"></a>既知の問題

- スナップショットは、同じ App Service に対して複数の Visual Studio クライアントでデバッグは現在サポートされていません。
- Roslyn IL 最適化は ASP.NET Core プロジェクトに完全にサポートされていません。 ASP.NET Core プロジェクトでは、いないことができますをいくつかの変数を参照してください。 または、条件付きステートメントでいくつかの変数を使用します。 
- 特別な変数など*$FUNCTION*または*$CALLER*、条件ステートメントやプロジェクトの ASP.NET Core logpoints で評価されることはできません。
- スナップショットのデバッグはアプリのサービスでは動作しません[ローカル キャッシュ](/azure/app-service/app-service-local-cache)オンにします。
- スナップショットの API アプリのデバッグは現在サポートされていません。

## <a name="site-extension-upgrade"></a>サイト拡張機能のアップグレード

スナップショットのデバッグと Application Insights は、サイトのプロセスに読み込まれ、アップグレード中にファイル ロック問題が発生する ICorProfiler によって異なります。 この処理を実稼働サイトのダウン時間がないことを確認することをお勧めします。

- 作成、[デプロイ スロット](/azure/app-service/web-sites-staged-publishing)アプリ サービス内およびスロットには、サイトを展開します。
- Visual Studio で、クラウド エクスプ ローラーとは、Azure ポータルから、運用スロットをスワップします。
- スロット サイトを停止します。 すべてのインスタンスからサイト w3wp.exe プロセスを強制終了するまで数秒かかります。
- Kudu サイトまたは Azure ポータルから、スロットのサイト拡張機能のアップグレード (*アプリ サービスのブレード > 開発ツール > 拡張子 > 更新*)。
- スロット サイトを開始します。 もう一度ウォーム アップするサイトにアクセスすることをお勧めします。
- 運用スロットをスワップします。

## <a name="see-also"></a>関連項目

[Visual Studio でのデバッグ](../debugger/index.md)  
[スナップショットのデバッガーを使用してライブの ASP.NET アプリをデバッグします。](../debugger/debug-live-azure-applications.md)  
[スナップショットのデバッグに関する FAQ](../debugger/debug-live-azure-apps-faq.md)  
