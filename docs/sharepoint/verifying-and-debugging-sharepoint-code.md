---
title: "SharePoint コードのデバッグの検証と |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- unit testing [SharePoint development in Visual Studio]
- IntelliTrace [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, IntelliTrace
- SharePoint development in Visual Studio, unit testing
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d3717d3bee3665705ce39307b640e02a931cd75f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-and-debugging-sharepoint-code"></a>SharePoint コードの検証およびデバッグ
  IntelliTrace と単体テストを使用すると、SharePoint ソリューションを簡単にデバッグして、ソリューション内の各メソッドが正常に動作することを確認できます。 これらの機能は、他の種類のプロジェクトと同じ手順で、[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] の SharePoint プロジェクトに対して使用できます。  
  
## <a name="intellitrace"></a>[IntelliTrace]  
 IntelliTrace を使用して、SharePoint ソリューションの現在の状態だけでなく、過去に発生したイベントおよび発生時のコンテキストも調べることができます。 SharePoint ソリューション内の目的のイベントが記録されたさまざまな時点に移動し、各時点の状態と変数値をレビューすることができます。 この動的ナビゲーションを使用すると、多数のブレークポイントを設定しなくても、すばやく簡単に SharePoint ソリューションをデバッグできます。 また、デバッグ セッションを IntelliTrace ログ (.iTrace) ファイルに保存し、後でこのファイルを Visual Studio Ultimate で開いて、ポスト クラッシュ デバッグを実行できます。 .ITrace ファイルには、エラーの原因をより簡単に理解できるようにするタイミングと場所は、特定の SharePoint エラーが発生した、に関する詳細情報が含まれています。 .iTrace ファイルに含まれる情報は、SharePoint の Unified Logging System (ULS) で作成される完全なエラー ログのサブセットです。 この情報には、ユーザー プロファイルがいつ開かれたか、閉じられたか、SharePoint プロジェクト内のプロパティがいつ読み込まれたか、読み取られたか、変更されたかなど、SharePoint 固有のイベントが含まれています。 IntelliTrace でどのイベントを記録するか、構成することもできます。 詳細については、次を参照してください。[保存された IntelliTrace データを使用する](/visualstudio/debugger/using-saved-intellitrace-data)と[構成 IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)です。  
  
 SharePoint でエラーが発生した場合、エラー ダイアログ ボックスには、そのエラーの "相関 ID" 識別子が表示されます。 .iTrace ファイルに示されているイベントから相関 ID を取得することもできます。 特定の相関 id が発生したイベントのすべての一覧を表示するには、ID を入力することができます、 **Analysis** IntelliTrace の概要 ページのセクションです。 このセクションでは、発生したイベントの名前のみを表示するか、イベントの名前と共に、関数名、終了/エントリ ポイント、パラメーター、戻り値などの呼び出し情報を表示するかを選択できます。  
  
 選択して、IntelliTrace で Visual Studio イベントを取得できます、 **f5 キーを押して**キー。 ただし、SharePoint 固有のイベントを取得するには、Microsoft Monitoring Agent を使用して、SharePoint ソリューションの IntelliTrace データを収集する必要があります。 このツールは、Visual Studio の外部で配置されたアプリケーションの IntelliTrace データを収集し、.iTrace ファイルを作成します。 詳細については、次を参照してください。 [IntelliTrace 機能の](/visualstudio/debugger/intellitrace-features)と[IntelliTrace スタンドアロン コレクターを使用して](/visualstudio/debugger/using-the-intellitrace-stand-alone-collector)です。  
  
## <a name="unit-testing"></a>単体テスト  
 単体テストを使用すると、コード内のエラーを検出しやすくなります。単体テストでは、テスト メソッドの内部にテスト コードを記述して、それを実行します。 これらのメソッドには、SharePoint オブジェクト モデルに基づいてプロジェクトのロジックと機能を検証するために使用できる、空の変数と Assert ステートメントが含まれます。 詳しくは、「[コードの単体テストUnit Test Your Code](/visualstudio/test/unit-test-your-code)」をご覧ください。  
  
### <a name="support-for-microsoft-fakes-framework"></a>Microsoft Fakes フレームワークのサポート  
 SharePoint プロジェクトは Microsoft Fakes をサポートしています。これは、.NET Framework に基づいたアプリケーションでデリゲート ベースのテスト スタブと shim を作成できる分離フレームワークです。 Fakes フレームワークを使用することにより、単体テスト内でダミー実装を作成、管理、および挿入できます。 これらのスタブと shim は環境から単体テストを分離します。 スタブを作成すると、オーバーライド可能なメソッドを持つインターフェイスまたは非シール クラスを使用するコードをテストできます。 shim を作成すると、静的またはオーバーライド可能なメソッドを持つシール クラスへの、ハードコーディングされた呼び出しを代替 shim 実装にリダイレクトすることができます。 また、スタブ型および shim 型のデリゲートを使用して、個々のスタブ メンバーの動作を動的にカスタマイズすることもできます。 詳細については、次を参照してください。[分離 Code Under Test Microsoft Fakes で](/visualstudio/test/isolating-code-under-test-with-microsoft-fakes)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[IntelliTrace](/visualstudio/debugger/intellitrace)|IntelliTrace を使用して Visual Studio ソリューションをより簡単にデバッグする方法について説明します。|  
|[チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|IntelliTrace を使用して SharePoint プロジェクトのコード エラーを検出する方法について説明します。|  
|[コードの単体テスト](/visualstudio/test/unit-test-your-code)|単体テストを使用してコードの論理エラーを検出する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [コード品質の向上](/visualstudio/test/improve-code-quality)  
  
  