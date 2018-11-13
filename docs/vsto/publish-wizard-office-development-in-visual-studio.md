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
ms.openlocfilehash: 0d1b72745b3bd8a24dc69a5bc4e1508c8b2f7571
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672751"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>発行ウィザード (Visual Studio での Office 開発)
  使用して、**発行ウィザード**ソリューション ファイルを指定した場所にコピーするマニフェスト ファイルを作成し、セットアップ プログラムを作成します。  
  
 このウィザードでは、上へのアクセスに、**ビルド**] メニューの [選択**発行** *SolutionName*します。 アクセスすることも、**発行ウィザード**から**ソリューション エクスプ ローラー**します。 プロジェクト ノードのショートカット メニューを開き、選択し、**発行**します。  
  
 以下の各セクションでは、ウィザードのページについて説明します。  
  
## <a name="where-do-you-want-to-publish-the-application"></a>アプリケーションを発行する場所をでしょうか。  
 **このアプリケーションを発行する場所を指定します。**  
 必須。 発行場所は、ディレクトリを**発行ウィザード**ビルドのマニフェスト、アセンブリ、一時的な証明書、およびその他のファイルなどのソリューション ファイルをコピーします。 このディレクトリへの書き込みアクセス権が必要です。  
  
 ディスクのパス、ファイル共有、FTP サイト、または web サイトの URL として場所を入力するかクリックして、**参照**場所を参照するボタンをクリックします。 これらの形式でパスができます。  
  
- 標準の相対または絶対パス Windows 形式など*C:\Deploy\MyApplication*または*\MyApplication*します。  
  
- 汎用名前付け規則 (UNC) パスなど *\\\ServerName\MyApplication\\*します。  
  
- URL の web サイトなど http://www.microsoft.com/MyApplicationします。  
  
  発行場所は、既定では、 *http://localhost/projectname/* かどうかがある、IIS をインストールまたは実行する場合は、publish \ ディレクトリが IIS インストールされていません。  
  
> [!NOTE]  
>  他の考慮事項があるターゲット コンピューターが Windows Vista を実行している場合。 ローカルな発行オプションを使用するには、Windows Vista コンピューターの管理者があります。 さらに、既定の場所は常には、*発行\\*ディレクトリにインストールされている IIS のあるかどうかに関係なく。  
  
## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>エンドユーザーのコンピューター上の既定のインストール パスとは何ですか。  
 インストール パスは省略可能です。 たい場合は、後でインストール パスを設定できます。 詳細については、次を参照してください。[方法: Office ソリューションのインストール パスを変更して](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)します。  
  
 インストール パスは、エンドユーザーが、カスタマイズをインストール ディレクトリです。 このディレクトリは、ソリューションで更新プログラムを確認するために使用するパスでもあります。 **発行ウィザード**パスに入力したものと同じでない限り、この場所にソリューションを配置しないは、**このアプリケーションを発行する場所を指定**前のページのボックスです。  
  
 **Web サイトから**  
 エンドユーザーは、ソリューションをインストールするには URL を指定します。  
  
 **UNC パスまたはファイル共有から**  
 エンドユーザーは、ソリューションをインストールするには UNC パスを指定します。  
  
 **CD-ROM または DVD-ROM から**  
 このオプションでは、インストール パスは必要ありません。  
  
 Visual Studio は、CD または DVD には書き込みできません。 CD または DVD に出力を手動でコピーする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce を使用して Office ソリューションを配置します。](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [[発行] ページ、プロジェクト デザイナー &#40;Visual Studio での Office 開発&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)  
  
  