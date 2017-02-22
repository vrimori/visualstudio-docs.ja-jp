---
title: "Excel Communicator インターフェイスのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Excel Communicator インターフェイスのサンプル
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IExcelUICommunication`  インターフェイスのサンプルは `ExcelAddIn` プロジェクト内の`ExcelUICommunicator` オブジェクトで使用されています。  
  
## IExcelUICommunication インターフェイス  
 このインターフェイスは、コード化された UI テスト プロセスで実行される `CodedUIExtension` と [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] プロセスで実行される `ExcelCodedUIAddIn` の間の通信ポイントを定義します。  
  
 `ExcelCodedUIAddinHelper`  アセンブリには、このインターフェイスから派生し、Excel オブジェクト モデルを使用してメソッドを処理する `ExcelUICommunicator` クラスがあります。  
  
 メソッドには、要求された情報を Excel から取得し、`CellInformation` オブジェクトなどの情報オブジェクトの 1 つを作成して返すオブジェクトがあります。  
  
 また、提供される情報オブジェクトを使用して、Excel 内にある対応するコントロールを見つけ、そのコントロールで処理を実行するメソッドもあります。  たとえば、`ScrollIntoView` メソッドは所定のセルが表示されるまでワークシートをスクロールします。  
  
## CodedUIExtensibilitySample と ExcelCodedUIAddinHelper の通信  
 `ExcelCodedUIAddinHelper`  アセンブリは Excel プロセスで実行されます。このアセンブリには、`IExcelUITestCommunication` インターフェイスを実装して、要求された情報を Excel UI から直接取得または設定する `UICommunicator` クラスがあります。  
  
 `CodedUIExtensibilitySample`  アセンブリは Visual Studio のコード化された UI テスト プロセスで実行されます。  このアセンブリには .NET リモート処理チャネルを開く `Communicator` クラスがあり、`ExcelCodedUIAddinHelper` アセンブリ内の `UICommunicator` オブジェクトを使用するために `IExcelUICommunication` インターフェイスを使用して、要求と `CellInformation` オブジェクトなどの情報オブジェクトを 2 つのアセンブリ間で渡す、`Instance` プロパティを提供します。  
  
## 参照  
 [コード化された UI テストと操作の記録を拡張して Microsoft Exce をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [コード化された UI テスト用の Excel アドインのサンプル](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Excel 用にコード化された UI テストの拡張子のサンプル](../test/sample-coded-ui-test-extension-for-excel.md)