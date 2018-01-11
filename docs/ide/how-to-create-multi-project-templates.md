---
title: "方法 : 複数プロジェクトのテンプレートを作成する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac7701e3e4dc11bc5634436c3e6f831f6711e514
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="how-to-create-multi-project-templates"></a>方法 : 複数プロジェクトのテンプレートを作成する
複数プロジェクトのテンプレートは、2 つ以上のプロジェクトのコンテナーとして機能します。 複数プロジェクトのテンプレートに基づくプロジェクトが **[新しいプロジェクト]** ダイアログ ボックスで作成されると、テンプレート内のすべてのプロジェクトがソリューションに追加されます。  

 複数プロジェクトのテンプレートは、2 つ以上のプロジェクト テンプレートと `ProjectGroup` 型のルート テンプレートからなります。

 複数プロジェクトのテンプレートは、標準テンプレートとは動作も異なります。 複数プロジェクトのテンプレートには、次の固有の特性があります。  
  
-   複数プロジェクトのテンプレートの個別のプロジェクトには、**[新しいプロジェクト]** ダイアログ ボックスで名前を割り当てることができません。 代わりに、`ProjectTemplateLink` 要素の `ProjectName` 属性を使用して、各プロジェクトの名前を指定します。 詳細については、次のセクションの最初の例を参照してください。  
  
-   複数プロジェクトのテンプレートには別の言語で記述したプロジェクトを含めることができますが、テンプレート自体の全体は `ProjectType` 要素を使用して 1 つのカテゴリにのみ配置できます。  
  
### <a name="to-create-a-multi-project-template"></a>複数プロジェクトのテンプレートを作成するには  
  
1.  複数プロジェクトのテンプレートに含めるプロジェクトを作成します。
    1.  プロジェクトを作成します。  
  
    > [!NOTE]
    >  テンプレートのソースとなるプロジェクトに名前を付けるときは、有効な識別子文字のみを使ってください。 名前に無効な文字が含まれるプロジェクトからエクスポートされたテンプレートでは、後でそのテンプレートを基にしてプロジェクトを作成したときに、コンパイル エラーが発生する可能性があります。 有効な識別子文字について詳しくは、「[Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)」(宣言された要素の名前) をご覧ください。  
  
    2.  プロジェクトを編集して、テンプレートとしてエクスポートできる状態にします。  
  
    3.  必要に応じて、コード ファイルを編集し、パラメーター置換を行う場所を示します。 パラメーター置換について詳しくは、「[方法: テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)」をご覧ください。  
  
    4.  **[プロジェクト]** メニューの **[テンプレートのエクスポート]** をクリックします。 **[テンプレートのエクスポート]** ウィザードが開きます。  
  
    5.  **[プロジェクト テンプレート]** をクリックします。  
  
    6.  現在のソリューションに複数のプロジェクトがある場合は、テンプレートとしてエクスポートするプロジェクトを選択します。  
  
    7.  **[次へ]**をクリックします。  
  
    8.  アイコンと、テンプレートのプレビュー イメージを選択します。 これらは、**[新しいプロジェクト]** ダイアログ ボックスに表示されます。  
  
    9. テンプレートの名前と説明を入力します。  
  
    10. **[完了]**をクリックします。 プロジェクトが .zip ファイルにエクスポートされ、指定した出力場所に置かれます。また、選択した場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインポートされます。  
  
2.  生成された zip ファイルから .vstemplate ファイルを抽出し、テンプレートのエクスポートに使用するプロジェクト ファイルと同じディレクトリに入れます。

3.  複数プロジェクトのテンプレート用のメタデータを含めるルート .vstemplate ファイルを作成します。 詳細については、次のセクションの最初の例を参照してください。  
  
4.  テンプレートに含めるファイルおよびフォルダーを選択して右クリックし、**[送る]** をクリックしてから **[圧縮 (zip 形式) フォルダー]** をクリックします。 ファイルとフォルダーが .zip ファイルに圧縮されます。  
  
> [注意!] 複数プロジェクトのテンプレートは、次の項目を含み、.zip ファイルに圧縮する必要があります。  
>   
> -   複数プロジェクトのテンプレート全体のルート .vstemplate ファイル。 このルート .vstemplate ファイルは、**[新しいプロジェクト]** ダイアログ ボックスに表示されるメタデータを含み、このテンプレート内のプロジェクトの .vstemplate ファイルの場所を指定します。 このファイルは、.zip ファイルのルートに配置する必要があります。  
>   
> -   完全なプロジェクト テンプレートに必要なファイルを含む 1 つ以上のフォルダー。 これにはプロジェクトのすべてのコード ファイルが含まれ、プロジェクトの .vstemplate ファイルも含まれます。  
>   
> たとえば、2 つのプロジェクトを含む複数プロジェクトのテンプレート .zip ファイルは、次のファイルとディレクトリを持つことが考えられます。  
>   
>  MultiProjectTemplate.vstemplate  
>   
>  \Project1\Project1.vstemplate  
>   
>  \Project1\Project1.vbproj  
>   
>  \Project1\Class.vb  
>   
>  \Project2\Project2.vstemplate  
>   
>  \Project2\Project2.vbproj  
>   
>  \Project2\Class.vb  
>   
>  複数プロジェクトのテンプレートのルート .vstemplate ファイルは、単一プロジェクトのテンプレートとは次の点が異なります。  
>   
> -   `VSTemplate` 要素の `Type` 属性には値 `ProjectGroup` が含まれます。 例:  
>   
>     ```  
>     <VSTemplate Version="2.0.0" Type="ProjectGroup"  
>         xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
>     ```  
>   
> -   `TemplateContent` 要素には、含まれるプロジェクトの .vstemplate ファイルへのパスを定義する 1 つ以上の `ProjectTemplateLink` 要素を持つ `ProjectCollection` 要素が含まれます。 例:  
>   
>     ```  
>     <TemplateContent>  
>         <ProjectCollection>  
>             <ProjectTemplateLink>  
>                 Project1\Project1.vstemplate  
>             </ProjectTemplateLink>  
>             <ProjectTemplateLink>  
>                 Project2\Project2.vstemplate  
>             </ProjectTemplateLink>  
>         </ProjectCollection>  
>     </TemplateContent>  
>     ```  
>   
  
5.  .zip テンプレート ファイルを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクト テンプレートのディレクトリに配置します。 既定では、このディレクトリは \My Documents\Visual Studio *バージョン*\Templates\ProjectTemplates\\ です。  
  
## <a name="example"></a>例  
 基本的なマルチプロジェクトのルート .vstemplate ファイルの例を以下に示します。 この例では、テンプレートには `My Windows Application` と `My Class Library` の 2 つのプロジェクトが含まれています。 `ProjectName` 要素の `ProjectTemplateLink` 属性は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がこのプロジェクトに割り当てる名前を設定します。 `ProjectName` 属性が存在しない場合、.vstemplate ファイルの名前がプロジェクト名として使用されます。  
  
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
  
## <a name="example"></a>例  
 この例では、`SolutionFolder` 要素を使用して、プロジェクトを `Math Classes` および `Graphics Classes` という 2 つのグループに分割します。 テンプレートには 4 つのプロジェクトが含まれ、その 2 つは各ソリューション フォルダーに配置されます。  
  
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
  
## <a name="see-also"></a>参照  
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [方法 : プロジェクト テンプレートを作成する](../ide/how-to-create-project-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder 要素 (Visual Studio テンプレート)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink 要素 (Visual Studio テンプレート)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
