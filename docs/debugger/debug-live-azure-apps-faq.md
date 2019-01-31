---
title: スナップショットのデバッグに関する FAQ |Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1465d7ee664b1c1d534350be19e4c067a74cb79
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024501"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>よく寄せられる質問の Visual Studio でスナップショットのデバッグ

スナップショット デバッガーを使用して、ライブ Azure アプリケーションのデバッグ時に生じる可能性がありますの質問の一覧を示します。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>スナップショットの作成のパフォーマンス コストとは何ですか。

スナップショット デバッガーは、アプリのスナップショットをキャプチャする場合は、アプリのプロセスをフォークとフォークしたコピーを中断します。 スナップショットをデバッグするときに、プロセスのフォークしたコピーをデバッグします。 このプロセスは 10 ~ 20 ミリ秒しかかかりませんが、アプリの完全なヒープではコピーされません。 代わりに、ページのテーブルのみをコピーし、設定ページの書き込み時にコピーします。 ヒープの変更、アプリのオブジェクトの一部には場合、それぞれのページはコピーされます。 したがって、各スナップショットには、少ないメモリ内 (ほとんどのアプリのキロバイト数百) の順序があります。 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>スケール アウトされた Azure App Service (アプリの複数のインスタンス) があるとすると、どうなりますか。

アプリの複数のインスタンスがある場合は、スナップ ポイントすべて 1 つのインスタンスに適用されます。 指定された条件とヒットする最初のスナップ ポイントのみでは、スナップショットを作成します。 を複数個のスナップ ポイントがある場合は、最初のスナップショットを作成する同じインスタンスからそれ以降のスナップショットが取得されます。 出力ウィンドウに送信されるログポイント ログポイント アプリケーション ログに送信されるすべてのインスタンスからメッセージを送信するときに 1 つのインスタンスからのメッセージがのみ表示されます。 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>スナップショット デバッガーがシンボルを読み込む方法

スナップショット デバッガーでは、Azure App Service へのローカルまたはデプロイされたアプリケーションは対応するシンボルがあることが必要です。 (埋め込みの Pdb が現在サポートされていません。)スナップショット デバッガーは、Azure App Service からシンボルを自動的にダウンロードします。 Visual Studio 2017 バージョン 15.2 でも、Azure App Service に展開するアプリのシンボルを展開します。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>スナップショット デバッガーは、アプリケーションのリリース ビルドに対して動作しますか。

はい - スナップショット デバッガーは、リリース ビルドに対して機能するものです。 関数で、スナップ ポイントが配置されると、デバッグできるように、デバッグ バージョンに戻す、関数が再コンパイルされます。 スナップショット デバッガーを停止すると、関数は、リリース ビルドに返されます。 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>実稼働アプリケーションで副作用が発生ログポイントことができますか。

いいえ - アプリに追加するすべてのログ メッセージは実質的に評価されます。 すべての副作用は、アプリケーションでが発生することはできません。 ただし、いくつかのネイティブ プロパティをログポイントをアクセスできない可能性があります。 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>マイ サーバーは、負荷がある場合、スナップショット デバッガーは動作でしょうか。

はい、スナップショットのデバッグは、サーバー負荷の下で作業できます。 スナップショット デバッガーの調整し、状況でのスナップショットをキャプチャしませんが、サーバーで少量のメモリを解放します。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>スナップショット デバッガーのアンインストール方法

次の手順で、App Service では、スナップショット デバッガー サイト拡張機能をアンインストールできます。

1. Visual Studio または Azure portal で Cloud Explorer を使用するか、アプリをオフにするサービスを提供します。
1. App Service の Kudu サイトに移動します (つまり、yourappservice **。scm**. azurewebsites.net) に移動します**サイト拡張機能**します。
1. それを削除するスナップショット デバッガー サイト拡張機能にある [X] をクリックします。

## <a name="see-also"></a>関連項目

[Visual Studio でのデバッグ](../debugger/index.md)  
[スナップショット デバッガーを使用して、ライブ ASP.NET アプリをデバッグします。](../debugger/debug-live-azure-applications.md)  
[スナップショットのデバッグのトラブルシューティングと既知の問題](../debugger/debug-live-azure-apps-troubleshooting.md)
