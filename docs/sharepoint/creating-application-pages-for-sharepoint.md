---
title: For SharePoint アプリケーション ページの作成 |Microsoft ドキュメント
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
ms.openlocfilehash: 8bc73918a2af82acab1fd465f5f80755cc594ba9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691980"
---
# <a name="creating-application-pages-for-sharepoint"></a>For SharePoint アプリケーション ページの作成
  *アプリケーション ページ*が SharePoint Web サイトで使用するよう設計された ASP.NET Web ページです。 アプリケーション ページとは、ASP.NET ページの特化された型です。 アプリケーション ページと標準の ASP.NET ページの主な違いは、アプリケーション ページには、SharePoint のマスター ページとマージされるコンテンツが含まれているです。 マスター ページには、サイト上の他のページと同じ外観と動作を共有するアプリケーション ページができるようにします。  
  
 Visual Studio では、デザイナーを使用して、アプリケーション ページをデザインすることができます。 デザイナーは、マスター ページで定義されている各コンテンツのプレース ホルダーのコンテンツ領域を表示します。 アプリケーション ページをデザインするには、これらの領域にコントロールをドラッグします。  
  
## <a name="application-pages"></a>アプリケーション ページ
 アプリケーション ページは、サイトのページが特定の 1 つのサイトには、サーバー上のすべてのサイトで共有されます。 詳細については、 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)です。  
  
 既定は、SharePoint サイトを作成するときに表示されるページのほとんどは、サイトのページです。 サイトのページは、SharePoint ページ ライブラリに追加できます。 ユーザーは、SharePoint デザイナーなどのツールを使用して、サイトのページをカスタマイズできます。 [サイト] ページでは、動的 Web パーツ、および Web パーツの領域などの機能もホストできます。  
  
 アプリケーション ページには、これらの作業を行うことはできません。 ただし、アプリケーション ページは、最適な型を作成する場合は、ページをカスタム コードを含むページのです。 サイトのページには、カスタム コードを追加できますが、コードが、ユーザーが SharePoint デザイナーなどのツールを使用して、ページをカスタマイズした場合の実行を停止します。  
  
> [!NOTE]  
>  Visual Studio の管轄外に役立つテンプレートが SharePoint サイトのサイトのページを作成します。 詳細については、次を参照してください。 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)です。  
  
## <a name="create-an-application-page"></a>アプリケーション ページを作成します。
 アプリケーション ページを作成するには追加、**アプリケーション ページ**を SharePoint プロジェクト項目です。 アプリケーション ページを作成するときに Visual Studio は、次のフォルダーをプロジェクトに追加します。  
  
|フォルダー|説明|  
|------------|-----------------|  
|レイアウト|SharePoint のファイル システムの _layouts 仮想ディレクトリにマップされます。|  
|レイアウトのサブフォルダー|アプリケーション ページを構成するファイルが含まれています。 既定では、このフォルダーは、プロジェクトと同じ名前にします。 いつでも、このフォルダーの名前を変更することができます。 プロジェクトを実行するときに、Visual Studio は、SharePoint のファイル システムの _layouts 仮想ディレクトリをこのフォルダーを展開します。|  
  
 Visual Studio では、次のファイルをプロジェクトに追加します。  
  
|ファイル|説明|  
|----------|-----------------|  
|ASP.NET ページのファイル (.aspx)|ページを定義する XML マークアップが含まれています。|  
|アプリケーション ページ コード ファイル|アプリケーション ページで、分離コードが含まれています。 このファイルにイベントを処理するコードを追加します。|  
|アプリケーション ページ デザイナー コード ファイル|デザイナーによって生成されるコードが含まれています。 このファイルを直接編集しないでください。|  
  
## <a name="design-and-debug-an-application-page"></a>デザインおよびアプリケーション ページのデバッグ
 Visual Studio のデザイナー ビューを使用してアプリケーション ページの内容をデザインします。 プロジェクトでアプリケーション ページを開くときに、このデザイナーが表示されます (ショートカット メニューを開き、選択しをダブルクリックして**開く**) を選択し、**デザイン**の下部にあるボタンをクリックします。エディター。  
  
> [!NOTE]  
>  ページをデザインするだけで、**ソース**デザイナーのビューです。 **デザイン**アプリケーション ページのデザイナーのビューを無効にします。  
  
 Visual Studio での他の SharePoint プロジェクト項目をデバッグする場合と同様、アプリケーション ページをデバッグすることができます。 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 アプリケーション ページを表示する必要があります手動でに移動する、アプリケーション ページの場所 (例: http://*Server_Name*/_layouts/*Project_Name*/ApplicationPage1.aspx)。  
  
 SharePoint プロジェクトをデバッグする方法の詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
## <a name="choose-a-master-page"></a>マスター ページを選択します。
 既定では、**アプリケーション ページ**項目は、プロジェクトのデバッグを使用しているサイトのマスター ページを参照します。 V4.master という名前のページに表示されていることを見つけることができます、**マスタ ページ ギャラリ**SharePoint サイトのです。  
  
 設定して、アプリケーション ページで使用されるマスター ページを明示的に変更できます、`MasterPageFile`アプリケーションの属性`Page`要素。 (例: `MasterPageFile="~/_layouts/applicationv4.master"`)。 実際には、動的なマスター ページは、SharePoint サーバーで有効でない場合は、この属性を設定する必要があります。 SharePoint のマスター ページの詳細については、次を参照してください。[マスター ページ](http://go.microsoft.com/fwlink/?LinkID=169281)です。  
  
## <a name="see-also"></a>関連項目
 [多層 SharePoint Foundation 開発](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET の概要](/aspnet/overview)   
 [ASP.NET Web ページ](/aspnet/web-pages/index)   
  
