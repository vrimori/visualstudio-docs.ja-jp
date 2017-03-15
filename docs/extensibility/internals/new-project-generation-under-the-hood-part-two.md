---
title: "新しいプロジェクトの生成: 実際のところ、第&2; 部 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5f214774a5cf0aeb3896004632f8a2076782b14
ms.lasthandoff: 02/22/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>新しいプロジェクトの生成: 実際のところ、第&2; 部します。
[新しいプロジェクトの生成: 短縮、パート&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)を説明しましたが、どのように**新しいプロジェクト**ダイアログ ボックスが表示されます。 選択したと仮定、 **Visual c# Windows アプリケーション**、情報を入力した、**名**と**場所**テキスト ボックス、および [ok] のクリックされました。  
  
## <a name="generating-the-solution-files"></a>ソリューション ファイルを生成します。  
 アプリケーション テンプレートを選択するように指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を解凍し、対応する .vstemplate ファイルを開くし、このファイル内の XML コマンドを解釈するためのテンプレートを起動します。 これらのコマンドは、新規または既存のソリューションにプロジェクトおよびプロジェクト項目を作成します。  
  
 テンプレートは、.vstemplate ファイルが入っている同じ .zip フォルダーの項目テンプレートと呼ばれる、ソース ファイルをアンパックします。 テンプレートは、これらのファイルを適切にカスタマイズする、新しいプロジェクトにコピーします。 プロジェクトおよび項目テンプレートの概要については、次を参照してください。 [NIB: Visual Studio のテンプレート](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041)します。  
  
### <a name="template-parameter-replacement"></a>テンプレート パラメーターの置換  
 テンプレートは、新しいプロジェクト項目テンプレートをコピー、ファイルをカスタマイズする文字列を含むすべてのテンプレート パラメーターが置き換えられます。 テンプレート パラメーターは、前後にドル記号は、たとえば、特別なトークン、$date$ です。  
  
 一般的なプロジェクト項目テンプレートを見てみましょう。 展開し、Program files \microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip フォルダー内の Program.cs を確認します。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Simple という名前の新しい Windows アプリケーション プロジェクトを作成する場合、テンプレートに置き換えられます、`$safeprojectname$`プロジェクトの名前のパラメーターです。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 テンプレート パラメーターの一覧については、次を参照してください。[テンプレート パラメーター](../../ide/template-parameters.md)します。  
  
## <a name="a-look-inside-a-vstemplate-file"></a>内における、します。VSTemplate ファイル  
 基本的な .vstemplate ファイルが次の形式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 については、 \<TemplateData > セクション、[新しいプロジェクトの生成: 内部の下、パート&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)します。 このセクションでタグを使用の外観を制御して、**新しいプロジェクト** ダイアログ ボックス。  
  
 タグは、 \<TemplateContent > コントロールを新しいプロジェクトやプロジェクト項目の生成」セクションします。 ここでは、 \<TemplateContent > \programfiles\microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip フォルダ内の cswindowsapplication.vstemplate ファイルからセクションです。  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<プロジェクト > タグは、プロジェクトの生成を制御し、 \<ProjectItem > タグは、プロジェクト項目の生成を制御します。 ReplaceParameters パラメーターが true の場合、テンプレートは、プロジェクト ファイルまたは項目内のすべてのテンプレート パラメーターをカスタマイズします。 この場合、すべてのプロジェクト項目、カスタマイズ、Settings.settings を除くします。  
  
 TargetFileName パラメーターは、生成されたプロジェクト ファイルまたはアイテムの相対パスと名前を指定します。 これにより、プロジェクトのフォルダー構造を作成できます。 この引数を指定しない場合、プロジェクト項目がプロジェクト項目テンプレートと同じ名前になります。  
  
 結果ウィンドウ アプリケーションのフォルダー構造になります。  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 最初で唯一\<プロジェクト > テンプレートの読み取りでタグ。  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 これは、テンプレート項目 windowsapplication.csproj のカスタマイズをコピーして Simple.csproj プロジェクト ファイルを作成する新しいプロジェクト テンプレートを指示します。  
  
### <a name="designers-and-references"></a>デザイナーと参照  
 わかりますソリューション エクスプ ローラーで、[プロパティ] フォルダーが存在し、必要なファイルが含まれています。 しかし、では、プロジェクトを参照し、デザイナー ファイル Resources.resx に Resources.Designer.cs や Form1.Designer.cs Form1.cs をなどの依存関係でしょうか。  これらで設定 Simple.csproj ファイルが生成されるとします。  
  
 ここでは、 \<ItemGroup > プロジェクト参照を作成する Simple.csproj から。  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 これらは、ソリューション エクスプ ローラーに表示される&6; つのプロジェクト参照であることを確認できます。 別のセクションを次に示します\<ItemGroup > します。 わかりやすくするため、多数のコード行が削除されました。 このセクションでは、Settings.Designer.cs を Settings.settings に依存します。  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>関連項目  
 [新しいプロジェクトの生成: 実際のところ、第&1; 部します。](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild1.md)
