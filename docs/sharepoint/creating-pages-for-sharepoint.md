---
title: SharePoint 用ページの作成 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51903d1bf98a76a3ea3987af5330e8ce3c0d125e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864788"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint 用ページを作成します。
  アプリケーション ページ、サイトのページ、マスター ページおよび SharePoint サイトのページ レイアウトを作成することができます。  
  
 Visual Studio でテンプレートを使用して、アプリケーション ページを作成できます。 SharePoint デザイナーを使用して、サイトのページ、マスター ページ、およびページのレイアウトを作成します。 次に、これらのページを SharePoint プロジェクトで使用する Visual Studio にインポートできます。  
  
 カスケード スタイル シート、ECMAScript、およびテーマを使用して、ページの動作と外観を変更することもできます。  
  
## <a name="types-of-sharepoint-pages"></a>SharePoint ページの種類
 次の表では、4 つの主な種類の SharePoint サイトを含むページについて説明します。  
  
|ページの種類|説明|  
|---------------|-----------------|  
|アプリケーション ページ|カスタム コードを格納するページまたはページを複数のサイトで共有できるようにする場合は、アプリケーション ページを作成します。 それ以外の場合、サイトのページには、最適な選択肢があります。|  
|サイトのページ|次のタスクのいずれかを実行する場合は、サイト ページを作成します。<br /><br /> -ページを SharePoint ライブラリに追加します。<br />-動的な Web パーツおよび Web パーツ ゾーンなどのホスト機能にページを有効にします。<br />-SharePoint Designer を使用して、ページをカスタマイズするユーザーを有効にします。<br /><br /> カスタム コードを格納するページの場合、サイトのページを作成できません。 サイト ページにカスタム コードを追加できますが、コードは、SharePoint デザイナーを使用してページをカスタマイズするときに実行を停止します。|  
|マスター ページ|サイト ページ用の一般的な構造を定義する場合に、マスター ページおよびアプリケーション ページを作成します。|  
|ページ レイアウト|固有のページ レイアウト[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]し、さらにサイトのページおよびアプリケーション ページに共通の構造を定義することを有効にします。|  
  
 ページの種類ごとの概要については、次を参照してください。[ビルディング ブロック。ページとユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)、および[ページ レイアウトとマスター ページ](http://go.microsoft.com/fwlink/?LinkID=182096)します。  
  
## <a name="create-application-pages"></a>アプリケーション ページを作成します。
 Visual Studio でアプリケーション ページを作成するには追加することで、**アプリケーション ページ**を SharePoint プロジェクト項目。 ページにコントロールを追加し、コードを追加してコントロールのイベントを処理できます。  
  
 ページのコード ファイルにブレークポイントを設定、デバッガーを起動し、追加の構成手順を実行せずにローカル SharePoint サイトのページをテストできます。 詳細については、次を参照してください。 [for SharePoint アプリケーション ページを作成する](../sharepoint/creating-application-pages-for-sharepoint.md)します。  
  
## <a name="create-site-pages-master-pages-and-page-layouts"></a>サイトのページ、マスター ページ、およびページ レイアウトを作成します。
 SharePoint デザイナーを使用して、サイトのページ、マスター ページ、およびページ レイアウトを作成できます。 次に、これらのページを Visual Studio にインポートできます。 展開または Visual Studio で使用可能なソース管理機能を活用する場合は、ページをインポートします。 詳細については、次を参照してください。[既存の SharePoint サイトからインポートする項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)します。  
  
 インポートした後、これらのページを変更するのには難しいので、それらをインポートする前に、これらのページを設計する必要があります。  
  
## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>カスケード スタイル シート、ECMAScript、およびテーマを作成します。
 Visual Studio では、開発のカスケード スタイル シート (CSS)、ECMAScript (JavaScript、JScript)、または SharePoint サイトのテーマ ファイルのテンプレートは提供されません。 SharePoint SDK で使用できるガイダンスを使用するか、SharePoint Designer などのツールを使用して、これらのファイルを作成できます。  
  
 これらのファイルを直接をソリューションに追加することができます。 またはインポートすることができます。 いずれの場合も、追加する各項目に対して適切なマップされたフォルダーを作成する必要があります。 マップされたフォルダーを作成する方法の詳細については、次を参照してください。[方法: 追加すると、マップされたフォルダーを削除する](../sharepoint/how-to-add-and-remove-mapped-folders.md)します。  
  
 カスケード スタイル シートの作成の詳細については、次を参照してください。[カスケード スタイル シート クラスでの使用状況 SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098)します。 SharePoint ソリューションの JavaScript および JScript ファイルを作成する方法の詳細については、次を参照してください。[設定を、基本的な ASPX ページの ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099)します。 テーマの詳細については、次を参照してください。[ビルディング ブロック。ページとユーザー インターフェイス](http://go.microsoft.com/fwlink/?LinkID=182095)します。  
  
## <a name="related-topics"></a>関連トピック
  
|タイトル|説明|  
|-----------|-----------------|  
|[For SharePoint アプリケーション ページを作成します。](../sharepoint/creating-application-pages-for-sharepoint.md)|アプリケーション ページを追加する方法について説明します。 *.aspx* SharePoint マスター ページとマージされるコンテンツ。|  
|[方法: アプリケーション ページを作成します。](../sharepoint/how-to-create-an-application-page.md)|SharePoint サイト上で実行される ASP.NET ページを作成する方法を示します。|  
|[チュートリアル: SharePoint アプリケーション ページを作成します。](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|デザインおよび SharePoint サイトの ASP.NET Web ページをデバッグする方法を示します。|  
