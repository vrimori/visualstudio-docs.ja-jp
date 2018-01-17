---
title: "プロジェクトとファイルの Visual Studio テンプレート | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3959b01fdfc0ff77bdd5a3ffa0c96366b9da87d7
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="project-and-item-templates"></a>プロジェクト テンプレートと項目テンプレート

プロジェクト テンプレートおよび項目テンプレートには、基本的なコードや構造をユーザーに提供する再使用可能なスタブが用意されており、ユーザーは独自の目的に合わせてそれをカスタマイズできます。

## <a name="visual-studio-templates"></a>Visual Studio のテンプレート

Visual Studio では、複数の定義済みのプロジェクト テンプレートおよび項目テンプレートがインストールされます。 たとえば、**[新しいプロジェクト]** ダイアログ ボックスに表示される Visual Basic や C# の **Windows フォーム アプリ** テンプレートおよび**クラス ライブラリ** テンプレートは、プロジェクト テンプレートです。 項目テンプレートは **[新しい項目の追加]** ダイアログ ボックスに表示され、コード ファイル、XML ファイル、HTML ページ、スタイル シートなどの項目を含みます。

これらのテンプレートは、ユーザーがプロジェクトの作成を開始したり、既存プロジェクトを拡張したりするための開始点を提供します。 プロジェクト テンプレートには、特定の種類のプロジェクトで必要になるファイルが用意されており、標準のアセンブリ参照が含まれています。また、ここで既定のプロパティとコンパイラ オプションが設定されます。 項目テンプレートの複雑さは、特定のファイル拡張子を持つ 1 つの空のファイルから、スタブ コードを含むソース コード ファイル、デザイナー情報ファイル、埋め込みリソースなどの項目を含む複数ファイル用の項目まで、さまざまです。

**[新しいプロジェクト]** ダイアログ ボックスおよび **[新しい項目の追加]** ダイアログ ボックスからインストール済みテンプレートを使えるだけでなく、独自のテンプレートを作成したり、コミュニティで作成されたテンプレートをダウンロードして使ったりできます。 詳細については、「[方法: プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」および「[方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)」を参照してください。

## <a name="contents-of-a-template"></a>テンプレートの内容

すべてのプロジェクト テンプレートと項目テンプレートは、Visual Studio でインストールされたものも、自分で作成したものも、同じ原則で機能し、似た内容から構成されます。 すべてのテンプレートには次の項目が含まれます。

- テンプレートを使用すると作成されるファイル。 これには、ソース コード ファイル、埋め込みリソース、プロジェクト ファイルなどが含まれます。

- 1 つの .vstemplate ファイル。 このファイルにはメタデータが含まれます。このメタデータは、**[新しいプロジェクト]** ダイアログ ボックスおよび **[新しい項目の追加]** ダイアログ ボックスにテンプレートを表示し、テンプレートからプロジェクトや項目を作成するために必要な情報が含まれます。 .vstemplate ファイルについては、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。

これらのファイルが .zip ファイルに圧縮されて適切なフォルダーに配置されると、Visual Studio はそれを次の場所に自動的に表示します。

- プロジェクト テンプレートは、**[新しいプロジェクト]** ダイアログ ボックスに表示されます。

- 項目テンプレートは、**[新しい項目の追加]** ダイアログ ボックスに表示されます。

テンプレート フォルダーについては、「[方法: テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

## <a name="starter-kits"></a>スタート キット

スタート キットは拡張されたテンプレートであり、コミュニティの他のメンバーと共有できます。 スタート キットには、コンパイルされるコード サンプル、ドキュメント、および有用で実際的なアプリケーションをビルドする際の新しいツールやプログラミング技法を習得するうえで役立つ他のリソースが含まれています。 スタート キットの基本的な内容と手順は、テンプレートの場合と同じです。 詳しくは、「[方法: スタート キットを作成する](../ide/how-to-create-starter-kits.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[方法: プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)  
[方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)  
[テンプレート パラメーター](../ide/template-parameters.md)  
[テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)  
[Visual Studio テンプレートの NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)