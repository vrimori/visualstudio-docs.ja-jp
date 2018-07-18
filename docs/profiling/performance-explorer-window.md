---
title: '[パフォーマンス エクスプローラー] ウィンドウ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f27d1436aaeb0ec75876edf9119dff93f7539483
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31582112"
---
# <a name="performance-explorer-window"></a>[パフォーマンス エクスプローラー] ウィンドウ

Visual Studio IDE の **[パフォーマンス エクスプローラー]** ウィンドウでは、Visual Studio のプロファイル ツールを使用してパフォーマンス セッションを構成および開始することができます。

## <a name="performance-explorer-toolbar"></a>パフォーマンス エクスプローラーのツール バー

**パフォーマンス エクスプローラー**のツール バーでは以下のオプションを使用できます。

- **パフォーマンス ウィザードの起動** - パフォーマンス ウィザードを表示し、[パフォーマンス エクスプローラー] ウィンドウに新しいパフォーマンス セッションを追加します。

- **新しいパフォーマンス セッション** - 空のパフォーマンス セッションを [パフォーマンス エクスプローラー] ウィンドウに追加します。

- **起動** - **[起動]** コマンド ボタン リストでは、ターゲット アプリケーションを開始する際に、プロファイリングを即時に有効にすること (**プロファイルを使用して起動**) も、プロファイリングを中断しておくこと (**プロファイルを一時停止して起動**) もできます。

- **メソッド** - セッションのプロファイル方法をサンプリングにするか、インストルメンテーションにするかを指定します。

- **停止** - ターゲット アプリケーションとプロファイラーを即時に終了します。

- **アタッチ/デタッチ** - **[プロファイラーをプロセスにアタッチします]** ダイアログ ボックスを表示し、プロファイラーをアタッチする実行中のプロセスを選択します。

## <a name="performance-explorer-window"></a>[パフォーマンス エクスプローラー] ウィンドウ

**[パフォーマンス エクスプローラー]** ウィンドウには、1 つ以上のパフォーマンス セッションのバイナリおよびレポート データ ファイルを表示するツリー コントロールが表示されます。

- **セッション名** - ツリー コントロールのルートには、セッションの名前が含まれます。 セッション名を右クリックし、セッション プロパティを設定するか、ターゲット アプリケーションおよびプロファイラーを開始します。

- **ターゲット** - セッションでプロファイリングされるバイナリの名前を表示します。 **[ターゲット]** を右クリックし、バイナリ、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト、Web サイトを追加または削除します。 ターゲット名を右クリックし、個々のバイナリのプロパティを設定します。

- **レポート** - セッションに対して生成されるプロファイラー データ ファイルの名前を表示します。 **[レポート]** を右クリックし、既存のレポートの追加、または 2 つのプロファイラー データ ファイルの比較を行います。 レポート名を右クリックし、プロファイラー データ ファイルを開くか、削除するか、エクスポートします。

## <a name="see-also"></a>関連項目

[概要](../profiling/overviews-performance-tools.md)  
[パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)  
[データ コレクションの制御](../profiling/controlling-data-collection.md)