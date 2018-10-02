---
title: プロジェクトと項目テンプレートの作成 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e288329637c6a6f421a5b32f19084897a31e5f22
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548050"
---
# <a name="creating-project-and-item-templates"></a>プロジェクトと項目テンプレートの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を作成するプロジェクトと項目テンプレート](https://docs.microsoft.com/visualstudio/ide/creating-project-and-item-templates)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のプロジェクト テンプレートおよび項目テンプレートには、再使用可能なスタブが用意されています。これらによりユーザーは、提供される基本的なコードや構造をそれぞれの用途に使用できます。  
  
## <a name="visual-studio-templates"></a>Visual Studio テンプレート  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] をインストールすると、いくつかの定義済みのプロジェクト テンプレートおよび項目テンプレートがインストールされます。 **[新しいプロジェクト]** ダイアログ ボックスで使用できる、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] および [!INCLUDE[csprcs](../includes/csprcs-md.md)] の Windows フォーム アプリケーションとクラス ライブラリの各テンプレートは、プロジェクト テンプレートの例です。 インストールされた項目テンプレートは **[新しい項目の追加]** ダイアログ ボックスで使用でき、コード ファイル、XML ファイル、HTML ページ、スタイル シートなどの項目を含みます。  
  
 これらのテンプレートは、ユーザーがプロジェクトの作成を開始したり、現在のプロジェクトを拡大したりするための開始点として使用できます。 プロジェクト テンプレートには、特定の種類のプロジェクトで必要になるファイルが用意されており、標準のアセンブリ参照が含まれています。また、ここで既定のプロパティとコンパイラ オプションが設定されます。 項目テンプレートは、正しいファイル名拡張子を持つ 1 つの空のファイルから、スタブ コードを含むソース コード ファイル、デザイナー情報ファイル、埋め込みリソースなどの項目を含む複数ファイル用の項目まで、複雑性がさまざまに異なります。  
  
 **[新しいプロジェクト]** ダイアログ ボックスおよび **[新しい項目の追加]** ダイアログ ボックスからインストール済みテンプレートを使用できるだけでなく、独自のテンプレートを作成したり、コミュニティで作成されたテンプレートをダウンロードして使用したりできます。 詳しくは、「[方法: プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」および「[方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)」をご覧ください。  
  
## <a name="contents-of-a-template"></a>テンプレートの内容  
 すべてのプロジェクト テンプレートと項目テンプレートは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でインストールされたものも、自分で作成したものも、同じ原則で機能し、似た内容から構成されます。 すべてのテンプレートには次の項目が含まれます。  
  
-   テンプレートを使用すると作成されるファイル。 これには、ソース コード ファイル、埋め込みリソース、プロジェクト ファイルなどが含まれます。  
  
-   1 つの .vstemplate ファイル。 このファイルにはメタデータが含まれます。このメタデータが [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] に提供する情報に基づいて、**[新しいプロジェクト]** ダイアログ ボックスおよび **[新しい項目の追加]** ダイアログ ボックスにテンプレートが表示され、そのテンプレートからプロジェクトや項目が作成されます。 .vstemplate ファイルについて詳しくは、「[テンプレート パラメーター](../ide/template-parameters.md)」をご覧ください。  
  
 これらのファイルは、.zip ファイルに圧縮されて適切なフォルダーに配置されると、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で自動的に表示されます。 プロジェクト テンプレートは、**[新しいプロジェクト]** ダイアログ ボックスの **[マイ テンプレート]** セクションに表示され、項目テンプレートは **[新しい項目の追加]** ダイアログ ボックスに表示されます。 テンプレート フォルダーについて詳しくは、「[方法: テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」をご覧ください。  
  
## <a name="starter-kits"></a>スタート キット  
 スタート キットは拡張されたテンプレートであり、コミュニティの他のメンバーと共有できます。 スタート キットには、コンパイルされるコード サンプル、ドキュメント、および有用で実際的なアプリケーションをビルドする際の新しいツールやプログラミング技法を習得するうえで役立つ他のリソースが含まれています。 スタート キットの基本的な内容と手順は、テンプレートの場合と同じです。 詳しくは、「[方法: スタート キットを作成する](../ide/how-to-create-starter-kits.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)   
 [方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)   
 [テンプレート パラメーター](../ide/template-parameters.md)   
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)



