---
title: "コード化された UI テスト用の Excel アドインのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード化された UI テスト, Excel アドイン サンプル"
ms.assetid: 2cd52d1a-4c35-43ca-8a84-9c79dabd907f
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# コード化された UI テスト用の Excel アドインのサンプル
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] 用アドイン サンプルは、Excel ワークシートのコード化された UI テストを明確にサポートし、Visual Studio Enterprise で動作するように設計されています。 このアドインは、Visual Studio Tools for Office を使用して作成されています。  
  
 Excel アドインを作成する方法の詳細については、「[チュートリアル : 初めての Excel 用 VSTO アドインの作成](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)」を参照するか、または MSDN で "Excel アドイン" を検索してください。  
  
 Excel アドインは Excel 用のコード化された UI テスト拡張機能に関するこのドキュメントの主題ではありませんが、いくつかのコメントが役立ちます。  
  
 このアドインの重要な部分:  
  
-   `ThisAddIn`  クラス \- `ExcelUICommunicator` と [Excel 用にコード化された UI テストの拡張子のサンプル](../test/sample-coded-ui-test-extension-for-excel.md)の間の .NET リモート処理チャネルを管理します。  
  
-   `ExcelCodedUIAddinHelper_TemporaryKey.pfx`  \- アドインのテスト用のセキュリティ証明書。  
  
-   `ExcelUICommunicator`  クラス \- このクラスは、`IExcelUICommunication` インターフェイスを実装します。  
  
## ThisAddIn クラス  
 このクラスのほとんどは、実際に Excel アドイン プロジェクトを作成するときに Visual Studio Tools for Office によって `ThisAddIn.Designer.cs` ファイルに生成されます。  
  
 実装する必要があるメンバーは、`ThisAddIn_Startup()` と `ThisAddIn_Shutdown()` のイベント ハンドラーです。  これらのイベント ハンドラーは、`ExcelUICommunicator` によって使用される .NET リモート処理チャネルを初期化または閉じることを目的としています。  
  
## ExcelCodedUIAddinHelper\_TemporaryKey.pfx  
 このファイルには、Visual Studio Tools for Office によって生成され、アドインと拡張機能のテストのために Excel プロセスで動作するのに必要なアドイン アセンブリのアクセス許可を与える一時的なセキュリティ証明書が含まれます。  この証明書を削除した後、プロジェクトの**プロパティ** ウィンドウの **\[署名\]** タブで新しい証明書を作成するか、または独自のテスト用証明書をアタッチする必要があります。  
  
## ExcelUICommunicator クラス  
 このクラスは、`IExcelUITestCommunication` インターフェイスを実装し、Excel オブジェクト モデルから要求された UI 情報を取得します。  詳細については、「[Excel Communicator インターフェイスのサンプル](../test/sample-excel-communicator-interface.md)」を参照してください。  
  
## 参照  
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [チュートリアル : 初めての Excel 用 VSTO アドインの作成](../Topic/Walkthrough:%20Creating%20Your%20First%20VSTO%20Add-in%20for%20Excel.md)   
 [Office および SharePoint 開発](/office-dev/office-dev/office-and-sharepoint-development-in-visual-studio)