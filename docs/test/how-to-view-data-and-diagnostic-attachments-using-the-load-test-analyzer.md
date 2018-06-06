---
title: Visual Studio でロード テストのためのデータおよび診断の添付ファイルを表示する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 525f4a1d11cd4026410baf696b4593daf2595e12
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751366"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>方法: ロード テスト アナライザーを使用してデータおよび診断の添付ファイルを表示する

ロード テストの実行前に、使用する診断アダプターおよびデータ アダプターを指定する、テストの設定を選択できます。 ロード テストの完了後は、結果の分析時にロード テスト アナライザーを使用して、それらの診断アダプターとデータ アダプターの詳細を表示できます。 データと診断アダプターの詳細を表示するには、ロード テスト アナライザーのツール バーの **[データと診断の添付ファイルの表示]** をクリックします。 たとえば、ロード テストの設定でシステム情報アダプターが構成されていた場合、ロード テストの実行時に使用されたコンピューターのシステム情報を表示できます。

![[診断データ アダプター添付ファイルの選択] ダイアログ ボックス](../test/media/load_adapterdialog.png)

また、ロード テストの設定に IntelliTrace アダプターを含めることもできます。 IntelliTrace アダプターを使用した場合は、IntelliTrace の概要ページを開くことができます。

![IntelliTrace の概要](../test/media/load_intellitrace.png)

詳細については、「[Collect Diagnostic Information Using Test Settings](../test/collect-diagnostic-information-using-test-settings.md)」(テスト設定を使用して診断を収集する) と [IntelliTrace データの収集](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)に関するページを参照してください。

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>ロード テスト アナライザーでロード テストのデータと診断の添付ファイルを表示するには

1.  ロード テストが完了するか、ロード テスト結果を開いたら、ロード テスト アナライザーのツール バーの **[データと診断の添付ファイルの表示]** をクリックします。

     **[診断データ アダプター添付ファイルの選択]** ダイアログ ボックスが表示されます。

2.  分析する診断データ アダプター添付ファイルを選択し、**[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)