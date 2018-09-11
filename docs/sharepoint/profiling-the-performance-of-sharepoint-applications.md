---
title: SharePoint アプリケーションのパフォーマンスのプロファイリング |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67623989fc8ff2bf2d44bc435a48db81fecb1fba
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282342"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>SharePoint アプリケーションのパフォーマンスをプロファイルします。

SharePoint アプリケーションの実行速度が遅いか効率的でない場合、Visual Studio のプロファイル機能を使用して、問題のあるコードやその他の要素を特定できます。 ロード テスト機能を使用すると、多数のユーザーがアプリケーションに同時にアクセスする場合など、ストレス下で SharePoint アプリケーションを実行する方法を決定できます。 Web パフォーマンス テストを実行すると、Web 上でのアプリケーションの実行方法を測定できます。 コード化された UI テストを使用すると、ユーザー インターフェイスを含め、SharePoint アプリケーション全体が適切に機能しているかどうかを確認できます。 これらのテストを一緒に使用すると、アプリケーションを配置する前にパフォーマンスの問題を識別するのに役立ちます。

## <a name="profile-tools-overview"></a>プロファイル ツールの概要

プロファイルとは、実行中のアプリケーションのパフォーマンス動作を観察および記録するプロセスのことです。 アプリケーションをプロファイルすると、ボトルネック、非効率的なコード、メモリ割り当ての問題など、アプリケーションの実行速度の低下または過度なメモリ消費を引き起こす問題を見つけることができます。 たとえば、プロファイルを使用すると、頻繁に呼び出され、アプリケーション全体のパフォーマンスを低下させる可能性があるコードのセグメントであるホットスポットをコード内で特定できます。 特定したホットスポットは、最適化するか除去します。

統合開発環境 (IDE: Integrated Development Environment) を使用すると、このようなパフォーマンスの問題を特定し検索できます。 SharePoint プロジェクトに対するこれらのツールの動作は、他の種類の Visual Studio プロジェクトに対する動作と同じです。 プロファイリング ツールのパフォーマンス ウィザードでは、指定したテストを使用するパフォーマンス セッションを作成できます。 パフォーマンス セッションは、1 つまたは複数のプロファイリング実行の結果と共に、アプリケーションからパフォーマンス情報を収集するために使用される構成データのセットです。 パフォーマンス セッションは、プロジェクト フォルダーに格納され、それらを表示することができます**パフォーマンス エクスプ ローラー**します。 詳細については、「[パフォーマンス収集方法について](/visualstudio/profiling/understanding-performance-collection-methods)」を参照してください。

