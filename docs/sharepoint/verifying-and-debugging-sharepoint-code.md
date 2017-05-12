---
title: "SharePoint コードの検証およびデバッグ"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "単体テスト [Visual Studio での SharePoint 開発]"
  - "IntelliTrace [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発、IntelliTrace"
  - "Visual Studio での SharePoint 開発、単体テスト"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# SharePoint コードの検証およびデバッグ
  IntelliTrace と単体テストを使用すると、SharePoint ソリューションを簡単にデバッグして、ソリューション内の各メソッドが正常に動作することを確認できます。  これらの機能は、他の種類のプロジェクトと同じ手順で、[!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] の SharePoint プロジェクトに対して使用できます。  
  
## IntelliTrace  
 IntelliTrace を使用して、SharePoint ソリューションの現在の状態だけでなく、過去に発生したイベントおよび発生時のコンテキストも調べることができます。  SharePoint ソリューション内の目的のイベントが記録されたさまざまな時点に移動し、各時点の状態と変数値を確認することができます。  この動的ナビゲーションを使用すると、多数のブレークポイントを設定しなくても、すばやく簡単に SharePoint ソリューションをデバッグできます。  また、デバッグ セッションを IntelliTrace ログ \(.iTrace\) ファイルに保存し、後でこのファイルを Visual Studio Ultimate で開いて、ポスト クラッシュ デバッグを実行できます。  .iTrace ファイルには、特定の SharePoint エラーがいつどこで発生したかに関する詳細情報が含まれているため、エラーの原因がわかりやすくなります。  .iTrace ファイルに含まれる情報は、SharePoint の Unified Logging System \(ULS\) で作成される完全なエラー ログのサブセットです。  この情報には、ユーザー プロファイルがいつ開かれたか、閉じられたか、SharePoint プロジェクト内のプロパティがいつ読み込まれたか、読み取られたか、変更されたかなど、SharePoint 固有のイベントが含まれています。  IntelliTrace でどのイベントを記録するか、構成することもできます。  詳細については、「[保存された IntelliTrace データの使用](../debugger/using-saved-intellitrace-data.md)」および「[デバッグ情報収集のための IntelliTrace の構成](http://msdn.microsoft.com/ja-jp/7657ecab-e07e-4b1b-872d-f05d966be37e)」を参照してください。  
  
 SharePoint でエラーが発生した場合、エラー ダイアログ ボックスには、そのエラーの "相関 ID" 識別子が表示されます。  .iTrace ファイルに示されているイベントから相関 ID を取得することもできます。  特定の相関 ID で発生したすべてのイベントの一覧を表示するには、IntelliTrace の概要ページの **\[分析\]** のセクションに ID を入力します。  このセクションでは、発生したイベントの名前のみを表示するか、イベントの名前と共に、関数名、終了\/エントリ ポイント、パラメーター、戻り値などの呼び出し情報を表示するかを選択できます。  
  
 **F5** キーを押すことにより、IntelliTrace で Visual Studio イベントを取得できます。  ただし、SharePoint 固有のイベントを取得するには、Microsoft Monitoring Agent を使用して、SharePoint ソリューションの IntelliTrace データを収集する必要があります。  このツールは、Visual Studio の外部で配置されたアプリケーションの IntelliTrace データを収集し、.iTrace ファイルを作成します。  詳細については、「[IntelliTrace の機能](../debugger/intellitrace-features.md)」および「[IntelliTrace スタンドアロン コレクターを使用する](../debugger/using-the-intellitrace-stand-alone-collector.md)」を参照してください。  
  
## 単体テスト  
 単体テストを使用すると、コード内のエラーを検出しやすくなります。単体テストでは、テスト メソッドの内部にテスト コードを記述して、それを実行します。  これらのメソッドには、SharePoint オブジェクト モデルに基づいてプロジェクトのロジックと機能を検証するために使用できる、空の変数と Assert ステートメントが含まれます。  詳細については、「[コードの単体テスト](../test/unit-test-your-code.md)」を参照してください。  
  
### Microsoft Fakes フレームワークのサポート  
 SharePoint プロジェクトは Microsoft Fakes をサポートしています。これは、.NET Framework に基づいたアプリケーションでデリゲート ベースのテスト スタブと shim を作成できる分離フレームワークです。  Fakes フレームワークを使用することにより、単体テスト内でダミー実装を作成、管理、および挿入できます。  これらのスタブと shim は環境から単体テストを分離します。  スタブを作成すると、オーバーライド可能なメソッドを持つインターフェイスまたは非シール クラスを使用するコードをテストできます。  shim を作成すると、静的またはオーバーライド可能なメソッドを持つシール クラスへの、ハードコーディングされた呼び出しを代替 shim 実装にリダイレクトすることができます。  また、スタブ型および shim 型のデリゲートを使用して、個々のスタブ メンバーの動作を動的にカスタマイズすることもできます。  詳細については、「[Microsoft Fakes を使用したテストでのコードの分離](../test/isolating-code-under-test-with-microsoft-fakes.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[IntelliTrace の使用](../debugger/intellitrace.md)|IntelliTrace を使用して Visual Studio ソリューションをより簡単にデバッグする方法について説明します。|  
|[チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|IntelliTrace を使用して SharePoint プロジェクトのコード エラーを検出する方法について説明します。|  
|[コードの単体テスト](../test/unit-test-your-code.md)|単体テストを使用してコードの論理エラーを検出する方法について説明します。|  
  
## 参照  
 [コードの品質向上](../test/improve-code-quality.md)  
  
  