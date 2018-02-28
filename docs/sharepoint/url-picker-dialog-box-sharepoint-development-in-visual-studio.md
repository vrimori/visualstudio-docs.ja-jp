---
title: "URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 65851596d7a9df1ec7da9106891dff6471f1afb6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発)
  URL ピッカー ダイアログ ボックスでは、SharePoint を実行しているローカル サーバー上には、マスター ページ ファイルまたはイメージ ファイルは、プロジェクト内、または配置をなどのファイルを選択できます。  
  
 プロパティを設定するファイルを選択するオプションがある場合、このダイアログ ボックスが表示されます。 省略記号ボタンをクリックしてこのダイアログ ボックスを開くことができます (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) にさまざまなプロパティの横にある、 **のプロパティ**ウィンドウです。 省略記号ボタンとしても表示されます、IntelliSense がプロンプトで特定の属性に値を割り当てるときに、**ソース**デザイナーのビューです。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **プロジェクト フォルダー**  
 プロジェクトまたは SharePoint を実行しているローカル サーバー上で定義されたフォルダーの一覧を表示します。 サブフォルダーを表示する展開ボタンを選択します。  
  
 展開、**プロジェクト**ノードをプロジェクトにファイルを選択します。 いうような表示 ダイアログ ボックスで、プロジェクト内のファイルは、次の条件を満たす必要があります。  
  
-   ファイルは、マップされたフォルダーに含まれる必要があります。  
  
-   ファイルは、ソリューション パッケージに追加する必要があります。  
  
-   ファイルは、別のプロジェクトに存在することはできません。  
  
 これらの条件を満たしていないファイルを参照する場合は、ファイルのパスを手動で入力する必要があります。  
  
 展開して、**サーバー** SharePoint が実行されているローカル サーバーに配置されているファイルを選択するノードです。 いうような表示 ダイアログ ボックスで、これらのファイルは、次の条件を満たす必要があります。  
  
-   ファイルは、次のマップされたフォルダーのいずれかである必要があります:**イメージ**、**レイアウト**、または**全体について**です。  
  
-   ファイルは、SharePoint コンテンツ データベースに存在することはできません。  
  
 これらの条件を満たしていないファイルを参照する場合は、ファイルのパスを手動で入力する必要があります。  
  
 **フォルダーの内容**  
 選択したフォルダーに格納されているファイルの一覧を表示します。 ファイルを選択し、[、 **OK** ] ダイアログ ボックスを閉じ、選択内容がその呼び出し元プロセスに送信するボタンをクリックします。  
  
 **ファイルの種類**  
 実行しているタスクに対応するファイルの一覧から選択できます。  
  
## <a name="see-also"></a>参照  
 [For SharePoint アプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Web パーツまたはアプリケーション ページの再利用できるコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  