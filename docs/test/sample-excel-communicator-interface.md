---
title: "Excel Communicator インターフェイスのサンプル | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: 653d6430f18b2ca5cdbd2e1307f0c8386cebea91
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="sample-excel-communicator-interface"></a>Excel Communicator インターフェイスのサンプル
`IExcelUICommunication` インターフェイスのサンプルは `ExcelAddIn` プロジェクト内の `ExcelUICommunicator` オブジェクトで使用されています。  
  
## <a name="iexceluicommunication-interface"></a>IExcelUICommunication インターフェイス  
 このインターフェイスは、コード化された UI テスト プロセスで実行される `CodedUIExtension` と [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] プロセスで実行される `ExcelCodedUIAddIn` の間の通信ポイントを定義します。  
  
 `ExcelCodedUIAddinHelper` アセンブリには、このインターフェイスから派生し、Excel オブジェクト モデルを使用してメソッドを処理する `ExcelUICommunicator` クラスがあります。  
  
 一部のメソッドは、要求した情報を Excel から取得した後に `CellInformation` オブジェクトなどの情報オブジェクトの 1 つを作成し、返します。  
  
 また、提供される情報オブジェクトを使用して、Excel 内にある対応するコントロールを見つけ、そのコントロールで処理を実行するメソッドもあります。 たとえば、`ScrollIntoView` メソッドは所定のセルが表示されるまでワークシートをスクロールします。  
  
## <a name="codeduiextensibilitysample-and-excelcodeduiaddinhelper-communication"></a>CodedUIExtensibilitySample と ExcelCodedUIAddinHelper の通信  
 `ExcelCodedUIAddinHelper` アセンブリは Excel プロセスで実行されます。このアセンブリには、`IExcelUITestCommunication` インターフェイスを実装して、必要な情報を Excel UI から直接取得または設定する `UICommunicator` クラスがあります。  
  
 `CodedUIExtensibilitySample` アセンブリは Visual Studio のコード化された UI テスト プロセスで実行されます。 このアセンブリには `Communicator` クラスがあります。このクラスは .NET リモート処理チャネルを開き、`Instance` プロパティを提供します。このプロパティは `IExcelUICommunication` インターフェイスを使用して、`ExcelCodedUIAddinHelper` アセンブリ内の `UICommunicator` オブジェクトを使用し、要求および情報オブジェクト (`CellInformation` オブジェクトなど) を 2 つのアセンブリ間で相互にやり取りします。  
  
## <a name="see-also"></a>関連項目  
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [コード化された UI テスト用の Excel アドインのサンプル](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Excel 用にコード化された UI テストの拡張機能のサンプル](../test/sample-coded-ui-test-extension-for-excel.md)
