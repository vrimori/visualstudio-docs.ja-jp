---
ms.technology: vs-ai-tools
ms.openlocfilehash: f11a66fd06a2b0b3b23d35c3153c5dd26fab282e
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="view-recent-job-performance-and-details"></a>最近のジョブのパフォーマンスと詳細を表示する
ジョブが送信されたら、ジョブの一覧を表示して、ジョブの状態やジョブの期間などを確認することができます。

1. **サーバー エクスプローラー**で、特定の計算コンテキストを展開します。
1. **[ジョブ]** をダブルクリックします。
1. その計算コンテキストに送信されたジョブの一覧が表示されます。
1. 一覧内で特定の**ジョブ**を選択して詳細を確認します。

![ジョブの監視](media\job-details\monitor-jobs.png)

> Linux VM に送信されたジョブ履歴は /tmp ディレクトリ内の VM に格納されます。 したがって、VM が再起動されるたびにジョブ履歴はクリアされます。 ジョブ履歴を永続的に記録する場合は、Azure Machine Learning 内の計算コンテキストとして VM を構成してから、ジョブを Azure Machine Learning に送信します (ご利用の VM を計算コンテキストとして選択)。