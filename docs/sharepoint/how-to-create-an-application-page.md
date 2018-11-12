---
title: '方法: アプリケーション ページを作成する |Microsoft Docs'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f390ddf14925b43f1aa1d9e79db05e2aa64f234
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296204"
---
# <a name="how-to-create-an-application-page"></a>方法: アプリケーション ページを作成
  1 つまたは複数の SharePoint サイトの ASP.NET web ページを作成することができます。 SharePoint では、これらのページに、アプリケーション ページは呼び出されます。 サイトのページとは異なり、アプリケーション ページには、ページの背後で実行されるコードが含まれています。 詳細については、次を参照してください。[用 SharePoint アプリケーション ページを作成](../sharepoint/creating-application-pages-for-sharepoint.md)です。  
  
### <a name="to-create-an-application-page"></a>アプリケーション ページを作成するには  
  
1.  Visual Studio で、SharePoint プロジェクトを開くか作成します。  
  
     詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)します。  
  
2.  **ソリューション エクスプローラー**で、プロジェクト ノードを選択します。  
  
3.  メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。  
  
4.  **新しい項目の追加** ダイアログ ボックスで、展開、 **SharePoint**ノードを選択し、 **2010**項目。  
  
5.  SharePoint テンプレートの一覧で選択**アプリケーション ページ**します。  
  
6.  **名前**ボックス、アプリケーションのページでの名前を指定し、選択、**追加**ボタンをクリックします。  
  
     複数のフォルダーとファイルがプロジェクトに追加されます。 これらのファイルの詳細については、次を参照してください。[用 SharePoint アプリケーション ページを作成](../sharepoint/creating-application-pages-for-sharepoint.md)です。  
  
     **ソース**ASP.NET ページファイル、Visual Web Developer デザイナーのビューが表示されます。 コントロールを追加して、ページを設計することができます、**ツールボックス**コンテンツ プレース ホルダーに配置することです。 詳細については、次を参照してください。[ソース ビュー、Web ページ デザイナー](/previous-versions/aspnet/ms178154\(v\=vs.100\))します。  
  
7.  コントロールのイベントを処理する場合は、アプリケーション ページのコード ファイルにコードを追加します。  
  
     コード ファイルを選択し、ASP.NET ページファイルのノードを展開する場合に表示されますが、 *.cs*または *.vb*プロジェクトの言語に応じて、拡張機能。 アプリケーション ページを作成する方法のエンド ツー エンド例は、次を参照してください。[チュートリアル: SharePoint アプリケーション ページを作成する](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)します。  
  
## <a name="see-also"></a>関連項目
 [For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [チュートリアル: SharePoint アプリケーション ページを作成します。](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
