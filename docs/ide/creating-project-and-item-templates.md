---
title: プロジェクトとファイルの Visual Studio テンプレート
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62e51a5a03011874acc723eaf159e3f7130d1340
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573259"
---
# <a name="project-and-item-templates"></a>プロジェクト テンプレートと項目テンプレート

プロジェクト テンプレートおよび項目テンプレートには、基本的なコードや構造をユーザーに提供する再使用可能なスタブが用意されており、ユーザーは独自の目的に合わせてそれをカスタマイズできます。

## <a name="visual-studio-templates"></a>Visual Studio のテンプレート

Visual Studio では、複数の定義済みのプロジェクト テンプレートおよび項目テンプレートがインストールされます。 たとえば、**[新しいプロジェクト]** ダイアログ ボックスに表示される Visual Basic や C# の **Windows フォーム アプリ** テンプレートおよび**クラス ライブラリ** テンプレートは、プロジェクト テンプレートです。 項目テンプレートは **[新しい項目の追加]** ダイアログ ボックスに表示され、コード ファイル、XML ファイル、HTML ページ、スタイル シートなどの項目を含みます。

これらのテンプレートは、ユーザーがプロジェクトの作成を開始したり、既存プロジェクトを拡張したりするための開始点を提供します。 プロジェクト テンプレートには、特定の種類のプロジェクトで必要になるファイルが用意されており、標準のアセンブリ参照が含まれています。また、ここで既定のプロパティとコンパイラ オプションが設定されます。 項目テンプレートの複雑さは、特定のファイル拡張子を持つ 1 つの空のファイルから、スタブ コードを含む複数のソース コード ファイル、デザイナー情報ファイル、埋め込みリソースまで、さまざまです。

**[新しいプロジェクト]** ダイアログ ボックスと **[新しい項目の追加]** ダイアログ ボックスでインストール済みテンプレートを使用したり、独自のテンプレートを作成したり、コミュニティで作成されたテンプレートをダウンロードして使用したりできます。 詳細については、「[方法: プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」および「[方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)」を参照してください。

## <a name="contents-of-a-template"></a>テンプレートの内容

すべてのプロジェクト テンプレートと項目テンプレートは、Visual Studio でインストールされたものも、自分で作成したものも、同じ原則で機能し、似た内容から構成されます。 すべてのテンプレートには次の項目が含まれます。

- テンプレートを使用すると作成されるファイル。 これらのファイルには、ソース コード ファイル、埋め込みリソース、プロジェクト ファイルなどが含まれます。

- *.vstemplate* ファイルが 1 つ。**[新しいプロジェクト]** ダイアログ ボックスと **[新しい項目の追加]** ダイアログ ボックスにテンプレートを表示し、テンプレートからプロジェクトや項目を作成するために必要なメタデータが含まれます。 *.vstemplate* ファイルについては、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。

これらのファイルが *.zip* ファイルに圧縮されて適切なフォルダーに配置されると、Visual Studio はそれを次の場所に自動的に表示します。

- プロジェクト テンプレートは、**[新しいプロジェクト]** ダイアログ ボックスに表示されます。

- 項目テンプレートは、**[新しい項目の追加]** ダイアログ ボックスに表示されます。

テンプレート フォルダーについては、「[方法: テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [方法: プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)
- [方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)
- [テンプレート パラメーター](../ide/template-parameters.md)
- [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)
- [Visual Studio テンプレートの NuGet パッケージ](/nuget/visual-studio-extensibility/visual-studio-templates)