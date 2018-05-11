---
title: 'Excel 拡張子のサンプル: ExtensionPackage クラス | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 623b18a22441fdd2478716582d94a8b878c31d54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Excel 拡張子のサンプル: ExtensionPackage クラス
このクラスは <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> クラスを拡張し、[!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] ワークシートをテストするコード化された UI テストのエントリ ポイントになります。

## <a name="assembly-attribute"></a>アセンブリ属性
 ファイルは、アセンブリを UI テスト拡張として識別するアセンブリ属性で始まります。

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 この属性は、基本クラス名、パッケージ クラスの名前、およびカスタム拡張パッケージ クラスの完全修飾クラス名を宣言します。

## <a name="simple-properties"></a>単純なプロパティ
 このクラスには、コード化された UI テスト フレームワークが拡張とアセンブリを識別および説明するために使用する値を提供するプロパティがあります。 詳細については、コードのコメントをご覧ください。

## <a name="getservice-method"></a>GetService メソッド
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> メソッドは、各オブジェクトの基底クラスによって識別され、コード化された UI テスト フレームワークがテクノロジ マネージャー、プロパティ プロバイダー、およびアクション フィルターにアクセスするために使用する単一エントリ ポイントです。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
