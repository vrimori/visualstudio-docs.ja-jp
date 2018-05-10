---
title: Visual Studio の既存のプロジェクトと項目テンプレートを更新する
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f5cf764f76d72b17128c46f2b7ec16ffcf4153cf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-update-existing-templates"></a>方法: 既存のテンプレートを更新する

テンプレートを作成し、複数のファイルを *.zip* ファイルに圧縮した後で、テンプレートを変更できます。 それには、テンプレートのファイルを手動で変更するか、テンプレートに基づいてプロジェクトから新しいテンプレートをエクスポートします。

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>テンプレートのエクスポート ウィザードの使用による既存のプロジェクト テンプレートの更新

Visual Studio の**テンプレートのエクスポート ウィザード**を使って、既存のテンプレートを更新することができます。

1. **[ファイル]** > **[新規]** > **[プロジェクト]** の順に選んで、**[新しいプロジェクト]** ダイアログ ボックスを開きます。

1. 更新するテンプレートを選択し、プロジェクトの名前と場所を入力して、**[OK]** を選択します。

1. Visual Studio でプロジェクトを変更します。

1. **[プロジェクト]** メニューの **[テンプレートのエクスポート]** を選択します。

    **テンプレートのエクスポート ウィザード**が開きます。

1. ウィザードの指示に従って、テンプレートを *.zip* ファイルとしてエクスポートします。

1. (省略可能) テンプレートを **[新しいプロジェクト]** ダイアログ ボックスに追加するには、*.zip* ファイルを *%USERPROFILE%\Documents\Visual Studio \<バージョン\>\Templates\ProjectTemplates* ディレクトリに置きます。 **テンプレートのエクスポート ウィザード**で **[テンプレートを自動的に Visual Studio にインポート]** オプションを選ばなかった場合、このステップを実行する必要があります。

1. 古いテンプレートの *.zip* ファイルを削除します。

## <a name="manually-update-an-existing-template"></a>既存のテンプレートを手動で更新する

圧縮された *.zip* ファイル内のファイルを変更することで、**テンプレートのエクスポート ウィザード**を使わずに既存のテンプレートを更新できます。

### <a name="to-manually-update-an-existing-template"></a>既存のテンプレートを手動で更新するには

1. テンプレートを含む *.zip* ファイルを探します。 ユーザー プロジェクト テンプレートは、*%USERPROFILE%\Documents\Visual Studio \<バージョン\>\Templates\ProjectTemplates* にあります。

1. *.zip* ファイルを展開します。

1. 現在のテンプレート ファイルを変更または削除するか、テンプレートに新しいファイルを追加します。

1. *.vstemplate* XML ファイルを開いたり、変更したり、保存したりして、更新された動作または新しいファイルを処理します。

    *.vstemplate* スキーマの詳細については、[「Visual Studio テンプレート スキーマ参照 (機能拡張)](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。 ソース ファイルでパラメーター化できる内容の詳細については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。

1. テンプレートでファイルを選び、右クリック メニューまたはコンテキスト メニューから、**[送る]** > **[圧縮 (zip 形式) フォルダー]** の順に選択します。

    選択したファイルは *.zip* ファイルに圧縮されます。

1. 新しい *.zip* ファイルを古い *.zip* ファイルと同じディレクトリに配置します。

1. 抽出したテンプレート ファイルと古いテンプレート *.zip* ファイルを削除します。

## <a name="see-also"></a>関連項目

- [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [テンプレート パラメーター](../ide/template-parameters.md)
- [方法: スタート キットを作成する](../ide/how-to-create-starter-kits.md)