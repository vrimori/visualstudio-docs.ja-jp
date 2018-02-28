---
title: "Visual Studio の項目テンプレートを作成する | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd5d7fba092df5accfaad9d26cfc05f196981ba
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-create-item-templates"></a>方法: 項目テンプレートを作成する

このトピックでは、**テンプレートのエクスポート ウィザード**を使って項目テンプレートを作成する方法を示します。 テンプレートを複数のファイルで構成する場合は、「[方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)」をご覧ください。

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>ユーザー項目テンプレートを [新しい項目の追加] ダイアログ ボックスに追加するには

1. Visual Studio でプロジェクトを作成するか開きます。

1. 項目をプロジェクトに追加し、必要に応じて変更します。

1. コード ファイルを変更して、パラメーター置換を行う場所を示します。 詳細については、「[方法: テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)」を参照してください。

1. **[プロジェクト]** メニューの **[テンプレートのエクスポート...]** を選択します。

1. **[テンプレートの種類の選択]** ページで、**[項目テンプレート]** を選び、項目を含むプロジェクトを選択して、**[次へ]** を選択します。

1. **[エクスポートする項目の選択]** ページで、テンプレートを作成する項目を選択し、**[次へ]** を選択します。

1. **[項目参照の選択]** ページで、テンプレートに含めるアセンブリ参照を選択し、**[次へ]** を選択します。

1. **[テンプレート オプションの選択]** ページで、テンプレートの名前および省略可能な説明、アイコン画像、プレビュー画像を入力して、**[完了]** を選択します。

    テンプレートのファイルが .zip ファイルに追加されて、ウィザードで指定したディレクトリにコピーされます。 既定の場所は、%USERPROFILE%\Documents\Visual Studio \<バージョン\>\My Exported Templates です。

1. **テンプレートのエクスポート ウィザード**で **[テンプレートを自動的に Visual Studio にインポート]** オプションをオンにしなかった場合は、エクスポートされたテンプレートを見つけて、それをユーザー項目テンプレートのディレクトリにコピーします。 既定の場所は、%USERPROFILE%\Documents\Visual Studio \<バージョン\>\Templates\ItemTemplates です。

1. Visual Studio をいったん閉じて開きなおします。

1. 新しいプロジェクトを作成するか、既存のプロジェクトを開き、**[プロジェクト]** > **[新しい項目の追加...]** の順に選ぶか、**Ctrl** + **Shift** + **A** キーを押します。

   項目テンプレートが、**[新しい項目の追加]** ダイアログ ボックスに表示されます。 **テンプレートのエクスポート ウィザード**で説明を追加した場合、ダイアログ ボックスの右側に説明が表示されます。

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>ユニバーサル Windows アプリ プロジェクトで項目テンプレートを使えるようにするには

基本的なテンプレートを作成する作業の多くはウィザードで行われますが、多くの場合、テンプレートをエクスポートした後で .vstemplate ファイルを手動で変更する必要があります。 たとえば、ユニバーサル Windows アプリ プロジェクトの **[新しい項目の追加]** ダイアログに項目を表示する場合、追加の手順をいくつか実行する必要があります。

1. 前のセクションの手順に従って、項目テンプレートをエクスポートします。

1. 作成された .zip ファイルを抽出し、Visual Studio で .vstemplate ファイルを開きます。

1. C# ユニバーサル Windows プロジェクトの場合は、次の XML を `<TemplateData>` 要素内に追加します。

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Visual Studio で、.vstemplate ファイルを保存して閉じます。

1. .vstemplate ファイルをコピーして、.zip ファイルに戻します。

     **[ファイルのコピー]** ダイアログ ボックスが表示されたら、**[コピーして置き換える]** をクリックします。

これで、**[新しい項目の追加]** ダイアログ ボックスから、このテンプレートに基づく項目をユニバーサル Windows プロジェクトに追加できます。

## <a name="to-enable-templates-for-specific-project-subtypes"></a>特定のプロジェクト サブタイプのテンプレートを有効にするには

Windows、Office、Database、Web など、特定のプロジェクト サブタイプにのみテンプレートが表示されるように指定できます。

1. 項目テンプレートの .vstemplate ファイルで、ProjectType 要素を探します。

1. [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 要素を ProjectType 要素の直後に追加します。

1. 要素のテキスト値を次のいずれかの値に設定します。

    - Windows
    - Office
    - データベース
    - Web

たとえば、`<ProjectSubType>Database</ProjectSubType>` のように指定します。

**Office** プロジェクトの項目テンプレートの例を次に示します。

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>テンプレートのエクスポート ウィザードを使わずに項目テンプレートを手動で作成するには

場合によっては、項目テンプレートをゼロから手動で作成する必要があります。

1. プロジェクトとプロジェクト項目を作成します。

1. プロジェクト項目を変更して、テンプレートとして保存できる状態にします。

1. 必要に応じて、コード ファイルを変更し、パラメーター置換を行う場所を示します。 パラメーター置換の詳細については、「[方法: テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)」を参照してください。

1. XML ファイルを作成し、.vstemplate ファイル拡張子を使って、プロジェクトの項目ファイルと同じディレクトリに保存します。

1. 項目テンプレート メタデータを提供するための .vstemplate XML ファイルを編集します。 詳細については、「[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)」 (拡張機能) と、前のセクションの例を参照してください。

1. .vstemplate ファイルを保存して閉じます。

1. エクスプローラーで、テンプレートに含めるファイルを選んで右クリックし、**[送る]** > **[圧縮 (zip 形式) フォルダー]** の順に選択します。 選択したファイルは .zip ファイルに圧縮されます。

1. .zip ファイルをコピーして、ユーザーの項目テンプレートの場所に貼り付けます。 Visual Studio 2017 での規定のディレクトリは、%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates です。 詳細については、「[方法: プロジェクト テンプレートと項目テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。

## <a name="see-also"></a>関連項目

[プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)  
[方法 : 複数ファイルの項目テンプレートを作成する](../ide/how-to-create-multi-file-item-templates.md)  
[Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md) (拡張機能)
