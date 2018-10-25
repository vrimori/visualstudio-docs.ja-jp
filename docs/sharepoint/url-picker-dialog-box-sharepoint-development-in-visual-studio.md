---
title: URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発) |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 517058c99a6ec5a297b95324decbb2cfcbe04271
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950759"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL ピッカー ダイアログ ボックス (Visual Studio での SharePoint 開発)
  URL ピッカー ダイアログ ボックスでは、SharePoint を実行しているローカル サーバー上には、マスター ページのファイルまたはイメージ ファイルは、プロジェクトまたは配置をなどのファイルを選択できます。  
  
 プロパティを設定するファイルを選択するオプションがある場合、このダイアログ ボックスが表示されます。 省略記号ボタンをクリックして、このダイアログ ボックスを開くことができます (![ASP.NET モバイル デザイナー楕円](../sharepoint/media/mwellipsis.gif "ASP.NET モバイル デザイナー楕円")) でのさまざまなプロパティの横にある、 **プロパティ**ウィンドウ。 省略記号ボタンも表示されます、IntelliSense とプロンプトの特定の属性に値を割り当てるときに、**ソース**デザイナーのビュー。  
  
## <a name="uielement-list"></a>UIElement の一覧
 **プロジェクト フォルダー**  
 プロジェクトまたは SharePoint を実行しているローカル サーバーで定義されているフォルダーの一覧が表示されます。 サブフォルダーを表示する展開ボタンを選択します。  
  
 展開、**プロジェクト**ノード、プロジェクト ファイルを選択します。 いうような表示 ダイアログ ボックスで、プロジェクト内のファイルは、次の条件を満たす必要があります。  
  
- ファイルは、マップされたフォルダーに含まれる必要があります。  
  
- ファイルは、ソリューション パッケージに追加する必要があります。  
  
- ファイルは、別のプロジェクトであることはできません。  
  
  これらの条件を満たしていないファイルを参照する場合は、ファイルのパスを手動で入力する必要があります。  
  
  展開、 **Server** SharePoint を実行しているローカル サーバーに配置されているファイルを選択するノード。 いうような表示 ダイアログ ボックスで、これらのファイルは、次の条件を満たす必要があります。  
  
- ファイルは次のマップされたフォルダーのいずれかである必要があります:**イメージ**、**レイアウト**、または**ControlTemplates**します。  
  
- ファイルは、SharePoint コンテンツ データベースに存在することはできません。  
  
  これらの条件を満たしていないファイルを参照する場合は、ファイルのパスを手動で入力する必要があります。  
  
  **フォルダーの内容**  
  選択したフォルダーに格納されているファイルの一覧を表示します。 ファイルを選択し、[、 **OK** ] ダイアログ ボックスを閉じ、選択内容がそれを呼び出したプロセスに送信するボタンをクリックします。  
  
  **ファイルの種類**  
  実行するタスクの適切なファイルの一覧から選択することができます。  
  
## <a name="see-also"></a>関連項目
 [For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [For SharePoint の web パーツを作成します。](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
