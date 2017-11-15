---
title: "Excel 拡張子のサンプル: ExtensionPackage クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.openlocfilehash: d493f4f3fd3bf7a3f5d4f393303d4ec4f5a555d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
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
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [コード化された UI テストと操作の記録を拡張して Microsoft Excel をサポート](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
