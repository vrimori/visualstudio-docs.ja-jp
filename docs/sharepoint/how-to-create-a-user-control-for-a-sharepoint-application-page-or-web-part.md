---
title: '方法: SharePoint アプリケーション ページのユーザー コントロールを作成または Web パーツ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58288f482b7b32319d8c45c9b12e75899541b81e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865048"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>方法: SharePoint アプリケーション ページまたは web パーツのユーザー コントロールを作成します。
  SharePoint ソリューション向けの独自の機能を備えたカスタム ユーザー コントロールを作成し、その機能をプロジェクト内で再利用することができます。 ユーザー コントロールは、Web パーツまたはアプリケーション ページに含めることができます。他の ASP.NET コントロールや SharePoint コントロールを追加し、コントロールのプロパティとメソッドを定義することもできます。 ユーザー コントロールの詳細については、次を参照してください。 [web パーツまたはアプリケーション ページの再利用可能なコントロール作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)と[ユーザー コントロールと SharePoint のサーバー コントロール](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/)します。  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint のユーザー コントロールを作成するには  
  
1.  Visual Studio で、SharePoint プロジェクトを開くか作成します。  
  
     参照してください[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。  
  
2.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
3.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
4.  **インストール済み**ウィンドウで、選択、 **Office/sharepoint**ノード。  
  
5.  SharePoint テンプレートの一覧で選択**ユーザー コントロール (ファーム ソリューションのみ)** します。  
  
    > [!NOTE]  
    >  ユーザー コントロールはファーム ソリューションでのみ機能します。  
  
6.  **名前**ボックス、ユーザー コントロールの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     複数のフォルダーとファイルがプロジェクトに追加されます。 これらのファイルの詳細については、次を参照してください。 [web パーツまたはアプリケーション ページの再利用可能なコントロール作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)です。  
  
     既定では、ユーザー コントロール ファイルの表示で、**ソース**Visual Web Developer デザイナーのビュー。 このビューで、コントロールの XML マークアップを編集できます。 切り替えることができます**デザイン**からコントロールをドラッグしてコントロールを視覚的にデザインする場合の表示、**ツールボックス**します。 参照してください[デザイン ビュー、Web ページ デザイナー](/previous-versions/aspnet/ms178149\(v\=vs.100\))します。  
  
7.  コントロールで発生するイベントを処理する場合は、ユーザー コントロールのコード ファイルにコードを追加します。  
  
     このファイルに表示されます**ソリューション エクスプ ローラー**ユーザー コントロール ファイルであり、 *.cs*または *.vb*プロジェクトの言語に応じて、拡張機能。  
  
## <a name="see-also"></a>関連項目
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成します。](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [For SharePoint の web パーツを作成します。](../sharepoint/creating-web-parts-for-sharepoint.md)  
