---
title: 'Excel 拡張子のサンプル: ExtensionPackage クラス | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fadfbf9291daf35cea4e7ef3005cf3791c2fe052
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533631"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Excel 拡張子のサンプル: ExtensionPackage クラス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Excel 拡張子のサンプル: ExtensionPackage クラス](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-extensionpackage-class)します。  
  
このクラスは <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> クラスを拡張し、[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] ワークシートをテストするコード化された UI テストのエントリ ポイントになります。  
  
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



