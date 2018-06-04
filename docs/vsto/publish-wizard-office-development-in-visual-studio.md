---
title: 発行ウィザード (Visual Studio での Office 開発)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2481557d1d75d64b5eb3f52f2755953ca344d323
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692721"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>発行ウィザード (Visual Studio での Office 開発)
  使用して、**発行ウィザード**ソリューション ファイルを指定した場所にコピーするマニフェストのファイルを作成し、セットアップ プログラムを作成します。  
  
 このウィザードにアクセスする、**ビルド**] メニューの [選択**発行** *SolutionName*です。 アクセスすることも、**発行ウィザード**から**ソリューション エクスプ ローラー**です。 プロジェクト ノードのショートカット メニューを開き、選択**発行**です。  
  
 以下の各セクションでは、ウィザードのページについて説明します。  
  
## <a name="where-do-you-want-to-publish-the-application"></a>アプリケーションを発行する場所ですか。  
 **このアプリケーションを発行する場所を指定します。**  
 必須。 発行場所のディレクトリは、ここで、**発行ウィザード**ビルドのマニフェスト、アセンブリ、一時的な証明書、およびその他のファイルなどのソリューション ファイルをコピーします。 このディレクトリへの書き込みアクセス権が必要です。  
  
 ディスクのパス、ファイル共有、FTP サイトまたは web サイトの URL と場所を入力またはクリックして、**参照**場所を参照するボタンをクリックします。 パスは、これらの形式で指定できます。  
  
-   標準の相対パスまたは絶対パス Windows 書式を設定するように*C:\Deploy\MyApplication*または*\MyApplication*です。  
  
-   汎用名前付け規則 (UNC) パスなど *\\\ServerName\MyApplication\\*です。  
  
-   URL の web サイトなどhttp://www.microsoft.com/MyApplicationです。  
  
 発行場所は、既定では、 *http://localhost/projectname/* かどうかがある、IIS をインストールまたは操作を行う場合は、publish \ ディレクトリが IIS インストールされていません。  
  
> [!NOTE]  
>  他の考慮事項があるターゲット コンピューターが Windows Vista を実行している場合。 ローカルの発行オプションを使用するには、Windows Vista コンピュータの管理者である必要がある必要があります。 さらに、既定の場所は、常に、*発行\\* IIS をインストールがあるかどうかに関係なく、ディレクトリです。  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>エンドユーザーのコンピューター上の既定のインストール パスとは何ですか。  
 インストール パスはオプションです。 たい場合は、後で、インストール パスを設定できます。 詳細については、「[する方法: Office ソリューションのインストール パスを変更して](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)です。  
  
 インストール パスは、エンドユーザーがカスタマイズをインストールするディレクトリです。 このディレクトリは、ソリューションで更新プログラムを確認するために使用するパスでもあります。 **発行ウィザード**に入力したものと同じパスがない限り、この場所にソリューションを展開しないは、**このアプリケーションを発行する場所を指定**前のページのボックスです。  
  
 **Web サイトから**  
 エンドユーザーは、ソリューションをインストールするには、URL を指定します。  
  
 **UNC パスまたはファイル共有から**  
 エンドユーザーは、ソリューションをインストールするには UNC パスを指定します。  
  
 **CD-ROM または DVD-ROM から**  
 このオプションでは、インストール パスは必要ありません。  
  
 Visual Studio は、CD または DVD には書き込みできません。 CD または DVD に出力を手動でコピーする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce を使用して Office ソリューションを配置します。](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [[発行] ページ、プロジェクト デザイナー &#40;Visual Studio での Office 開発&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Office ソリューションを配置します。](../vsto/deploying-an-office-solution.md)  
  
  