---
title: For SharePoint アプリケーション ページの作成 |Microsoft Docs
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
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f1c3b03507ca97724106c6ca1d121b3c54eb659
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853143"
---
# <a name="create-application-pages-for-sharepoint"></a>For SharePoint アプリケーション ページを作成します。
  *アプリケーション ページ*は SharePoint Web サイトで使用するために設計された ASP.NET Web ページです。 アプリケーション ページは、ASP.NET ページの特殊な種類です。 アプリケーション ページと標準の ASP.NET ページの主な違いは、アプリケーション ページに、SharePoint のマスター ページとマージされるコンテンツが含まれています。 マスター ページには、サイト上の他のページと同じ外観と動作を共有するアプリケーション ページことができます。  
  
 Visual Studio では、デザイナーを使用してアプリケーション ページをデザインすることができます。 デザイナーでは、マスター ページで定義されている各コンテンツのプレース ホルダーのコンテンツ領域が表示されます。 アプリケーション ページをデザインするには、これらの領域にコントロールをドラッグします。  
  
## <a name="application-pages"></a>アプリケーション ページ
 アプリケーション ページは、サイトのページが特定の 1 つのサイトには、サーバー上のすべてのサイトで共有されます。 詳細については、 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)します。  
  
 既定では、SharePoint サイトを作成するときに表示されるページのほとんどは、サイトのページは。 サイトのページは、SharePoint ページのライブラリに追加できます。 ユーザーは、SharePoint Designer などのツールを使用して、[サイト] ページをカスタマイズできます。 [サイト] ページでは、動的 Web パーツ、および Web パーツの領域などの機能もホストできます。  
  
 アプリケーション ページには、これらの操作を実行できません。 ただし、アプリケーション ページは、ページを作成する場合は、カスタム コードを含むページの最適な型です。 サイト ページにカスタム コードを追加できますが、コードは、ユーザーは、SharePoint Designer などのツールを使用して、ページをカスタマイズした場合に実行を停止します。  
  
> [!NOTE]  
>  Visual Studio では提供されませんする際に役立つテンプレートは、SharePoint サイトのサイト ページを作成します。 詳細については、次を参照してください。 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)します。  
  
## <a name="create-an-application-page"></a>アプリケーション ページを作成します。
 アプリケーション ページを作成するには追加、**アプリケーション ページ**を SharePoint プロジェクト項目。 アプリケーション ページを作成するときに Visual Studio は、次のフォルダーをプロジェクトに追加します。  
  
|フォルダー|説明|  
|------------|-----------------|  
|レイアウト|SharePoint のファイル システムの _layouts 仮想ディレクトリにマップされます。|  
|レイアウトのサブフォルダー|アプリケーション ページを構成するファイルが含まれています。 既定では、このフォルダーには、プロジェクトと同じ名前があります。 このフォルダーは、いつでも変更できます。 プロジェクトを実行するときに、Visual Studio は、SharePoint のファイル システムの _layouts 仮想ディレクトリにこのフォルダーを展開します。|  
  
 Visual Studio では、プロジェクトに次のファイルが追加されます。  
  
|ファイル|説明|  
|----------|-----------------|  
|ASP.NET ページファイル (*.aspx*)|ページを定義する XML マークアップが含まれています。|  
|アプリケーション ページ コード ファイル|アプリケーション ページで、分離コードが含まれています。 このファイルにイベントを処理するコードを追加します。|  
|アプリケーション ページ デザイナー コード ファイル|デザイナーによって生成されるコードが含まれています。 このファイルを直接編集しないでください。|  
  
## <a name="design-and-debug-an-application-page"></a>デザインおよびアプリケーション ページのデバッグ
 Visual Studio のデザイナー ビューを使用して、アプリケーション ページの内容をデザインします。 プロジェクトでアプリケーション ページを開くときに、このデザイナーが表示されます (またはショートカット メニューを選択し、ダブルクリックして**開く**) 選択し、**デザイン**の下部にあるボタンエディター。  
  
> [!NOTE]  
>  ページを作成するだけで、**ソース**デザイナーのビュー。 **デザイン**アプリケーション ページ用のデザイナー ビューが無効になっています。  
  
 Visual Studio での他の SharePoint プロジェクト項目をデバッグする場合と同様に、アプリケーション ページをデバッグできます。 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 アプリケーション ページを表示する必要があります手動でに移動するアプリケーション ページの場所 (例: http://<em>Server_Name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx)。  
  
 SharePoint プロジェクトをデバッグする方法の詳細については、次を参照してください。[のトラブルシューティングを行う SharePoint ソリューション](../sharepoint/troubleshooting-sharepoint-solutions.md)します。  
  
## <a name="choose-a-master-page"></a>マスター ページを選択します。
 既定で、**アプリケーション ページ**項目が、プロジェクトのデバッグを使用しているサイトのマスター ページを参照します。 V4.master という名前のページがその一覧に検索することができます、**マスタ ページ ギャラリ**の SharePoint サイト。  
  
 設定して、アプリケーション ページによって使用されるマスター ページを明示的に変更できる、`MasterPageFile`属性は、アプリケーションの`Page`要素。 (例: `MasterPageFile="~/_layouts/applicationv4.master"`)。 実際には、動的なマスター ページは、SharePoint サーバーで有効になっていない場合は、この属性を設定する必要があります。 SharePoint のマスター ページの詳細については、次を参照してください。[マスター ページ](http://go.microsoft.com/fwlink/?LinkID=169281)します。  
  
## <a name="see-also"></a>関連項目
 [SharePoint Foundation の開発の詳細](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET の概要](/aspnet/overview)   
 [ASP.NET Web ページ](/aspnet/web-pages/index)   
  
