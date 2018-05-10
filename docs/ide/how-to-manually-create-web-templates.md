---
title: Visual Studio の Web テンプレートを作成する
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: aeaeea5ee4d1d8e65cdc13ca11192a70e0459be1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manually-create-web-templates"></a>方法: Web テンプレートを手動で作成する

Web テンプレートの作成方法は、他の種類のテンプレートを作成する場合と異なります。 Web プロジェクト テンプレートは **[新しい Web サイトの追加]** ダイアログ ボックスに表示され、Web プロジェクトの項目はプログラミング言語によって分類されるので、*vstemplate* ファイルではテンプレートを Web テンプレートとして指定し、プログラミング言語を示す必要があります。

> [!NOTE]
> Web テンプレートには空の *.webproj* ファイルが含まれている必要があり、そのファイルが `Project` 要素の `File` 属性の *vstemplate* ファイルで参照されている必要があります。 Web プロジェクトには *.proj* プロジェクト ファイルは必要ありませんが、Web テンプレートが正常に機能するには、このスタブ ファイルを作成する必要があります。

## <a name="to-manually-create-a-web-template"></a>Web テンプレートを手動で作成するには

1. Web プロジェクトを作成します。

1. プロジェクト内のファイルを変更または削除するか、新しいファイルをプロジェクトに追加します。

1. XML ファイルを作成し、*vstemplate* ファイル名拡張子を使って、プロジェクトと同じディレクトリに保存します。 このファイルを Visual Studio のプロジェクトに追加しないでください。

1. *vstemplate* XML ファイルを編集して、プロジェクト テンプレート メタデータを提供します。 詳細については、[後の例](#example)を参照してください。

1. *vstemplate* ファイルで `ProjectType` 要素を探し、テキスト値を `Web` に設定します。

1. `ProjectType` 要素の後に `ProjectSubType` 要素を追加し、テキスト値をテンプレートのプログラミング言語に設定します。 プログラミング言語は次のいずれかの値です。

    - CSharp
    - VisualBasic

    例:

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. テンプレート内のファイル (*vstemplate* ファイルを含む) を選択して右クリックし、**[送る]** > **[圧縮 (zip 形式) フォルダー]** の順に選択します。 ファイルは *.zip* ファイルに圧縮されます。

1. *.zip* テンプレート ファイルを Visual Studio プロジェクト テンプレートのディレクトリに格納します。 既定では、このディレクトリは *%USERPROFILE%\Documents\Visual Studio \<バージョン\>\ProjectTemplates* です。

## <a name="example"></a>例

次の例では、Web プロジェクト テンプレートの基本的な *vstemplate* ファイルを示します。

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>関連項目

- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [Visual Studio テンプレート スキーマ参照 (機能拡張)](../extensibility/visual-studio-template-schema-reference.md)