---
title: プロジェクト テンプレートを作成する
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9479eca1ac7763e1dc2861cffc8e0d940368692
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985813"
---
# <a name="how-to-create-project-templates"></a>方法: プロジェクト テンプレートを作成する

このトピックでは、**テンプレートのエクスポート ウィザード**を使ってテンプレートを作成する方法を示します。テンプレートは *.zip* ファイルにパッケージ化されます。

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>テンプレートのエクスポート ウィザードを使ってユーザー プロジェクト テンプレートを作成するには

1. プロジェクトを作成します。

    > [!NOTE]
    > テンプレートのソースとなるプロジェクトに名前を付けるときは、有効な識別子文字のみを使ってください。 そうしないと、テンプレートから作成されるプロジェクトでコンパイル エラーが発生することがあります。 有効な識別子文字については、「[Declared element names (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)」(宣言された要素の名前 (Visual Basic)) または「[Identifiers (C++)](/cpp/cpp/identifiers-cpp)」(識別子 (C++)) を参照してください。 または、[テンプレート パラメーター](../ide/template-parameters.md)を使って、クラスと名前空間に "安全な" 名前を使うこともできます。

2. プロジェクトを編集して、テンプレートとしてエクスポートできる状態にします。 たとえば、コード ファイルを編集して、パラメーター置換を行う場所を示します。 「[方法: テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)」を参照してください。

3. **[プロジェクト]** メニューの **[テンプレートのエクスポート]** を選択します。

   **テンプレートのエクスポート ウィザード**が開きます。

4. **[テンプレートの種類の選択]** ページで、**[プロジェクト テンプレート]** を選択します。 テンプレートにエクスポートするプロジェクトを選択し、**[次へ]** を選択します。

5. **[テンプレート オプションの選択]** ページで、テンプレートの名前および省略可能な説明、アイコン、プレビュー画像を入力します。 これらの項目は、**[新しいプロジェクト]** ダイアログ ボックスに表示されます。 **[完了]** を選択します。

   プロジェクトが *.zip* ファイルにエクスポートされて、指定した出力場所に置かれます。また、選択した場合は、Visual Studio にインポートされます。

>[!NOTE]
> **[新しいプロジェクト]** ダイアログ ボックスでテンプレートを探すには、**[インストール済み]** を展開し、*.vstemplate* ファイルの `ProjectType` 要素に対応するカテゴリを展開します。 たとえば、`<ProjectType>CSharp</ProjectType>` を含む *.vstemplate* ファイルは、既定では **[インストール済み]** > **[Visual C#]** に表示されます。 プロジェクトの種類のディレクトリにフォルダーを作成して、テンプレートの *.zip* ファイルを格納するだけで、プロジェクトの種類のサブディレクトリにテンプレートを整理できます。 詳細については、「[方法 :テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

## <a name="other-ways-to-create-project-templates"></a>プロジェクト テンプレートを作成する他の方法

プロジェクトを構成するファイルをフォルダーにまとめ、適切なメタデータを指定して *.vstemplate* XML ファイルを作成することにより、手動でプロジェクト テンプレートを作成できます。 詳細については、「[方法 :Web テンプレートを手動で作成する](../ide/how-to-manually-create-web-templates.md)」を参照してください。

Visual Studio SDK がインストールされている場合は、**VSIX プロジェクト** テンプレートを使うことで、完成したテンプレートを配置用に VSIX ファイルにラップすることができます。 詳細については、「[Getting started with the VSIX project template](../extensibility/getting-started-with-the-vsix-project-template.md)」(VSIX プロジェクト テンプレートの概要) を参照してください。

## <a name="see-also"></a>関連項目

- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [方法: 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)
- [VSIX プロジェクト テンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)