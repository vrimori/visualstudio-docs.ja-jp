---
title: "方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージング エクスプ ローラーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 25a2514f2d25661de2898be8d2ef9ff051cc5559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>方法: パッケージング エクスプローラーを使用してパッケージのフィーチャーおよび項目を追加および削除する
  SharePoint プロジェクト項目およびフィーチャーを配置するためのパッケージを構成するのには、パッケージング エクスプ ローラーを使用することができます。 .Wsp ファイル内では、SharePoint プロジェクト項目と機能を調整できます。  
  
 または、パッケージ デザイナーを使用して、表示およびアクティブ化順序を変更する機能の順序を変更することができます。 詳細については、次を参照してください。[する方法: して追加および削除のフィーチャーおよび項目をパッケージにパッケージ デザイナーを使用して](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)です。  
  
## <a name="opening-the-packaging-explorer"></a>パッケージング エクスプ ローラーを開く  
 Visual Studio ソリューションに 1 つ以上の SharePoint プロジェクト場合は、パッケージ エクスプ ローラーを開き、次の手順を使用できます。 または、パッケージング エクスプ ローラーが自動的に開きますフィーチャーまたはパッケージ デザイナーを表示するとします。 すべての機能およびパッケージ デザイナーを閉じると後もパッケージング エクスプ ローラーを閉じます。  
  
#### <a name="to-open-the-packaging-explorer"></a>パッケージ エクスプ ローラーを開く  
  
1.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、**パッケージング エクスプ ローラー**です。  
  
     **パッケージング エクスプ ローラー**に表示されます、**ツールボックス**です。  
  
## <a name="adding-a-feature-to-a-package"></a>パッケージに機能の追加  
 パッケージング エクスプ ローラーを使用して、パッケージに新規および既存の機能を追加できます。  
  
#### <a name="to-add-a-sharepoint-feature"></a>SharePoint 機能を追加するには  
  
1.  開く、**パッケージング エクスプ ローラー**、プロジェクトのショートカット メニューを開きを選択し、**フィーチャーの追加**です。  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>既存の SharePoint フィーチャーを移動するには  
  
1.  開く、**パッケージング エクスプ ローラー**、次の手順のいずれかを実行します。  
  
    -   ドラッグ、**機能**別のプロジェクトに 1 つのプロジェクトからです。  
  
    -   機能のショートカット メニューを開き、選択**切り取り**、クリックして、この機能を移動するプロジェクトのショートカット メニューを開いて**貼り付け**です。  
  
    > [!NOTE]  
    >  ソリューションに複数の SharePoint プロジェクトがある場合は、この手順を使用します。  
  
## <a name="validating-a-feature-or-package"></a>機能またはパッケージの検証  
 ファイルを検証することによって、SharePoint のフィーチャーおよびパッケージ内の潜在的な問題を識別できます。 警告とエラーは、エラー一覧 ウィンドウと出力ウィンドウに表示されます。  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>SharePoint フィーチャーまたはパッケージを検証するには  
  
1.  開く、**パッケージング エクスプ ローラー**です。  
  
2.  機能またはパッケージのショートカット メニューを開き、選択**検証**です。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  