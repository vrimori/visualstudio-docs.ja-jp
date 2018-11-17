---
title: UML モデルからファイルを生成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: afbb81a67d8d5f8f587979ab8adca4251562072a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804548"
---
# <a name="generate-files-from-a-uml-model"></a>UML モデルからファイルを生成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML モデルから、プログラム コード、スキーマ、ドキュメント、リソース、およびその他さまざまな種類の成果物を生成できます。 UML モデルからテキスト ファイルを生成する 1 つの便利な方法は、使用する[テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。 これを使用すると、生成するテキスト内にプログラム コードを埋め込むことができます。  
  
 主に 3 つのシナリオがあります。  
  
- [メニュー コマンドからファイルを生成する](#Command)またはジェスチャ。 UML モデルで使用できる [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] コマンドを定義します。  
  
- [アプリケーションからファイルを生成する](#Application)します。 UML モデルを読み取り、ファイルを生成するアプリケーションを記述します。  
  
- [デザイン時に生成する](#Design)します。 モデルを使用してアプリケーションの機能の一部を定義し、コードやリソースなどを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ソリューション内で生成します。  
  
  このトピックでは、のディスカッションで終わる[テキスト生成を使用する方法](#What)します。 詳細については、次を参照してください。[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。  
  
##  <a name="Command"></a> メニュー コマンドからファイルを生成します。  
 UML メニュー コマンド内で、前処理されたテキスト テンプレートを使用することができます。 テキスト テンプレートのコード内、または別の部分クラス内で、ダイアグラムによって表示されるモデルを読み取ることができます。  
  
 これらの機能の詳細については、以下のトピックを参照してください。  
  
- [モデリング図にメニュー コマンドを定義する](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [UML モデル内を移動する](../modeling/navigate-the-uml-model.md)  
  
  次の例に示す方法は、いずれかのモデル図から操作を開始する場合に、単一のモデルからテキストを生成するのに適しています。 別のコンテキストでモデルを処理するには、使用を検討して[Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md)モデルとその要素にアクセスします。  
  
### <a name="example"></a>例  
 この例を実行するには、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能 (VSIX) プロジェクトを作成します。 この例で使用されているプロジェクト名が`VdmGenerator`します。 **Source.extension.vsixmanifest**ファイル**コンテンツの追加**型のフィールドに設定し、 **MEF コンポーネント**と現在のプロジェクトを参照するソース パス。 この種類のプロジェクトを設定する方法の詳細については、次を参照してください。[モデリング図にメニュー コマンドを定義](../modeling/define-a-menu-command-on-a-modeling-diagram.md)します。  
  
 プロジェクトに、次のコードを含む C# ファイルを追加します。 このクラスは、UML クラス ダイアグラムに表示されるメニュー コマンドを定義します。  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 次のファイルはテキスト テンプレートです。 モデル内の各 UML クラスのテキスト行と、各クラスのそれぞれの属性の行を生成します。 モデルを読み取るためのコードはテキストに埋め込まれており、`<# ... #>` で区切られています。  
  
 このファイルを作成するには、ソリューション エクスプ ローラーでプロジェクトを右クリックをポイントして**追加**、 をクリックし、**新しい項目の**します。 選択**前処理されたテキスト テンプレート**します。 この例のファイル名にする必要があります**VdmGen.tt**します。 **カスタム ツール**ファイルのプロパティを指定する必要があります**TextTemplatingFilePreprocessor**します。 前処理されたテキスト テンプレートの詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 テキスト テンプレートによって C# 部分クラスが生成され、これが [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトの一部になります。 別のファイルに、同じクラスの部分宣言をもう 1 つ追加します。 このコードにより、テンプレートが UML モデル ストアにアクセスできるようになります。  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 キーを押して、プロジェクトをテストする**F5**します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の新しいインスタンスが開始します。 このインスタンスで、クラス ダイアグラムを含む UML モデルを開くか、作成します。 ダイアグラムにいくつかのクラスを追加し、各クラスにいくつかの属性を追加します。 ダイアグラムを右クリックし、例のコマンドをクリック`Generate VDM`します。 コマンド ファイルを作成する`C:\Generated.txt`します。 このファイルを検査します。 内容は次のテキストに似たものになりますが、ユーザー自身のクラスと属性が一覧表示されます。  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
##  <a name="Application"></a> アプリケーションからファイルを生成します。  
 UML モデルを読み取るアプリケーションから、ファイルを生成できます。 モデルとその要素にアクセスする最も柔軟で堅牢な方法は、この目的で[Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md)します。  
  
 また、基本的な API を使用してモデルを読み込み、前のセクションと同じ方法を使用して、モデルをテキスト テンプレートに渡すこともできます。  モデルの読み込みの詳細については、次を参照してください。[プログラム コードで UML モデルを読み取る](../modeling/read-a-uml-model-in-program-code.md)します。  
  
##  <a name="Design"></a> デザイン時にファイルを生成します。  
 プロジェクトに UML をコードとして解釈する標準的な方法がある場合は、テキスト テンプレートを作成して、UML モデルからプロジェクト内にコードを生成できます。 通常は、UML モデル プロジェクトと、アプリケーション コード向けの 1 つ以上のプロジェクトを含むソリューションがあります。 各コード プロジェクトには、モデルのコンテンツに基づき、プログラム コード、リソース、および構成ファイルを生成するいくつかのテンプレートが含まれていることがあります。 開発者は、クリックしてすべてのテンプレートを実行することができます、**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。 通常、プログラム コードは部分クラスの形式で生成されるので、手作業で記述された部分と簡単に統合できます。  
  
 このような [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトはテンプレート形式で配布できるので、チームのすべてのメンバーが、同じ方法でモデルからコードを生成するプロジェクトを生成できます。 通常、テンプレートは、生成コードの必須条件が満たされていることを確認するために、モデルの検証制約を含む拡張機能パッケージの一部となっています。  
  
### <a name="outline-procedure-for-generating-files"></a>ファイルを生成するための手順の概要  
  
-   テンプレートをプロジェクトに追加するには、選択**テキスト テンプレート**新規ファイルの追加 ダイアログ ボックス。 ほとんどの種類のプロジェクトにテンプレートを追加できますが、モデリング プロジェクトには追加できません。  
  
-   テンプレート ファイルのカスタム ツール プロパティを指定する必要があります**TextTemplatingFileGenerator**、およびファイル名拡張子は .tt をする必要があります。  
  
-   テンプレートには、少なくとも 1 つの出力ディレクティブが必要です。  
  
     `<#@ output extension=".cs" #>`  
  
     プロジェクトの言語に従い、拡張機能フィールドを設定します。  
  
-   テンプレートの生成コードがモデルにアクセスできるようにするには、UML モデルを読み取るために必要なアセンブリに対して `<#@ assembly #>` ディレクティブを記述します。 `ModelingProject.LoadReadOnly()` を使用してモデルを開きます。 詳細については、次を参照してください。[プログラム コードで UML モデルを読み取る](../modeling/read-a-uml-model-in-program-code.md)します。  
  
-   クリックすると、保存するときに、テンプレートが実行される**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。  
  
-   この種類のテンプレートの詳細については、次を参照してください。 [T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)します。  
  
-   一般的なプロジェクトでは、同じモデルからさまざまなファイルを生成するテンプレートがいくつかあります。 どのテンプレートでも、最初の部分は同じです。 このような重複を減らすために、共通部分を別のテキスト ファイルに移動し、各テンプレートのディレクティブ `<#@include file="common.txt"#>` を使用して呼び出します。  
  
-   また、テキスト生成処理にパラメーターを指定する、特殊なディレクティブ プロセッサも定義できます。 詳細については、次を参照してください。 [T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)します。  
  
### <a name="example"></a>例  
 この例では、ソース モデルの各 UML クラスに対して C# クラスを生成します。  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>この例で、Visual Studio ソリューションを設定するには  
  
1. 新しいソリューションのモデリング プロジェクトに、UML クラス ダイアグラムを作成します。  
  
   1.  **アーキテクチャ** メニューのをクリックして**新しいダイアグラム**します。  
  
   2.  選択**UML クラス図**します。  
  
   3.  プロンプトに従い、新しいソリューションとモデリング プロジェクトを作成します。  
  
   4.  UML クラス ツールをツールボックスからドラッグし、ダイアグラムにクラスをいくつか追加します。  
  
   5.  ファイルを保存します。  
  
2. 同じソリューションに、C# または Visual Basic プロジェクトを作成します。  
  
   -   ソリューション エクスプ ローラーでソリューションを右クリックして**追加**、 をクリックし、**新しいプロジェクト**します。 [**インストールされたテンプレート**、] をクリックして**Visual Basic**または**Visual c#、** など、プロジェクトの種類を選択します**コンソール アプリケーション**します。  
  
3. C# または Visual Basic プロジェクトにプレーンテキスト ファイルを追加します。 このファイルには、複数のテキスト テンプレートを記述するときに共有されるコードを含めます。  
  
   - ソリューション エクスプ ローラーでプロジェクトを右クリックして**追加**、 をクリックし、**新しい項目の**します。 選択**テキスト ファイル**します。  
  
     次のセクションに示すテキストを挿入します。  
  
4. C# または Visual Basic プロジェクトにテキスト テンプレート ファイルを追加します。  
  
   - ソリューション エクスプ ローラーでプロジェクトを右クリックして**追加**、 をクリックし、**新しい項目の**します。 選択**テキスト テンプレート**します。  
  
     下に示すコードを、テキスト テンプレート ファイルに挿入します。  
  
5. テキスト テンプレート ファイルを保存します。  
  
6. 従属ファイルのコードを検査します。 このコードには、モデルの各 UML クラスのクラスが含まれているはずです。  
  
   1.  Visual Basic プロジェクトでは、次のようにクリックします。 **すべてのファイル**ソリューション エクスプ ローラーのツールバー。  
  
   2.  ソリューション エクスプローラーで、テンプレート ファイル ノードを展開します。  
  
#### <a name="content-of-the-shared-text-file"></a>共有テキスト ファイルのコンテンツ  
 この例では、ファイルの名前は SharedTemplateCode.txt で、テキスト テンプレートと同じフォルダーにあります。  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>テキスト テンプレート ファイルのコンテンツ  
 次のテキストを配置、 **.tt**ファイル。 この例では、モデルの UML クラスから、C# ファイルのクラスを生成します。 ただし、どのような種類のファイルでも生成できます。 生成されるファイルの言語は、テキスト テンプレート コードが記述される言語とは関係ありません。  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
##  <a name="What"></a> テキスト生成を使用する方法  
 モデリングの真の力は、要件またはアーキテクチャ レベルで、モデルを使用して設計する際に発揮されます。 テキスト テンプレートを使用すると、高水準のアイディアをコードに変換する作業の一部を行うことができます。 多くの場合、これによって、UML モデルの要素とプログラム コードのクラスまたはその他の部分との間に、一対一の対応関係がもたらされるわけではありません。  
  
 さらに、変換は問題ドメインに依存します。モデルとコードとの間に、汎用的なマッピングはありません。  
  
 次に、モデルからコードを生成する例を示します。  
  
-   **製品ライン**します。 Fabrikam, Inc. は、ビルドし、空港の手荷物取り扱いシステムをインストールします。 毎回のインストールで、大半のソフトウェアは非常に似かよっていますが、ソフトウェア構成は、設置されている手荷物取り扱い機器と、各部がベルト コンベヤにどのように相互接続されているかによって異なります。 契約の初めに、Fabrikam のアナリストは空港管理者と要件について話し合い、UML アクティビティ図を使用してハードウェア計画をキャプチャします。 このモデルを基に、開発チームが構成ファイル、プログラム コード、計画、およびユーザー ドキュメントを生成します。 コードを手動で追加、微調整して作業を完了します。 ジョブを経て実績を積みながら、生成される素材のスコープを拡張していきます。  
  
-   **パターン**します。 Contoso, Ltd の開発者は、UML クラス ダイアグラムを使用し、Web サイトの構築や、ナビゲーション スキームの設計を行っています。 各 Web ページはクラスによって表され、関連付けがナビゲーション リンクを表します。 開発者は、モデルから Web サイトのコードの大部分を生成します。 それぞれの Web ページは、いくつかのクラスとリソース ファイルのエントリに対応しています。  この方法には、各ページの構築が単一のパターンに準拠するという利点があるため、手入力されたコードよりも信頼性と柔軟性が高くなります。 パターンは、生成するテンプレートにあり、モデルは可変性のある部分を取り込むために使用されます。  
  
-   **スキーマ**します。 Humongous Insurance は、世界中で数千ものシステムを運用しています。 これらのシステムでは、異なるデータベース、言語、およびインターフェイスが使用されています。 中央のアーキテクチャ チームが、業務概念とプロセスのモデルを内部的に公開します。 これらのモデルから、ローカル チームは、データベース部分やインターチェンジ スキーマ、プログラム コードの宣言などを生成します。 モデルをグラフィカル表示すると、チームで提案について話し合う際に役立ちます。 チームは、さまざまな業務分野に適用されるモデルのサブセットを示す、複数のダイアグラムを作成します。 また、変更の対象となる分野を色分けして強調表示します。  
  
## <a name="important-techniques-for-generating-artifacts"></a>成果物を生成するための重要な方法  
 前の例では、ビジネスによって異なるさまざまな目的でモデルが使用されており、クラスやアクティビティなどのモデリング要素の解釈は、アプリケーションごとに異なります。 モデルから成果物を生成するには、次の方法が便利です。  
  
-   **プロファイル**します。 1 つの業務分野内でも、要素型の解釈が異なることがあります。 たとえば、Web サイト ダイアグラムでは、いくつかのクラスが Web ページを表し、他のクラスがコンテンツ ブロックを表すことがあります。 このような違いをユーザーが簡単に記録できるようにするために、ステレオタイプを定義します。 ステレオタイプを使用すると、その種類の要素に適用される追加プロパティをアタッチすることもできます。 ステレオタイプは、プロファイル内にパッケージされます。 詳細については、次を参照してください。 [UML を拡張するプロファイルを定義して](../modeling/define-a-profile-to-extend-uml.md)します。  
  
     テンプレート コードでは、オブジェクトで定義されているステレオタイプに簡単にアクセスできます。 例えば:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
-   **制約付きモデル**します。 生成できるすべてのモデルが、どの目的にも有効であるとは限りません。 たとえば、Fabrikam の空港手荷物モデルでは、チェックイン デスクに出発荷物用のコンベヤが必要です。 ユーザーがこのような制約を確認できるよう、検証関数を定義できます。 詳細については、次を参照してください。 [UML モデルの検証制約を定義](../modeling/define-validation-constraints-for-uml-models.md)します。  
  
-   **手動で変更を保持する**します。 モデルからすべてのソリューション ファイルを生成できるわけではありません。 ほとんどの場合、生成されたコンテンツを手動で追加、または調整できるようにする必要があります。 ただし、このような手動での変更は、テンプレート変換が再実行されたときに維持されることが重要です。  
  
     テンプレートがコードを生成[!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]言語、開発者は、メソッドとコードを追加できるように、部分クラスを生成する必要があります。 また、各クラスを、メソッドを含む抽象基本クラス、およびコンストラクターのみを含む継承クラスのペアとして生成すると便利です。 これにより、開発者はメソッドをオーバーライドできます。 初期化をオーバーライドするには、コンストラクターではなく、別のメソッドで行います。  
  
     テンプレートが XML およびその他の種類の出力を生成する場合は、手動コンテンツを生成されたコンテンツとは別に保持することがより困難になる可能性があります。 1 つの方法としては、2 つのファイルを組み合わせるビルド処理でタスクを作成します。 また、開発者が、生成されるテンプレートのローカル コピーを調整するという方法もあります。  
  
-   **個別のアセンブリにコードを移動**します。 テンプレートに含めるコードの本体は、大きくしすぎないでください。 生成されたコンテンツは、計算とは別にしておいてください。テキスト テンプレートでのコードの編集は、完全にはサポートされていません。  
  
     代わりに、多くの計算を実行してテキストを生成する必要がある場合は、これらの関数を別のアセンブリに構築し、テンプレートからメソッドを呼び出します。



