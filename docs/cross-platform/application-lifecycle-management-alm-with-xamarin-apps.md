---
title: Xamarin アプリを使用したアプリケーション ライフサイクル管理 (ALM) | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 0cce9882add1443c2d9187d65b26a25081aac75b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634942"
---
# <a name="devops-with-xamarin-apps"></a>Xamarin アプリを使用した DevOps

Xamarin では、Android、iOS、および Windows を対象とするクロスプラットフォームのモバイル アプリを、C#、.NET、および Visual Studio を使用して作成することができます。 Xamarin を利用すると、コードの大部分をプラットフォーム間で共有し、プラットフォーム固有にする必要のあるコードをごく一部に抑えることができます。 Xamarin 自体の詳細については、「[Visual Studio と Xamarin](../cross-platform/visual-studio-and-xamarin.md)」を参照してください。

最新のプラットフォーム向けのアプリ開発には、コードを記述するだけでなく、それ以外の多くのアクティビティが関係します。 これらのアクティビティは、アプリの完全なライフサイクルの中で DevOps (開発 + 運用) 期間になされるものあり、たとえば、作業のアジャイルな計画と追跡、コードの設計と実装、ソース コード リポジトリの管理、ビルドの実行、継続的に実行されるインテグレーションと展開の管理、テスト (単体テストと UI テストを含む)、開発環境と運用環境の両方におけるさまざまな形式の診断の実行、製品利用統計情報と分析によるアプリのパフォーマンスとユーザー動作のリアルタイムな監視などがあります。

Visual Studio、Visual Studio Team Services、Team Foundation Server は、さまざまな DevOps 機能を提供しています。 これらの多くは、クロスプラットフォームのプロジェクトに完全に適用されます。 Xamarin アプリでは特にそう言えます。C# と .NET で構築し、いくつかの DevOps ツールはそれらを中心に構築されているからです。 その他のツールでは、ビルド環境およびランタイム環境との緊密な統合が必要です。 Xamarin アプリは Windows 以外のプラットフォームでも実行でき、.NET の Mono 実装を使用しているため、Xamarin では特定の必要に合わせて専門ツールが提供されます。

次の表は、Xamarin プロジェクトで動作する Visual Studio の DevOps 機能と制限がある機能を示しています。 各機能そのものの詳細については、リンク先のドキュメントを参照してください。

## <a name="agile-tools"></a>アジャイル ツール

参照リンク: **[アジャイル ツールとアジャイル プロジェクト管理の概要](/vsts/work/backlogs/overview?view=vsts)**

一般的なコメント: すべての計画機能と追跡機能は、プロジェクトの種類とコーディング言語には依存しません。

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|バックログとスプリントの管理|[はい]||
|作業の追跡|[はい]||
|チーム ルーム コラボレーション|[はい]||
|かんばんボード|[はい]||
|進行状況のレポートと視覚化|[はい]||

## <a name="modeling"></a>モデリング

参照リンク: **[アーキテクチャの分析とモデル化](../modeling/analyze-and-model-your-architecture.md)**

デザイン機能は、コーディング言語に依存しないか、または C# のような .NET 言語と一緒に機能します。 コードに関連する側面については「[ソフトウェア開発におけるアーキテクチャ図とモデル図の役割](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools)」を参照してください。

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|シーケンス図|[はい]||
|依存関係グラフ|[はい]||
|呼び出し階層|[はい]||
|クラス デザイナー|[はい]||
|アーキテクチャ エクスプローラー|[はい]||
|UML 図 (ユース ケース、アクティビティ、クラス、コンポーネント、シーケンス、および DSL)|[はい]||
|レイヤー図|[はい]||
|レイヤー検証|[はい]||

