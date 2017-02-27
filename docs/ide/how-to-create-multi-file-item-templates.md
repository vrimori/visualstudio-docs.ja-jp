---
title: "方法 : 複数ファイルの項目テンプレートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目テンプレート, 作成 (複数ファイルの項目テンプレートを)"
  - "複数ファイルの項目テンプレート"
  - "Visual Studio のテンプレート, 作成 (複数ファイルの項目テンプレートを)"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法 : 複数ファイルの項目テンプレートを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

項目テンプレートには 1 つの項目だけを指定できますが、1 つの項目が複数のファイルから構成されている場合があります。  たとえば、 Visual Basic の Windows フォーム項目テンプレートには、次の 3 種類のファイルが必要です:  
  
-   フォームのコードを含む .vb ファイル。  
  
-   フォームのデザイナー情報を含む .designer.vb ファイル。  
  
-   フォームの埋め込みリソースを含む .resx ファイル。  
  
 複数ファイルの項目テンプレートでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で項目が作成されるときに正しいファイル名拡張子が使用されるようにするために、パラメーターを使用する必要があります。  **テンプレートのエクスポート** ウィザードを使用して項目テンプレートを作成する場合は、これらのパラメーターが自動的に生成されるので、それ以上編集する必要はありません。  次の手順では、正しいファイル名拡張子を作成するためのパラメーターの使用方法について説明します。  
  
### 複数ファイルの項目テンプレートを手動で作成するには  
  
1.  単一のファイルから成る項目テンプレートと同じ方法で、項目テンプレートを作成します。  詳細については、「[方法 : 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)」を参照してください。  
  
2.  すべての `ProjectItem` 要素に `TargetFileName` 属性を追加します。  `TargetFileName` 属性の値を $fileinputname$.*FileExtension* に設定します。*FileExtension* は、テンプレートに含まれるファイルのファイル名拡張子です。  次に例を示します。  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     このテンプレートから派生した項目がプロジェクトに追加されると、ユーザーが **\[新しい項目の追加\]** ダイアログ ボックスに入力した名前に基づいてファイル名が決定されます。  
  
3.  テンプレートに含めるファイルを選択して右クリックし、**\[送る\]** をポイントして、**\[圧縮 \(zip 形式\) フォルダー\]** をクリックします。  選択したファイルは .zip ファイルに圧縮されます。  
  
4.  ユーザー項目テンプレートの場所に .zip ファイルを配置します。  既定では、このディレクトリは \\My Documents\\Visual Studio *バージョン*\\Templates\\ItemTemplates \\ です。  詳細については、「[方法 : テンプレートを配置して整理する](../ide/how-to-locate-and-organize-project-and-item-templates.md)」を参照してください。  
  
## 使用例  
 次の例では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows フォーム テンプレートを示します。  このテンプレートに基づいて項目が作成されると、作成される 3 つのファイルの名前は **\[新しい項目の追加\]** ダイアログ ボックスに入力された名前のとおりになります。  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)   
 [テンプレート名](../ide/template-parameters.md)   
 [方法 : テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)