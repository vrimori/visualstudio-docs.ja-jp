---
title: "方法 : Web テンプレートを手動で作成する | Microsoft Docs"
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
  - "プロジェクト テンプレート [Visual Studio], Web"
  - "テンプレート [Visual Studio], Web"
  - "Visual Studio のテンプレート, Web"
  - "Web テンプレート [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : Web テンプレートを手動で作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Web テンプレートの作成方法は、他の種類のテンプレートの作成方法とは異なります。  Web プロジェクト テンプレートは **\[新しい Web サイトの追加\]** ダイアログ ボックスに表示され、Web プロジェクト項目はプログラミング言語別に分類されるため、.vstemplate ファイルではテンプレートを Web テンプレートとして指定し、プログラミング言語を指定する必要があります。  
  
> [!NOTE]
>  Web テンプレートには、`Project` 要素の `File` 属性を使用して指定される空の .webproj ファイルが含まれる必要があります。  Web プロジェクトにはプロジェクト ファイルは必要ありませんが、このファイルは Web テンプレートが正しく機能するために必要となります。  
  
### Web テンプレートを手動で作成するには  
  
1.  Web プロジェクトを作成します。  
  
2.  プロジェクトのファイルを変更または削除するか、プロジェクトに新しいファイルを追加します。  
  
3.  XML ファイルを作成し、そのファイルをプロジェクトと同じディレクトリに .vstemplate ファイル名拡張子を使用して保存します。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロジェクトには追加しないでください。  
  
4.  .vstemplate XML ファイルを作成して、プロジェクト テンプレート メタデータを指定します。  詳細については、次のセクションの例を参照してください。  
  
5.  .vstemplate ファイルで `ProjectType` 要素を検索し、テキスト値を `Web` に設定します。  
  
6.  `ProjectType` 要素の後に `ProjectSubType` 要素を追加し、テキスト値をテンプレートのプログラミング言語に設定します。  プログラミング言語には、次のいずれかの値を指定できます。  
  
    -   CSharp  
  
    -   VisualBasic  
  
     次に例を示します。  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  テンプレート内のファイル \(.vstemplate ファイルを含む\) を選択して右クリックし、**\[送信\]** を選択し、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。  ファイルは .zip ファイルに圧縮されます。  
  
8.  .zip テンプレート ファイルを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト テンプレートのディレクトリに配置します。  既定では、このディレクトリは \\My Documents\\Visual Studio *バージョン*\\My Exported Templates \\ です。  
  
## 使用例  
 Web プロジェクト テンプレート用の基本的な .vstemplate ファイルの例を次に示します。  
  
```  
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
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)