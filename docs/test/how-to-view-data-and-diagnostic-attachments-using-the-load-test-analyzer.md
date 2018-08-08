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
ms.openlocfilehash: 228f8306b803fcbd0e83e23e5b8e919dc2116c37
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382465"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>方法: ロード テスト アナライザーを使用してデータおよび診断の添付ファイルを表示する

ロード テストの実行前に、使用する診断アダプターおよびデータ アダプターを指定する、テストの設定を選択できます。 ロード テストの完了後は、結果の分析時に**ロード テスト アナライザー**を使用して、それらの診断アダプターとデータ アダプターの詳細を表示できます。 データと診断アダプターの詳細を表示するには、**ロード テスト アナライザー**のツール バーの **[データと診断の添付ファイルの表示]** ボタンを選択します。 たとえば、ロード テストの設定でシステム情報アダプターが構成されていた場合、ロード テストの実行時に使用されたコンピューターのシステム情報を表示できます。

![[診断データ アダプター添付ファイルの選択] ダイアログ ボックス](../test/media/load_adapterdialog.png)

また、ロード テストの設定に IntelliTrace アダプターを含めることもできます。 IntelliTrace アダプターを使用した場合は、**IntelliTrace の概要**ページを開くことができます。

![IntelliTrace の概要](../test/media/load_intellitrace.png)

詳細については、「[テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)」と [IntelliTrace データの収集](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)に関するページを参照してください。

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>ロード テスト アナライザーでロード テストのデータと診断の添付ファイルを表示するには

1.  ロード テストが完了するか、ロード テスト結果を開いたら、**ロード テスト アナライザー**のツール バーの **[データと診断の添付ファイルの表示]** をクリックします。

     **[診断データ アダプター添付ファイルの選択]** ダイアログ ボックスが表示されます。

2.  分析する診断データ アダプター添付ファイルを選択し、**[OK]** をクリックします。

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