## <a name="code"></a>コード

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|[Team Foundation バージョン管理](/vsts/tfvc/overview?view=vsts) または Visual Studio Team Services を使用|[はい]||
|[Team Services で Git を使用した作業の開始](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|[はい]||
|[コード品質の向上](../test/improve-code-quality.md)|[はい]||
|[コード変更およびその他の履歴の検索](../ide/find-code-changes-and-other-history-with-codelens.md)|[はい]|ただし、実行時まで実装が解決しない、プラットフォームに固有の境界をまたぐ場合を除きます。|
|[コード マップを使用してアプリケーションをデバッグする](../modeling/use-code-maps-to-debug-your-applications.md)|[はい]||

## <a name="build"></a>ビルド

参照リンク: **[ビルドとリリース](/vsts/pipelines/index?view=vsts)**

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|オンプレミス TFS サーバー|[はい]|ビルド コンピューターに Xamarin がインストールされている必要があります。iOS 用にビルドするには、OSX コンピューターにリンクできる必要があります。 「[TFVC の使用](/vsts/tfvc/overview?view=vsts)」を参照してください。|
|Visual Studio Team Services にリンクされたオンプレミスのビルド サーバー|[はい]|手順については、「[Build and release agents](/vsts/pipelines/agents/agents?view=vsts)」 (ビルド エージェントとリリース エージェント) を参照してください。|
|Visual Studio Team Services のホスト コントローラー サービス|[はい]|「[Build your Xamarin app](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)」 (Xamarin アプリのビルド) を参照してください。|
|事前スクリプトと事後スクリプトによるビルド定義|[はい]||
|継続的な統合 (ゲート チェックインを含む)|[はい]|Git としての TFVC へのゲート チェックインのみ、チェックイン モデルではなく、プル要求モデルで機能します。|

## <a name="test"></a>テスト

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|テストの計画、テスト ケースの作成、およびテスト スイートの編成|[はい]||
|手動テスト|[はい]||
|テスト マネージャー (テストの記録と再生)|[はい]|Windows デバイスと Android エミュレーター (Visual Studio からのみ)。 [Xamarin Test Recorder](/appcenter/test-cloud/uitest/) を使用すると、すべてのデバイスの記録が可能です。|
|コード カバレッジ|N/A||
|[コードの単体テスト](../test/unit-test-your-code.md)|[はい]|Windows と Android を対象にする場合は、組み込みの MSTest ツールを使用できます。 Windows、Android、および iOS で単体テストを実行するには、Xamarin では NUnit が推奨されています。 「[TFVC の使用](/vsts/tfvc/overview?view=vsts)」を参照してください。|
|[UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)|Windows のみ|Visual Studio の UI テスト レコーダーは Windows のみです。 すべてのプラットフォームについては、[Xamarin.UITest](/appcenter/test-cloud/uitest/) を参照してください。|

## <a name="improve-code-quality"></a>コード品質の向上

参照リンク: **[コードの品質の向上](../test/improve-code-quality.md)**

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|[マネージド コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|[はい]||
|[コード クローン検出を使用した重複コードの検出](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|[はい]||
|[マネージド コードの複雑さと保守性の測定](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|[はい]||
|[パフォーマンス エクスプローラー](../profiling/performance-explorer.md)|×|代わりに、Xamarin Studio の [Xamarin プロファイラー](/xamarin/cross-platform/deploy-test/) を使用します。 Xamarin プロファイラーは現在プレビュー期間中であり、Windows を対象にした場合はまだ動作しないことに注意してください。|
|[.Net Framework のメモリ分析の問題](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|×|Visual Studio ツールには、プロファイリング用の Mono フレームワークへのフックはありません。|

## <a name="release-management"></a>リリース管理

参照リンク: **[Build and Release in VSTS and TFS (VSTS と TFS のビルドとリリース)](/vsts/pipelines/overview?view=vsts)**

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|リリース プロセスの管理|[はい]||
|スクリプトによるサイドローディング用のサーバーへの配置|[はい]||
|アプリ ストアへのアップロード|Partial|一部のアプリ ストアに対して、このプロセスを自動化することができる拡張機能が使用できます。  たとえば、[Google Play の拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play)については、[Visual Studio Team Services の拡張機能](https://marketplace.visualstudio.com/VSTS)を参照してください。|

## <a name="monitor-with-hockeyapp"></a>HockeyApp による監視

参照リンク: **[HockeyApp による監視](https://www.hockeyapp.net/features/)**

|機能|Xamarin でサポートされているかどうか|その他のコメント|
|-------------|----------------------------|-------------------------|
|クラッシュ分析、製品利用統計情報、およびベータ版の配布|[はい]||