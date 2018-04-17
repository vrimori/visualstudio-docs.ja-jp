---
title: Visual Studio でロード テストのためのデータおよび診断の添付ファイルを表示する | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 5d955412195a32a69e069ccac2b40456a9ffb986
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>方法: ロード テスト アナライザーを使用してデータおよび診断の添付ファイルを表示する

ロード テストの実行前に、使用する診断アダプターおよびデータ アダプターを指定する、テストの設定を選択できます。 ロード テストの完了後は、結果の分析時にロード テスト アナライザーを使用して、それらの診断アダプターとデータ アダプターの詳細を表示できます。 データと診断アダプターの詳細を表示するには、ロード テスト アナライザーのツール バーの **[データと診断の添付ファイルの表示]** をクリックします。 たとえば、ロード テストの設定でシステム情報アダプターが構成されていた場合、ロード テストの実行時に使用されたコンピューターのシステム情報を表示できます。

![[診断データ アダプター添付ファイルの選択] ダイアログ ボックス](../test/media/load_adapterdialog.png "Load_AdapterDialog")

また、ロード テストの設定に IntelliTrace アダプターを含めることもできます。 IntelliTrace アダプターを使用した場合は、IntelliTrace の概要ページを開くことができます。

![IntelliTrace の概要](../test/media/load_intellitrace.png "Load_IntelliTrace")

詳細については、「[Collect Diagnostic Information Using Test Settings](../test/collect-diagnostic-information-using-test-settings.md)」(テスト設定を使用して診断を収集する) と [IntelliTrace データの収集](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)に関するページを参照してください。

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>ロード テスト アナライザーでロード テストのデータと診断の添付ファイルを表示するには

1.  ロード テストが完了するか、ロード テスト結果を開いたら、ロード テスト アナライザーのツール バーの **[データと診断の添付ファイルの表示]** をクリックします。

     **[診断データ アダプター添付ファイルの選択]** ダイアログ ボックスが表示されます。

2.  分析する診断データ アダプター添付ファイルを選択し、**[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)