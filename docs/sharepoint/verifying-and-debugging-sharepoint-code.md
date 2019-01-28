---
title: 検証および SharePoint コードのデバッグ |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b57e07245631d37594d66ea7907b16efd817b2b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869490"
---
# <a name="verify-and-debug-sharepoint-code"></a>検証し、SharePoint コードのデバッグ
IntelliTrace と単体テストを使用すると、SharePoint ソリューションを簡単にデバッグして、ソリューション内の各メソッドが正常に動作することを確認できます。 その他の種類のプロジェクトと同じ手順に従って、Visual Studio での SharePoint プロジェクトのこれらの機能を使用できます。

## <a name="intellitrace"></a>Intellitrace
IntelliTrace を使用して、SharePoint ソリューションの現在の状態だけでなく、過去に発生したイベントおよび発生時のコンテキストも調べることができます。 SharePoint ソリューション内の目的のイベントが記録されたさまざまな時点に移動し、各時点の状態と変数値をレビューすることができます。 この動的ナビゲーションを使用すると、多数のブレークポイントを設定しなくても、すばやく簡単に SharePoint ソリューションをデバッグできます。 デバッグ セッションを IntelliTrace ログに保存することもできます (*.iTrace*) ファイル、Visual Studio Enterprise では、後で開くし、ポスト クラッシュ デバッグを実行します。 *.ITrace*ファイルに、エラーの原因をより簡単に理解できるようにするタイミングと場所は、特定の SharePoint エラーが発生した、に関する詳細情報が含まれます。 内の情報、 *.iTrace*ファイルは、Unified Logging System (ULS) SharePoint で作成する完全なエラー ログのサブセットです。 この情報には、ユーザー プロファイルがいつ開かれたか、閉じられたか、SharePoint プロジェクト内のプロパティがいつ読み込まれたか、読み取られたか、変更されたかなど、SharePoint 固有のイベントが含まれています。 IntelliTrace でどのイベントを記録するか、構成することもできます。 詳細については、「[保存された IntelliTrace データの使用](../debugger/using-saved-intellitrace-data.md)」を参照してください。

SharePoint でエラーが発生した場合、エラー ダイアログ ボックスには、そのエラーの "相関 ID" 識別子が表示されます。 記載されているイベントから相関 Id を取得することも、 *.iTrace*ファイル。 指定した相関 ID で発生したイベントのすべての一覧を表示するで ID を入力することができます、 **Analysis** IntelliTrace の概要 ページのセクション。 このセクションでは、発生したイベントの名前のみを表示するか、イベントの名前と共に、関数名、終了/エントリ ポイント、パラメーター、戻り値などの呼び出し情報を表示するかを選択できます。

選択して、IntelliTrace で Visual Studio イベントを取得できます、 **F5**キー。 ただし、SharePoint 固有のイベントを取得するには、Microsoft Monitoring Agent を使用して、SharePoint ソリューションの IntelliTrace データを収集する必要があります。 このツールは、IntelliTrace データを収集し、作成 *.iTrace* Visual Studio の外部で展開されているアプリケーション用のファイル。 詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)と[IntelliTrace スタンドアロン コレクターを使用して](../debugger/using-the-intellitrace-stand-alone-collector.md)します。

## <a name="unit-test"></a>単体テスト
単体テストを使用すると、コード内のエラーを検出しやすくなります。単体テストでは、テスト メソッドの内部にテスト コードを記述して、それを実行します。 これらのメソッドには、SharePoint オブジェクト モデルに基づいてプロジェクトのロジックと機能を検証するために使用できる、空の変数と Assert ステートメントが含まれます。 詳しくは、「[コードの単体テストUnit Test Your Code](../test/unit-test-your-code.md)」をご覧ください。

### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes フレームワークのサポート
SharePoint プロジェクトは Microsoft Fakes をサポートしています。これは、.NET Framework に基づいたアプリケーションでデリゲート ベースのテスト スタブと shim を作成できる分離フレームワークです。 Fakes フレームワークを使用することにより、単体テスト内でダミー実装を作成、管理、および挿入できます。 これらのスタブと shim は環境から単体テストを分離します。 スタブを作成すると、オーバーライド可能なメソッドを持つインターフェイスまたは非シール クラスを使用するコードをテストできます。 shim を作成すると、静的またはオーバーライド可能なメソッドを持つシール クラスへの、ハードコーディングされた呼び出しを代替 shim 実装にリダイレクトすることができます。 また、スタブ型および shim 型のデリゲートを使用して、個々のスタブ メンバーの動作を動的にカスタマイズすることもできます。 詳細については、次を参照してください。[テスト コードの分離 Microsoft Fakes で](../test/isolating-code-under-test-with-microsoft-fakes.md)します。

## <a name="related-articles"></a>関連記事

|タイトル|説明|
|-----------|-----------------|
|[IntelliTrace](../debugger/intellitrace.md)|IntelliTrace を使用して Visual Studio ソリューションをより簡単にデバッグする方法について説明します。|
|[チュートリアル: IntelliTrace を使用して SharePoint アプリケーションをデバッグします。](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|IntelliTrace を使用して SharePoint プロジェクトのコード エラーを検出する方法について説明します。|
|[コードの単体テスト](../test/unit-test-your-code.md)|単体テストを使用してコードの論理エラーを検出する方法について説明します。|

## <a name="see-also"></a>関連項目

- [コード品質の向上](../test/improve-code-quality.md)