---
title: '方法: 追加およびパッケージング エクスプ ローラーを使用して機能およびパッケージにアイテムを削除する |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b1211b0bdc3625b915221cfafaa5377d371aaa25
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880862"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>方法: 追加およびパッケージング エクスプ ローラーを使用して、フィーチャーおよびパッケージに項目を削除
  SharePoint プロジェクト項目およびフィーチャーを配置するパッケージを構成するには、パッケージング エクスプ ローラーを使用できます。 .Wsp ファイル内では、SharePoint プロジェクト項目と機能を調整できます。  
  
 または、パッケージ デザイナーを使用して、表示し、再アクティブ化順序を変更する機能を要求することができます。 詳細については、「[方法 :追加して、パッケージ デザイナーを使用して機能と、パッケージにアイテムを削除](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)します。  
  
## <a name="open-the-packaging-explorer"></a>パッケージング エクスプ ローラーを開く  
 Visual Studio ソリューションに少なくとも 1 つの SharePoint プロジェクトがある場合、パッケージ エクスプ ローラーを開く、次の手順を使用できます。 または、パッケージング エクスプ ローラーが自動的に開きますフィーチャーまたはパッケージ デザイナーを表示するとします。 すべての機能とパッケージ デザイナーが閉じた後もパッケージング エクスプ ローラーを閉じます。  
  
#### <a name="to-open-the-packaging-explorer"></a>パッケージング エクスプ ローラーを開く  
  
1.  メニュー バーで、**ビュー** > **その他の Windows** > **パッケージング エクスプ ローラー**します。  
  
     **パッケージング エクスプ ローラー**に表示されます、**ツールボックス**します。  
  
## <a name="adding-a-feature-to-a-package"></a>パッケージに機能の追加  
 パッケージング エクスプ ローラーを使用して、パッケージに新規および既存の機能を追加できます。  
  
#### <a name="to-add-a-sharepoint-feature"></a>SharePoint フィーチャーを追加するには
  
1.  開く、**パッケージング エクスプ ローラー**、プロジェクトのショートカット メニューを開き、選択し、**機能の追加**します。  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>既存の SharePoint 機能を移動するには  
  
1.  開く、**パッケージング エクスプ ローラー**、次の手順のいずれかを実行します。  
  
    -   ドラッグ、**機能**別のプロジェクトに 1 つのプロジェクトから。  
  
    -   機能のショートカット メニューを開き、選択**切り取り**の機能 を選択しプロジェクトのショートカット メニューを開き**貼り付け**します。  
  
    > [!NOTE]  
    >  ソリューションには、複数の SharePoint プロジェクトがある場合は、この手順を使用します。  
  
## <a name="validate-a-feature-or-package"></a>機能またはパッケージを検証します。  
 ファイルを検証することで、SharePoint のフィーチャーおよびパッケージ内の潜在的な問題を特定できます。 出力ウィンドウおよびエラー一覧 ウィンドウには、警告とエラーが表示されます。  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>SharePoint フィーチャーまたはパッケージを検証するには
  
1.  開く、**パッケージング エクスプ ローラー**します。  
  
2.  機能またはパッケージのショートカット メニューを開き、選択**検証**です。  
  
## <a name="see-also"></a>関連項目
 [パッケージ化し、SharePoint ソリューションのデプロイ](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
