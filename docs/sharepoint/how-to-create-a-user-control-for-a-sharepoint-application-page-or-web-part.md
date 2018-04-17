---
title: '方法: SharePoint アプリケーション ページのユーザー コントロールを作成または Web パーツ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26f71486f48379f0f7005107b3df4f9f79960ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>方法: SharePoint アプリケーション ページまたは Web パーツのユーザー コントロールを作成する
  SharePoint ソリューション向けの独自の機能を備えたカスタム ユーザー コントロールを作成し、その機能をプロジェクト内で再利用することができます。 ユーザー コントロールは、Web パーツまたはアプリケーション ページに含めることができます。他の ASP.NET コントロールや SharePoint コントロールを追加し、コントロールのプロパティとメソッドを定義することもできます。 ユーザー コントロールの詳細については、次を参照してください。 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成する](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)と[ユーザー コントロールと SharePoint のサーバー コントロール](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx)です。  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>SharePoint のユーザー コントロールを作成するには  
  
1.  Visual Studio で、SharePoint プロジェクトを開くか作成します。  
  
     参照してください[SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。  
  
2.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
3.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。  
  
     **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
4.  **インストール** ウィンドウで、選択、 **Office/sharepoint**ノード。  
  
5.  SharePoint テンプレートの一覧で選択**ユーザー コントロール (ファーム ソリューションのみ)**です。  
  
    > [!NOTE]  
    >  ユーザー コントロールはファーム ソリューションでのみ機能します。  
  
6.  **名前**ボックス、ユーザー コントロールの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     複数のフォルダーとファイルがプロジェクトに追加されます。 これらのファイルに関する詳細については、次を参照してください。 [Web パーツまたはアプリケーション ページの再利用可能なコントロールを作成する](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)です。  
  
     既定では、ユーザー コントロール ファイルの表示で、**ソース**Visual Web Developer デザイナーのビューです。 このビューで、コントロールの XML マークアップを編集できます。 切り替えることができます**デザイン**からコントロールをドラッグしてコントロールを視覚的にデザインする場合の表示、**ツールボックス**です。 参照してください[デザイン ビュー、Web ページ デザイナー](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d)です。  
  
7.  コントロールで発生するイベントを処理する場合は、ユーザー コントロールのコード ファイルにコードを追加します。  
  
     このファイルに表示されます**ソリューション エクスプ ローラー**ユーザー コントロール ファイルの下、.cs または .vb 拡張子は、プロジェクトの言語に応じて、します。  
  
## <a name="see-also"></a>関連項目  
 [Web パーツまたはアプリケーション ページの再利用可能なコントロールの作成](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [For SharePoint アプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [SharePoint の Web パーツの作成](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  