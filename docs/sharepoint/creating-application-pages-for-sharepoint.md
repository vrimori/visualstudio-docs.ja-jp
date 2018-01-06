---
title: "For SharePoint アプリケーション ページの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e159efdfd709a0ef8950347a191bb4053ef715bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-application-pages-for-sharepoint"></a>SharePoint のアプリケーション ページの作成
  *アプリケーション ページ*が SharePoint Web サイトで使用するよう設計された ASP.NET Web ページです。 アプリケーション ページとは、ASP.NET ページの特化された型です。 アプリケーション ページと標準の ASP.NET ページの主な違いは、アプリケーション ページには、SharePoint のマスター ページとマージされるコンテンツが含まれているです。 マスター ページには、サイト上の他のページと同じ外観と動作を共有するアプリケーション ページができるようにします。  
  
 Visual Studio では、デザイナーを使用して、アプリケーション ページをデザインすることができます。 デザイナーは、マスター ページで定義されている各コンテンツのプレース ホルダーのコンテンツ領域を表示します。 アプリケーション ページをデザインするには、これらの領域にコントロールをドラッグします。  
  
## <a name="application-pages"></a>アプリケーション ページ  
 アプリケーション ページは、サイトのページが特定の 1 つのサイトには、サーバー上のすべてのサイトで共有されます。 詳細については、 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)です。  
  
 既定は、SharePoint サイトを作成するときに表示されるページのほとんどは、サイトのページです。 サイトのページは、SharePoint ページ ライブラリに追加できます。 ユーザーは、SharePoint デザイナーなどのツールを使用して、サイトのページをカスタマイズできます。 [サイト] ページでは、動的 Web パーツ、および Web パーツの領域などの機能もホストできます。  
  
 アプリケーション ページには、これらの作業を行うことはできません。 ただし、アプリケーション ページは、最適な型を作成する場合は、ページをカスタム コードを含むページのです。 サイトのページには、カスタム コードを追加できますが、コードが、ユーザーが SharePoint デザイナーなどのツールを使用して、ページをカスタマイズした場合の実行を停止します。  
  
> [!NOTE]  
>  Visual Studio の管轄外に役立つテンプレートが SharePoint サイトのサイトのページを作成します。 詳細については、次を参照してください。 [SharePoint ページの種類](http://go.microsoft.com/fwlink/?LinkID=211584)です。  
  
## <a name="creating-an-application-page"></a>アプリケーション ページを作成する  
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
  
## <a name="designing-and-debugging-an-application-page"></a>設計とアプリケーション ページのデバッグ  
 Visual Studio のデザイナー ビューを使用してアプリケーション ページの内容をデザインします。 プロジェクトでアプリケーション ページを開くときに、このデザイナーが表示されます (ショートカット メニューを開き、選択しをダブルクリックして**開く**) を選択し、**デザイン**の下部にあるボタンをクリックします。エディター。  
  
> [!NOTE]  
>  ページをデザインするだけで、**ソース**デザイナーのビューです。 **デザイン**アプリケーション ページのデザイナーのビューを無効にします。  
  
 Visual Studio での他の SharePoint プロジェクト項目をデバッグする場合と同様、アプリケーション ページをデバッグすることができます。 Visual Studio デバッガーを開始すると、SharePoint サイトが開きます。  
  
 アプリケーション ページを表示する必要があります手動でに移動する、アプリケーション ページの場所 (例: http://*Server_Name*/_layouts/*Project_Name*/ApplicationPage1.aspx)。  
  
 SharePoint プロジェクトをデバッグする方法の詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)です。  
  
## <a name="choosing-a-master-page"></a>マスター ページの選択  
 既定では、**アプリケーション ページ**項目は、プロジェクトのデバッグを使用しているサイトのマスター ページを参照します。 V4.master という名前のページに表示されていることを見つけることができます、**マスタ ページ ギャラリ**SharePoint サイトのです。  
  
 設定して、アプリケーション ページで使用されるマスター ページを明示的に変更できます、`MasterPageFile`アプリケーションの属性`Page`要素。 (例: `MasterPageFile="~/_layouts/applicationv4.master"`)。 実際には、動的なマスター ページは、SharePoint サーバーで有効でない場合は、この属性を設定する必要があります。 SharePoint のマスター ページの詳細については、次を参照してください。[マスター ページ](http://go.microsoft.com/fwlink/?LinkID=169281)です。  
  
## <a name="see-also"></a>参照  
 [多層 SharePoint Foundation 開発](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET の概要](/aspnet/overview)   
 [ASP.NET Web ページ](/aspnet/web-pages/index)   
  
  