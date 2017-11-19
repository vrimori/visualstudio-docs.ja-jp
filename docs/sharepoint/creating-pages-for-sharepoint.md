---
title: "SharePoint 用ページの作成 |Microsoft ドキュメント"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bef1fce26bbd9ea57073273f462ec484a46a647b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="creating-pages-for-sharepoint"></a>SharePoint 用ページの作成
  アプリケーション ページ、サイトのページ、マスター ページ、および SharePoint サイトのページ レイアウトを作成することができます。  
  
 Visual Studio でテンプレートを使用してアプリケーション ページを作成することができます。 SharePoint Designer を使用して、サイトのページ、マスター ページ、およびページ レイアウトを作成します。 次に、SharePoint プロジェクトで使用する Visual Studio にこれらのページをインポートできます。  
  
 カスケード スタイル シート、ECMAScript、およびテーマを使用して、ページの動作と外観を変更することもできます。  
  
## <a name="types-of-sharepoint-pages"></a>SharePoint ページの種類  
 次の表では、4 つのメインの種類の SharePoint サイトを含むページについて説明します。  
  
|ページの種類|説明|  
|---------------|-----------------|  
|アプリケーション ページ|カスタム コードを格納するページまたは複数のサイト間で共有するページの場合は、アプリケーション ページを作成します。 それ以外の場合、サイトのページには、最適な選択肢があります。|  
|サイトのページ|次のタスクのいずれかを実行する場合は、サイトのページを作成します。<br /><br /> SharePoint ライブラリに、ページを追加します。<br />-動的の Web パーツおよび Web パーツの領域などのホスト機能にページを有効にします。<br />-SharePoint Designer を使用して、ページをカスタマイズするユーザーを有効にします。<br /><br /> カスタム コードを含むページにする場合、サイトのページを作成できません。 サイトのページには、カスタム コードを追加できますが、コードが、ユーザーが SharePoint デザイナーを使用して、ページをカスタマイズした場合の実行を停止します。|  
|マスター ページ|サイトのページに共通の構造を定義する場合に、マスター ページとアプリケーション ページを作成します。|  
|ページ レイアウト|固有のページ レイアウト[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]し、さらにサイトのページとアプリケーション ページに共通の構造を定義できるようにします。|  
  
 ページの各種類の概要については、次を参照してください。[ビルディング ブロック: ページと、ユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)、および[ページ レイアウトやマスター ページ](http://go.microsoft.com/fwlink/?LinkID=182096)です。  
  
## <a name="creating-application-pages"></a>アプリケーション ページの作成  
 追加することで、Visual Studio でアプリケーション ページを作成することができます、**アプリケーション ページ**を SharePoint プロジェクト項目です。 ページにコントロールを追加し、コードを追加してコントロールのイベントを処理できます。  
  
 ページのコード ファイルにブレークポイントを設定、デバッガーを起動、および追加の構成手順を実行せずローカル SharePoint サイトのページをテストできます。 詳細については、次を参照してください。 [for SharePoint アプリケーション ページを作成する](../sharepoint/creating-application-pages-for-sharepoint.md)です。  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>サイト ページ、マスター ページとページ レイアウトを作成します。  
 サイトのページ、マスター ページ、およびページ レイアウトを作成するには、SharePoint Designer を使用します。 次に、これらのページを Visual Studio にインポートできます。 展開または Visual Studio で使用可能なソース管理機能を利用する場合は、ページをインポートします。 詳細については、次を参照してください。[既存の SharePoint サイトからインポートする項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)です。  
  
 インポートした後、これらのページを変更するが困難なので、それらをインポートする前にこれらのページを設計する必要があります。  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>カスケード スタイル シート、ECMAScript、テーマの作成  
 Visual Studio では、開発のカスケード スタイル シート (CSS)、ECMAScript (JavaScript、JScript)、または SharePoint サイトのテーマ ファイルのテンプレートは提供されません。 SharePoint SDK で利用可能なガイダンスを使用して、または SharePoint デザイナーなどのツールを使用して、これらのファイルを作成することができます。  
  
 これらのファイルを直接ソリューションに追加することができますか、それらをインポートすることができます。 いずれの場合に、各項目を追加するに適切なマップされたフォルダーを作成する必要があります。 マップされたフォルダーを作成する方法の詳細については、次を参照してください。[する方法: 追加し、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)です。  
  
 カスケード スタイル シートの作成の詳細については、次を参照してください。[カスケード スタイル シート クラス内の使用状況 SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098)です。 SharePoint ソリューションの JavaScript および JScript ファイルの作成の詳細については、次を参照してください。[設定を、基本 ASPX ページ ECMAScript の](http://go.microsoft.com/fwlink/?LinkID=182099)します。 テーマの詳細については、次を参照してください。[ビルディング ブロック: ページと、ユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)です。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[SharePoint のアプリケーション ページの作成](../sharepoint/creating-application-pages-for-sharepoint.md)|アプリケーション ページを追加する方法について説明します。 SharePoint のマスター ページとマージされる .aspx コンテンツ。|  
|[方法: アプリケーション ページを作成する](../sharepoint/how-to-create-an-application-page.md)|SharePoint サイト上で実行される ASP.NET ページを作成する方法を示します。|  
|[チュートリアル: SharePoint アプリケーション ページの作成](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|デザインおよび SharePoint サイトの ASP.NET Web ページをデバッグする方法を示します。|  
  
  