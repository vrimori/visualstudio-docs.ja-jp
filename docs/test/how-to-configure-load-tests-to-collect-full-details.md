---
title: Visual Studio でのロード テストの仮想ユーザーの完全な詳細情報を収集する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 70930a09f01450d59b44678ebd26d7e742af7294
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379626"
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>方法: 詳細情報を収集するようにロード テストを構成してテスト結果で仮想ユーザー アクティビティを有効にする

ロード テストの**仮想ユーザー アクティビティ チャート**を使用するには、すべての詳細情報を収集するようにロード テストを構成する必要があります。 ロード テストをこのように構成するには、ロード テストに関連付けられた **[タイミングの詳細ストレージ]** プロパティを **[すべての個別詳細]** に設定します。 このモードでは、ロード テストによってすべてのテスト、ページ、およびトランザクションに関する詳細情報が収集されます。

 以前のバージョンの Visual Studio ロード テストからプロジェクトをアップグレードする場合は、以降に示す手順に従ってすべての詳細情報の収集を有効にしてください。

 **[タイミングの詳細ストレージ]** プロパティの **[すべての個別の詳細]** 設定は、次のオプションのうちいずれかに設定できます。

-   **[すべての個別詳細]:** 各テスト、各トランザクション、テスト中に発行された各ページについて、個々のタイミング データを収集し、保存します。

    > [!NOTE]
    > ロード テストの結果に仮想ユーザーに関するデータを表示するには、**[すべての個別詳細]** を選択する必要があります。

-   **[なし]:** 個々のタイミング詳細情報は収集しません。 ただし、平均値は表示されます。

-   **[統計のみ]:** 個々のタイミング データを、パーセンタイル データの形式だけで保存します。 これにより、領域リソースを節約できます。

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>ロード テストで [タイミングの詳細ストレージ] プロパティを構成するには

1.  **ロード テスト エディター**で、ロード テストを開きます。

2.  ロード テストで、**[実行設定]** ノードを展開します。

3.  構成する実行設定 (**[Run Settings1[Active]]** など) を選択します。

4.  **[プロパティ]** ウィンドウを開きます。 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。

5.  **[結果]** カテゴリの **[タイミングの詳細ストレージ]** プロパティを選択し、**[すべての個別詳細]** を選択します。

     **[タイミングの詳細ストレージ]** プロパティを **[すべての個別詳細]** に設定すると、ロード テストを実行して**仮想ユーザー アクティビティ チャート**を表示できるようになります。 詳細については、[ロード テスト中に仮想ユーザーが行っている操作を分析する方法](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [詳細ビューでの仮想ユーザー アクティビティの分析](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [チュートリアル: 仮想ユーザー アクティビティ チャートを使用した問題の特定](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)