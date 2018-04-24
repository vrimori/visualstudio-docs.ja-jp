---
title: Excel Communicator インターフェイスのサンプル | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 85d369ad7ddb468da86f3b19c070be4e125f941a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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

- [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
- [コード化された UI テスト用の Excel アドインのサンプル](../test/sample-excel-add-in-for-coded-ui-testing.md)
- [Excel 用にコード化された UI テストの拡張子のサンプル](../test/sample-coded-ui-test-extension-for-excel.md)