アプリケーションでプロファイル分析を作成して実行すると、レポートにそのパフォーマンスに関する詳細情報が示されます。 このレポートには、一定期間における CPU 使用率のグラフ、階層関数の呼び出し履歴、コール ツリーなどの項目を含めることができます。 レポートの正確な内容は、サンプリング、インストルメンテーションなど、実行するテストの種類によって異なることがあります。 詳細については、次を参照してください。[プロファイリング ツールのレポートの概要](http://go.microsoft.com/fwlink/?LinkId=224689)します。

## <a name="performance-session-process"></a>パフォーマンス セッションのプロセス

アプリケーションのプロファイリングを行うには、最初に、プロファイリング ツールのパフォーマンス ウィザードを使用してパフォーマンス セッションを作成します。 メニュー バーで、**分析**、**パフォーマンス ウィザードの起動**します。 ウィザードの完了時に、必要なプロファイリング方法、プロファイリングするアプリケーションなど、パフォーマンス セッションに必要な情報を入力します。 詳細については、次を参照してください。[方法: Web サイトまたは Web アプリケーションを使用して、パフォーマンス ウィザードをプロファイル](http://go.microsoft.com/fwlink/?LinkId=224692)します。 また、コマンド ライン オプションを使用して、パフォーマンス セッションを設定および実行することもできます。 詳細については、次を参照してください。 [、プロファイリングからコマンドライン ツールを使用して](http://go.microsoft.com/fwlink/?LinkId=224703)します。 パフォーマンス セッションのすべての側面を手動で構成する場合は、「[方法: パフォーマンス セッションを手動でプロファイリング ツールを使用して作成](http://go.microsoft.com/fwlink/?LinkId=224691)です。 も、単体テストからこのパフォーマンス セッションを作成することができます、**テスト結果**ウィンドウで、単体テストのショートカット メニューを開き、選択し、**パフォーマンス セッションの作成**です。

パフォーマンス セッションを設定したら、セッションの構成が保存され、プロファイル データを提供するようにサーバーが構成されます。その後、アプリケーションが実行されます。 アプリケーションの使用中、パフォーマンス データがログ ファイルに書き込まれます。 パフォーマンス セッションは、「**パフォーマンス エクスプ ローラー**下、**ターゲット**フォルダー。 パフォーマンス セッションが終了すると、そのレポートが表示されます、**レポート**フォルダー**パフォーマンス エクスプ ローラー**します。 レポートを表示するでを開く**パフォーマンス エクスプ ローラー**します。 を表示またはパフォーマンス セッションのプロパティを構成するには、でショートカット メニューを開いて**パフォーマンス エクスプ ローラー**を選び、**プロパティ**します。 パフォーマンス セッションの特定のプロパティの詳細については、次を参照してください。[プロファイリング ツールのパフォーマンス セッションを構成する](http://go.microsoft.com/fwlink/?LinkId=224694)します。 パフォーマンス セッションの結果を解釈する方法については、次を参照してください。[プロファイリング ツール データの分析](http://go.microsoft.com/fwlink/?LinkId=224704)します。

## <a name="stress-test"></a>ストレス テスト

アプリケーションのストレスへパフォーマンスを分析するには、Visual Studio でロード テストと web パフォーマンス テストを作成します。 Visual Studio でロード テストを作成するときに、アプリケーションをテストするときに比較対象として使用する、シナリオと呼ばれる要素の組み合わせを指定します。 これらの要素には、ロード パターン、テスト ミックス モデル、テスト ミックス、ネットワーク ミックス、Web ブラウザー ミックスなどが含まれます。 ロード テスト シナリオには、単体テストと Web パフォーマンス テストの両方を含めることができます。

図 1: ロード テストの結果の例

![ロード テストの実行グラフ ビュー](../sharepoint/media/load-webgraphs.png "実行中のロード テスト グラフ ビュー")

Web パフォーマンス テストでは、エンド ユーザーが SharePoint アプリケーションとやり取りする方法をシミュレートします。 Web パフォーマンス テストを作成するには、ブラウザー セッションで HTTP 要求を記録することによって、またはを使用して、 **Web パフォーマンス テスト レコーダー**します。 Web 要求に表示されます、 **Web パフォーマンス テスト エディター**ブラウザー セッションが完了後します。 結果をデバッグできるよう、 **Web パフォーマンス テスト結果ビューアー**します。 使用して、web パフォーマンス テストをビルドすることができますも手動で、 **Web パフォーマンス テスト エディター**します。

## <a name="test-user-interfaces"></a>ユーザー インターフェイスをテストします。

コード化された UI テストでは、ユーザー インターフェイス (UI) を介して SharePoint アプリケーションが自動的に実行されます。 これらのテストでは、ボタン、メニューなどの UI コントロールが正しく動作するかどうかを確認します。 この種類のテストは、検証や他のロジックが Web ページなどの UI で実行されている場合に特に便利です。 また、コード化された UI テストを使用して、手動テストを自動化することもできます。 SharePoint アプリケーションのコード化された UI テストは、他の種類のアプリケーションのテストを作成するときと同じ方法で作成します。 詳細については、次を参照してください。[コード化された UI テストでの SharePoint 2010 アプリケーションのテスト](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)します。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[チュートリアル: SharePoint アプリケーションをプロファイリングします。](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|SharePoint アプリケーションのサンプリング プロファイル分析を実行する方法を示します。|
|[リリース前のアプリのパフォーマンス テスト](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|SharePoint アプリケーションのストレス テストに役立つロード テストを作成する方法について説明します。|
|[コードの単体テスト](/visualstudio/test/unit-test-your-code)|単体テストを使用してコードの論理エラーを検出する方法について説明します。|
|[コード化された UI テストを使用した SharePoint 2010 アプリケーションのテスト](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|SharePoint アプリケーションのユーザー インターフェイスをテストする方法について説明します。|

## <a name="see-also"></a>関連項目

[ビルドし、SharePoint ソリューションをデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)
[コードの品質の向上](/visualstudio/test/improve-code-quality)
