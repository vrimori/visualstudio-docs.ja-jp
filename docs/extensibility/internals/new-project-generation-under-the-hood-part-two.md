---
title: '新しいプロジェクトの生成: フードの第 2 部 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69174be20a0961a6074650471bcb4b9d1df9fa98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="new-project-generation-under-the-hood-part-two"></a>新しいプロジェクトの生成: フードの第 2 部します。
[新しいプロジェクトの生成: 短縮、パート 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)見た方法、**新しいプロジェクト** ダイアログ ボックスが表示されます。 選択したと仮定、 **Visual c# の Windows アプリケーション**、情報を入力した、**名前**と**場所**テキスト ボックス、および [ok] のクリックしました。  
  
## <a name="generating-the-solution-files"></a>ソリューション ファイルを生成します。  
 アプリケーション テンプレートを選択するように指示[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を解凍して、対応する .vstemplate ファイルを開くし、このファイル内の XML コマンドを解釈するためのテンプレートを起動します。 これらのコマンドは、新規または既存のソリューションにプロジェクトとプロジェクト項目を作成します。  
  
 テンプレートは、.vstemplate ファイルが含まれる同じ .zip フォルダーから、項目テンプレートと呼ばれる、ソース ファイルをアンパックします。 テンプレートは、それに応じてカスタマイズして、新しいプロジェクトに、これらのファイルをコピーします。  
  
### <a name="template-parameter-replacement"></a>テンプレート パラメーターの置換  
 テンプレートは、新しいプロジェクト項目テンプレートをコピー、するときにファイルをカスタマイズする文字列をテンプレート パラメーターに置き換えます。 テンプレート パラメーターは、特殊なトークンは、前後にドル記号、たとえばです、$date$ です。  
  
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
  
 Simple という名前の新しい Windows アプリケーション プロジェクトを作成する場合、テンプレートに置き換えられます、`$safeprojectname$`プロジェクトの名前を持つパラメーター。  
  
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
  
 テンプレート パラメーターの完全な一覧については、「[テンプレート パラメーター](../../ide/template-parameters.md)」をご覧ください。  
  
## <a name="a-look-inside-a-vstemplate-file"></a>内側、します。VSTemplate ファイル  
 基本的な .vstemplate ファイルが次の形式  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 について説明しました、 \<TemplateData > セクションで、[新しいプロジェクトの生成: 短縮、パート 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)です。 このセクションでタグがの外観の制御に使用される、**新しいプロジェクト** ダイアログ ボックス。  
  
 内のタグ、 \<TemplateContent > コントロールを新しいプロジェクトとプロジェクト項目の生成」セクションします。 ここでは、 \<TemplateContent > \Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip フォルダーに cswindowsapplication.vstemplate ファイルからセクションです。  
  
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
  
 \<プロジェクト > タグは、プロジェクトの生成を制御し、 \<ProjectItem > タグは、プロジェクト項目の生成を制御します。 ReplaceParameters パラメーターが true の場合、テンプレートは、プロジェクト ファイル、または項目内のすべてのテンプレート パラメーターをカスタマイズします。 ここでは、すべてのプロジェクト項目は、カスタマイズ、Settings.settings を除く。  
  
 TargetFileName パラメーターは、結果として得られるプロジェクト ファイルまたはアイテムの相対パスと名前を指定します。 これにより、プロジェクトのフォルダー構造を作成できます。 この引数を指定しない場合、プロジェクト項目はプロジェクト項目テンプレートと同じ名前になります。  
  
 結果として得られる Windows アプリケーションのフォルダー構造は、次のようになります。  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 最初で唯一\<Project > タグで、テンプレートの読み取り。  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 これは、コピーしてカスタマイズするテンプレート アイテム windowsapplication.csproj Simple.csproj プロジェクト ファイルを作成する新しいプロジェクト テンプレートを指示します。  
  
### <a name="designers-and-references"></a>デザイナーとの参照  
 わかりますソリューション エクスプ ローラーで、[プロパティ] フォルダーが存在し、必要なファイルが含まれています。 参照プロジェクトに関する新機能ところですが、Resources.resx を Resources.Designer.cs およびに Form1.cs、Form1.Designer.cs などのデザイナー ファイルの依存関係ですか。  これらで設定 Simple.csproj ファイルの生成時にします。  
  
 ここでは、 \<ItemGroup > プロジェクトの参照を作成する Simple.csproj から。  
  
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
  
 これらは、ソリューション エクスプ ローラーに表示される 6 つのプロジェクト参照であることを確認できます。 別のセクションを次に示します\<ItemGroup >。 わかりやすくするため、多数のコード行が削除されました。 このセクションでは、Settings.Designer.cs を Settings.settings に依存します。  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>関連項目  
 [新しいプロジェクトの生成: 内部、パート 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)