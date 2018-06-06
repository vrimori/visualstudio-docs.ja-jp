---
title: スレッドおよびプロセスの同時実行データの収集 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 424675726dd91664923cde0a3a5ad5573d51b4d5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34548338"
---
# <a name="collect-thread-and-process-concurrency-data"></a>スレッドとプロセスの同時実行データの収集

Visual Studio のプロファイリング ツールの同時実行プロファイル メソッドを使用すると、プロファイリング対象のアプリケーションの機能がリソースへのアクセスを待機するすべての同期イベントに関する情報を含むリソース競合データを収集できます。

同時実行プロファイル メソッドは、次のいずれかの手順を使用して指定できます。

- プロファイリング ウィザードの最初のページで **[同時実行]** をクリックします。
- パフォーマンス セッションの [プロパティ] ダイアログ ボックスの **[全般]** ページで、**[同時実行]** をクリックします。
- **パフォーマンス エクスプローラー**のツールバーで、**[メソッド]** 一覧の **[同時実行]** をクリックします。

## <a name="common-tasks"></a>一般的なタスク

追加のオプションを、*[パフォーマンス セッション]* の **[プロパティ ページ]** ダイアログ ボックスで指定できます。 このダイアログ ボックスを開くには:

- **パフォーマンス エクスプローラー**で、パフォーマンス セッション名を右クリックして **[プロパティ]** をクリックします。

次の表の各タスクでは、同時実行メソッドを使用してプロファイリングを実行する際に、*[パフォーマンス セッション]* の**[プロパティ ページ]** ダイアログ ボックスで指定できるオプションについて説明しています。

|タスク|関連するコンテンツ|
|----------|---------------------|
|**[全般]** ページで、生成されるプロファイリング データ (.vsp) ファイルの名前付けの詳細を指定します。|- [方法: パフォーマンス データ ファイル名のオプションを設定する](../profiling/how-to-set-performance-data-file-name-options.md)|
|コード ソリューション内に複数の .exe プロジェクトがある場合は、**[起動]** ページで、開始するアプリケーションを指定します。|- [方法: 開始するバイナリを指定する](../profiling/how-to-specify-the-binary-to-start.md)|
|**[階層の相互作用]** ページで、プロファイリング実行に ADO.NET 呼び出しデータを追加します。|- [階層相互作用データを収集する](../profiling/collecting-tier-interaction-data.md)|
|**[Windows カウンター]** ページで、プロファイリング データをマークとして追加するオペレーティング システムのパフォーマンス カウンターを 1 つ以上指定します。|- [方法: Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)|
|アプリケーション モジュールで複数のバージョンを使用する場合は、**[詳細]** ページで、プロファイリングする .NET Framework ランタイムのバージョンを指定します。 既定では、最初に読み込まれたバージョンがプロファイリングされます。|- [方法: .NET Framework ランタイムを指定する](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|