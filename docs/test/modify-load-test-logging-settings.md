---
title: ロード テストのログ設定
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: e00f31dac1cf6b5ac329e51040027e94d4813dcb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036408"
---
# <a name="modify-load-test-logging-settings"></a>ロード テストのログ設定の変更

完了したロード テストの結果には、テスト対象コンピューターから定期的にログに収集されたパフォーマンス カウンター サンプルとエラー情報が含まれています。 パフォーマンス カウンター サンプルの多くは、ロード テストの実行中に収集されます。 収集されるパフォーマンス データの量は、実行の長さ、サンプリング間隔、テストするコンピューターの数、および収集対象のカウンターの数によって異なります。 大規模なロード テストでは、収集されるパフォーマンス データ量が数ギガバイトになることも珍しくありません。そのため、データをログに保存する間隔の変更を考慮する必要があります。 「[テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)」を参照してください。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*テスト コントローラー*は、テストの実行中に収集されたすべてのロード テスト サンプル データをデータベース ログにスプールします。 タイミング詳細やエラー詳細などの追加データは、テストの完了時にデータベースに読み込まれます。

|タスク|関連するトピック|
|-|-----------------------|
|**ロード テスト失敗時のログの保存:** ロード テストが失敗するたびにテスト ログを保存するかどうかも指定できます。|-   [方法:テスト ログにテストの失敗を記録するかどうかを指定する](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**ログ ファイルの最大サイズの設定:** テスト コントローラー サービスと関連付けられている XML 構成ファイルを編集して、ログ ファイルの最大ファイル サイズを指定できます。|[方法: ログ ファイルの最大サイズを指定する](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="see-also"></a>関連項目

- [ロード テストの実行設定の構成](../test/configure-load-test-run-settings.md)