---
title: スナップショットのデバッグに関する FAQ |Microsoft ドキュメント
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8547c14cfd8a59d775c909edb06e3542b18710c8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>よく寄せられる質問のスナップショットは、Visual Studio でデバッグ

スナップショットのデバッガーを使用してライブの Azure アプリケーションのデバッグ時に生じる可能性があります質問の一覧を次に示します。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>スナップショットの取得のパフォーマンス コストとは何ですか。

スナップショット デバッガーでは、アプリのスナップショットをキャプチャ、したときに、アプリの処理のフォークされ、分岐したコピーを中断します。 スナップショットをデバッグするときに分岐したコピー プロセスをデバッグします。 このプロセスは 10 ~ 20 ミリ秒のみを受け取りますが、; アプリの完全なヒープではコピーされません。代わりに、ページのテーブルのみをコピーし、書き込み時にコピーするページを設定します。 場合は、ヒープの変更で、アプリのオブジェクトの一部をそれぞれ専用のページがコピーされます。 各スナップショットは、(ほとんどのアプリのキロバイト数百) のオーダー非常に小さいインメモリ コストをそのためになります。 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>スケール アウト Azure App Service (を探すアプリの複数のインスタンス) がある場合の対処方法

アプリの複数のインスタンスがある場合は、snappoints すべて 1 つのインスタンスに適用されます。 指定された条件とヒットする最初の snappoint だけでは、スナップショットを作成します。 複数の snappoints があれば、それ以降のスナップショットは最初のスナップショットを作成したものと同じインスタンスから取得されます。 出力ウィンドウに送る Logpoints では、logpoints アプリケーション ログに送信されるすべてのインスタンスからメッセージを送信するときに、1 つのインスタンスからのメッセージはだけ表示されます。 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>スナップショットのデバッガーがシンボルを読み込む方法

スナップショット デバッガーは対応するシンボル アプリケーションか、ローカルにあるまたは (埋め込み Pdb は現在サポートされていません)、Azure App Service にデプロイすることが必要です。 スナップショットのデバッガーは、Azure App Service からシンボルを自動的にダウンロードします。 Visual Studio 2017 時点では、Azure App Service にも展開するバージョン 15.2 は、アプリのシンボルを展開します。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>スナップショットのデバッガーは、アプリケーションのリリース ビルドに対して機能しますか。

はい - スナップショット デバッガーはリリース ビルドに対して機能するためのものです。 関数で、snappoint が配置されると、デバッグ可能になります、デバッグ バージョンに戻す、関数が再コンパイルされます。 スナップショット デバッガーを停止すると、関数は、リリース ビルドに返されます。 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>実稼働アプリケーションで副作用が発生 logpoints ことができますか。

いいえ - アプリを追加するすべてのログ メッセージは実質的に評価されます。 アプリケーションで、副作用とことはできません。 ただし、一部のネイティブ プロパティは logpoints でアクセスできない可能性があります。 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>サーバーに負荷がかかる場合、スナップショットのデバッガーは動作しますか。

はい、スナップショットのデバッグは、負荷の下でサーバーを操作できます。 スナップショット デバッガーは調整して、状況でのスナップショットをキャプチャしませんが、サーバー上の空きメモリの不足量。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>スナップショットのデバッガーのアンインストール方法

スナップショットのデバッガーのサイト拡張機能をアンインストールするには、次の手順で、App Service で。

1. アプリ サービスをオフにする Visual Studio または Azure ポータルでクラウド エクスプ ローラーを使用するか。
1. App Service の Kudu サイトに移動 (つまり、yourappservice **。scm**. azurewebsites.net) に移動して**拡張機能をサイト**です。
1. 削除するスナップショットのデバッガーのサイト拡張機能にある [X] をクリックします。

## <a name="see-also"></a>関連項目

[Visual Studio でのデバッグ](../debugger/index.md)  
[スナップショットのデバッガーを使用してライブの ASP.NET アプリをデバッグします。](../debugger/debug-live-azure-applications.md)  
[スナップショットのデバッグのトラブルシューティングと既知の問題](../debugger/debug-live-azure-apps-troubleshooting.md)
