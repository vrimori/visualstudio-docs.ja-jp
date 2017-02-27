---
title: "方法 : 複数プロジェクトのテンプレートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "複数プロジェクトのテンプレート"
  - "プロジェクト テンプレート, 作成 (複数プロジェクトのテンプレートを)"
  - "Visual Studio のテンプレート, 作成 (複数プロジェクトのテンプレートを)"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 方法 : 複数プロジェクトのテンプレートを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

複数プロジェクトのテンプレートは、2 つ以上のプロジェクトのコンテナーとして機能します。  複数プロジェクトのテンプレートに基づくプロジェクトが **\[新しいプロジェクト\]** ダイアログ ボックスで作成されると、テンプレートに含まれるすべてのプロジェクトがソリューションに追加されます。  
  
 複数プロジェクトのテンプレートは、次の項目を含み、単一の .zip ファイルに圧縮する必要があります。  
  
-   複数プロジェクトのテンプレート全体のルート .vstemplate ファイル。  このルート .vstemplate ファイルは、**\[新しいプロジェクト\]** ダイアログ ボックスに表示されるメタデータを含み、このテンプレートに含まれるプロジェクトの .vstemplate ファイルの場所を指定します。  このファイルは、.zip ファイルのルートに配置する必要があります。  
  
-   完全なプロジェクト テンプレートに必要なファイルを含む 1 つ以上のフォルダー。  これには、プロジェクトのすべてのコード ファイル以外に、プロジェクトの .vstemplate ファイルも含まれます。  
  
 たとえば、2 つのプロジェクトを含む複数プロジェクトのテンプレート .zip ファイルは、次のファイルとディレクトリを持つことが考えられます。  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 複数プロジェクトのテンプレートのルート .vstemplate ファイルは、単一のプロジェクトから成るテンプレートとは、次の点が異なります。  
  
-   `VSTemplate` 要素の `Type` 属性の値は `ProjectGroup` です。  次に例を示します。  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   `TemplateContent` 要素には、含まれるプロジェクトの .vstemplate ファイルへのパスを定義する 1 つ以上の `ProjectTemplateLink` 要素を持つ `ProjectCollection` 要素が含まれます。  次に例を示します。  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 複数プロジェクトのテンプレートは、標準テンプレートとは動作も異なります。  複数プロジェクトのテンプレート固有の特性は、次のとおりです。  
  
-   複数プロジェクトのテンプレートの個別のプロジェクトには、**\[新しいプロジェクト\]** ダイアログ ボックスで名前を割り当てることができません。  代わりに、`ProjectTemplateLink` 要素の `ProjectName` 属性を使用して、各プロジェクトの名前を指定します。  詳細については、次のセクションの最初の例を参照してください。  
  
-   複数プロジェクトのテンプレートには別の言語で記述したプロジェクトを含めることができますが、テンプレート全体は `ProjectType` 要素で指定される 1 つのカテゴリにのみ配置できます。  
  
### 複数プロジェクトのテンプレートを作成するには  
  
1.  複数プロジェクトのテンプレートに含めるプロジェクトを作成します。  
  
2.  すべてのプロジェクトの .vstemplate ファイルを作成します。  詳細については、「[方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)」を参照してください。  
  
3.  複数プロジェクトのテンプレート用のメタデータを含めるルート .vstemplate ファイルを作成します。  詳細については、次のセクションの最初の例を参照してください。  
  
4.  テンプレートに含めるファイルおよびフォルダーを選択して右クリックし、**\[送る\]** をポイントして、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。  ファイルとフォルダーが .zip ファイルに圧縮されます。  
  
5.  .zip テンプレート ファイルを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト テンプレートのディレクトリに配置します。  既定では、このディレクトリは \\My Documents\\Visual Studio *バージョン*\\Templates\\ProjectTemplates \\ です。  
  
## 使用例  
 基本的な複数プロジェクトのルート .vstemplate ファイルの例を次に示します。  この例では、テンプレートには `My Windows Application` と `My Class Library` の 2 つのプロジェクトが含まれています。  `ProjectTemplateLink` 要素の `ProjectName` 属性は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がこのプロジェクトに割り当てる名前を設定します。  `ProjectName` 属性が存在しない場合、.vstemplate ファイルの名前がプロジェクト名として使用されます。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 使用例  
 この例では `SolutionFolder` 要素を使用して、プロジェクトを `Math Classes` と `Graphics Classes` の 2 つのグループに分けます。  テンプレートには 4 つのプロジェクトがあり、各ソリューション フォルダーには 2 つずつプロジェクトが置かれています。  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder 要素 \(Visual Studio テンプレート\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink 要素 \(Visual Studio テンプレート\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)