---
title: "Visual Studio でのカスタム プロジェクトと項目テンプレートの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目テンプレート, 項目テンプレートの概要"
  - "プロジェクト テンプレート [Visual Studio], プロジェクト テンプレートの概要"
  - "テンプレート [Visual Studio], テンプレートの概要"
  - "テンプレート [Visual Studio], 項目"
  - "テンプレート [Visual Studio], プロジェクト"
  - "Visual Studio のテンプレート, テンプレートの概要"
  - "Visual Studio のテンプレート, 項目"
  - "Visual Studio のテンプレート, プロジェクト"
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual Studio でのカスタム プロジェクトと項目テンプレートの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロジェクト テンプレートおよび項目テンプレートには、再使用可能なスタブが用意されています。これらによりユーザーは、提供される基本的なコードや構造をそれぞれの用途に使用できます。  
  
## Visual Studio テンプレート  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] をインストールすると、いくつかの定義済みのプロジェクト テンプレートおよび項目テンプレートがインストールされます。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\[新しいプロジェクト\] ダイアログ ボックスで使用できる、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] および  **の Windows フォーム アプリケーションとクラス ライブラリの各テンプレートは、プロジェクト テンプレートの例です。** インストールされた項目テンプレートは **\[新しい項目の追加\]** ダイアログ ボックスで使用でき、コード ファイル、XML ファイル、HTML ページ、スタイル シートなどの項目を含みます。  
  
 これらのテンプレートは、ユーザーがプロジェクトの作成を開始したり、現在のプロジェクトを拡大したりするための開始点として使用できます。  プロジェクト テンプレートには、特定の種類のプロジェクトで必要になるファイルが用意されており、標準のアセンブリ参照が含まれています。また、ここで既定のプロパティとコンパイラ オプションが設定されます。  項目テンプレートは、正しいファイル名拡張子を持つ 1 つの空のファイルから、スタブ コードを含むソース コード ファイル、デザイナー情報ファイル、埋め込みリソースなどの項目を含む複数ファイル用の項目まで、複雑性がさまざまに異なります。  
  
 **\[新しいプロジェクト\]** ダイアログ ボックスおよび **\[新しい項目の追加\]** ダイアログ ボックスからインストール済みテンプレートを使用できるだけでなく、独自のテンプレートを作成したり、コミュニティで作成されたテンプレートをダウンロードして使用したりできます。  詳細については、「[方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」と「[方法 : 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)」を参照してください。  
  
## テンプレートの内容  
 すべてのプロジェクト テンプレートと項目テンプレートは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でインストールされたものも、自分で作成したものも、同じ原則で機能し、似た内容から構成されます。  すべてのテンプレートには次の項目が含まれます。  
  
-   テンプレートを使用すると作成されるファイル。  これには、ソース コード ファイル、埋め込みリソース、プロジェクト ファイルなどが含まれます。  
  
-   1 つの .vstemplate ファイル。  このファイルにはメタデータが含まれます。このメタデータが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に提供する情報に基づいて、**\[新しいプロジェクト\]** ダイアログ ボックスおよび **\[新しい項目の追加\]** ダイアログ ボックスにテンプレートが表示され、そのテンプレートからプロジェクトや項目が作成されます。  .vstemplate ファイルの詳細については、「[テンプレート名](../ide/template-parameters.md)」を参照してください。  
  
 これらのファイルは、.zip ファイルに圧縮されて適切なフォルダーに配置されると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で自動的に表示されます。  プロジェクト テンプレートは、**\[新しいプロジェクト\]** ダイアログ ボックスの **\[マイ テンプレート\]** セクションに表示され、項目テンプレートは **\[新しい項目の追加\]** ダイアログ ボックスに表示されます。  テンプレート フォルダーの詳細については、「[方法 : テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。  
  
## スタート キット  
 スタート キットは拡張されたテンプレートであり、コミュニティの他のメンバーと共有できます。  スタート キットには、コンパイルされるコード サンプル、ドキュメント、および有用で実際的なアプリケーションをビルドする際の新しいツールやプログラミング技法を習得するうえで役立つ他のリソースが含まれています。  スタート キットの基本的な内容と手順は、テンプレートの場合と同じです。  詳細については、「[方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)」を参照してください。  
  
## 参照  
 [方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)   
 [方法 : 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)   
 [テンプレート名](../ide/template-parameters.md)   
 [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)   
 [方法 : スタート キットを作成する](../ide/how-to-create-starter-kits.md)