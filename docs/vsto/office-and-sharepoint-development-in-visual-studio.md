---
title: Visual Studio での office および SharePoint 開発
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7217c2b3177d3eb1f591cbb6256b9e40fba23b12
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673678"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Visual Studio での office および SharePoint 開発
  ユーザーが [Office ストア](https://store.office.com/) または組織のカタログからダウンロードする軽量なアプリやアドインを作成するか、ユーザーがコンピューターにインストールする .NET Framework ベースのソリューションを作成することによって、Microsoft Office および SharePoint を拡張できます。  
  
 このトピックの内容:  
  
-   [Office と SharePoint 用アドインの作成](#Apps)  
  
-   [VSTO アドインの作成します。](#Add-ins)  
  
-   [SharePoint ソリューションの作成](#Solutions)  
  
##  <a name="Apps"></a> Office と SharePoint 用アドインの作成  
 Office 2013 と SharePoint 2013 では、Office と SharePoint を拡張するためのアドインを構築、配布、収益化するために役立つ新しいアドイン モデルが導入されます。  これらのアドインは、Office Online または SharePoint Online で実行でき、ユーザーは多くのデバイスからアプリと対話できます。  
  
 新たに使用する方法について[Office アドイン モデル](https://msdn.microsoft.com/library/office/jj220082.aspx)ユーザーの Office エクスペリエンスを拡張します。  
  
 これらのアドインは VSTO アドインと、ソリューションと比較して小さいフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用して、それらをビルドすることができます。  作業を始めるには、Visual Studio で Office Developer Tools を使用するか、コードネーム "Napa" Office 365 開発ツールと呼ばれる、軽量な Web ベースのツールを使用します。これらのツールを使用すると、プロジェクトを作成し、コードを記述した後、構築したアドインをブラウザー内で実行できます。  
  
 ![概念モデルの Office および SharePoint 用アプリ](../vsto/media/officeandsharepointapps2015.png "Office および SharePoint の概念モデル用のアプリ")  
  
### <a name="build-an-office-add-in"></a>Office のアドインのビルドします。  
 Office の機能を拡張するには、Office アドインを構築します。 基本的には、Excel、Word、Outlook、PowerPoint などの Office アプリケーションでホストされている web ページ。 構築したアプリを使用して、ドキュメント、ワークシート、電子メール メッセージ、予定、プレゼンテーション、およびプロジェクトに機能を追加できます。  
  
 構築したアプリは Office ストアで販売できます。  [Office ストア](https://store.office.com/) を使用すると、アドインの収益化、更新プログラムの管理、および利用統計情報の追跡が簡単になります。 また、SharePoint のアプリ カタログや Exchange Server 上で、アプリをユーザーに公開することもできます。  
  
 Bing マップ内にワークシートのデータを表示する Office 向けアプリを次に示します。  
  
 ![Office 用アプリのコンテンツ](../vsto/media/appforoffice.png "Office 用アプリのコンテンツ")  
  
 **詳細を表示**  
  
|終了|解決方法については、|  
|--------|---------|  
|Office アドインの詳細を確認し、アドインを構築する。|[Office アドイン](http://msdn.microsoft.com/office/dn448457)|  
|Office のさまざまな拡張方法を比較し、アプリと Office アドインのどちらを使用する必要があるかを判断する。|[Office アドイン、VSTO、および VBA のためのロードマップ](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
  
### <a name="build-a-sharepoint-add-in"></a>SharePoint アドインのビルドします。  
 ユーザー向けに SharePoint を拡張するには、SharePoint アドインを構築します。 これは、ユーザーやビジネスの必要性を解決するための小規模な使いやすい、スタンドアロン アプリケーションでは基本的にします。  
  
 構築した SharePoint 用のアプリは [Office ストア](https://store.office.com/)で販売できます。 また、SharePoint のアドイン カタログを使用して、アドインをユーザーに公開することもできます。  サイト所有者は、ファーム サーバーやサイト コレクションの管理者の助けを借りることなく、アドインを SharePoint サイトにインストール、アップグレード、およびアンインストールできます。  
  
 ユーザーがビジネス用連絡先を管理に役立つ SharePoint 向けアプリの例を次に示します。  
  
 ![SharePoint 用 business contact manager アプリケーション](../vsto/media/appforsharepoint.png "SharePoint 用 Business contact manager アプリケーション")  
  
 **詳細を表示**  
  
|終了|解決方法については、|  
|--------|---------|  
|SharePoint アドインの詳細を確認し、アドインを構築する。|[SharePoint アドイン](https://msdn.microsoft.com/library/office/fp179930.aspx)|  
|SharePoint アドインを従来の SharePoint ソリューションと比較する。|[SharePoint アドインが SharePoint ソリューションと比較](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|SharePoint ソリューションと SharePoint アドインのどちらを構築するかを選択する。|[SharePoint アドインと SharePoint ソリューションの決定します。](https://msdn.microsoft.com/library/office/jj163114.aspx)|
  
##  <a name="Add-ins"></a> VSTO アドインの作成します。  
 VSTO アドインを Office 2007 または Office 2010 を対象とする、または Office 2013 および Office 2016 を超える Office アドインでできることを作成します。VSTO アドインはデスクトップ上でのみ動作します。 ユーザーは、通常の展開およびサポートをより困難になるように、VSTO アドインをインストールする必要があります。  ただし、VSTO アドインは、より密接に Office に統合できます。 たとえば、Office リボンにタブやコントロールを追加し、文書の結合やグラフの変更などの高度な自動化タスクを実行できます。 また、.NET Framework を活用し、C# および Visual Basic を使用して、Office オブジェクトと対話することもできます。  
  
 どのような VSTO アドインを実行できます例を示します。 この VSTO アドインは、PowerPoint にリボン コントロール、カスタム作業ウィンドウ、およびダイアログ ボックスを追加します。  
  
 ![PowerPoint アドイン ソリューション](../vsto/media/powerpointaddin.png "PowerPoint アドイン ソリューション")  
  
 **詳細を表示**  
  
|終了|読み取り|  
|--------|----------|  
|Office のさまざまな拡張方法を比較し、VSTO アドインと Office アドインのどちらを使用する必要があるかを判断する。|[Office アドイン、VSTO、および VBA のためのロードマップ](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|VSTO アドインを作成する。|[Visual Studio で作成した VSTO アドイン](https://msdn.microsoft.com/library/jj620922.aspx)|  
  
##  <a name="Solutions"></a> SharePoint ソリューションの作成  
 SharePoint Foundation 2010 および SharePoint Server 2010 を対象とする、または SharePoint アドインでできること以外の方法で SharePoint 2013 と SharePoint 2016 を拡張する SharePoint ソリューションを作成します。  
  
 SharePoint ソリューションには、内部設置型の SharePoint ファーム サーバーが必要です。 管理者はソリューションをインストールする必要があります。また、ソリューションは SharePoint 内で実行されるため、サーバーのパフォーマンスに影響を与える可能性があります。 ただし、ソリューションでは、より深いレベルの SharePoint オブジェクトへのアクセスが提供されます。 また、SharePoint ソリューションの構築時に、.NET Framework を活用し、C# および Visual Basic を使用して、SharePoint オブジェクトと対話できます。  
  
 **詳細を表示**  
  
|終了|解決方法については、|  
|--------|---------|  
|SharePoint ソリューションを SharePoint アドインと比較する。|[SharePoint アドインが SharePoint ソリューションと比較](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|SharePoint ソリューションを作成する。|[SharePoint ソリューションの作成](../sharepoint/create-sharepoint-solutions.md)|  
  
  
