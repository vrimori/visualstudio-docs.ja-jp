---
title: '新しいプロジェクトの生成: 内部、パート 1 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f678e15a26a85245e22edd323008ab517ea1e39c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907067"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>新しいプロジェクトの生成: 内部、パート 1
独自のプロジェクトの種類を作成する方法と考えるでしょうか。 新しいプロジェクトを作成すると実際にはどうなりますか不思議に思うでしょうか。 内部的には時間をかけてを実際に起こっているを確認しましょう。  
  
 Visual Studio を調整するいくつかのタスクがあります。  
  
-   すべての利用可能なプロジェクトの種類のツリーが表示されます。  
  
-   各プロジェクトの種類のアプリケーション テンプレートの一覧を表示し、いずれかを選択することができます。  
  
-   プロジェクトの名前とパスなど、アプリケーションのプロジェクト情報を収集します。  
  
-   プロジェクト ファクトリにこの情報を渡します。  
  
-   現在のソリューションにプロジェクト項目とフォルダーを生成します。  
  
## <a name="the-new-project-dialog-box"></a>新しいプロジェクト ダイアログ ボックス  
 すべては、新しいプロジェクトのプロジェクトの種類を選択すると開始します。 クリックして始めましょう**新しいプロジェクト**上、**ファイル**メニュー。 **新しいプロジェクト** ダイアログ ボックスが表示されたら、次のように見える。  
  
 ![新しいプロジェクト ダイアログ ボックス](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 詳しく見てをみましょう。 **プロジェクトの種類**ツリーが作成できるさまざまなプロジェクトの種類を一覧表示されます。 ようにプロジェクトの種類を選択すると**Visual c# Windows**、開始するためのアプリケーション テンプレートの一覧が表示されます。 **Visual Studio にインストールされたテンプレート**Visual Studio によってインストールされ、コンピューターのユーザーが使用できます。 新しいテンプレートを作成または収集するに追加できる**マイ テンプレート**られ、自分だけに使用できます。  
  
 ようにテンプレートを選択すると**Windows アプリケーション**、ダイアログ ボックスでは、ここでは、アプリケーションの種類の説明が表示されます**Windows ユーザー インターフェイスを備えたアプリケーションを作成するためのプロジェクト**します。  
  
 下部にある、**新しいプロジェクト**ダイアログ ボックスで、詳細情報を収集するコントロールを複数表示されます。 表示コントロールは、プロジェクトの種類によって異なりますが、一般に、プロジェクトが含まれます**名前**テキスト ボックスに、**場所**テキスト ボックスと関連**参照**ボタン、および、 **ソリューション名**テキスト ボックスと関連**ソリューションのディレクトリを作成**チェック ボックスをオンします。  
  
## <a name="populating-the-new-project-dialog-box"></a>新しいプロジェクト ダイアログ ボックスの設定  
 場所は、**新しいプロジェクト** ダイアログ ボックスから情報を取得するでしょうか。 ここでは、作業時間非推奨のうち 1 つには、2 つのメカニズムがあります。 **新しいプロジェクト** ダイアログ ボックスは、結合し、両方のメカニズムから取得した情報を表示します。  
  
 古い (非推奨) メソッドは、システム レジストリ エントリと .vsdir ファイルを使用します。 このメカニズムは、Visual Studio が開かれたときに実行されます。 新しいメソッドは、.vstemplate ファイルを使用します。 Visual Studio の初期化時に、たとえばを実行して、このメカニズムが実行されます。  
  
```  
devenv /setup  
```  
  
 または  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>プロジェクトの種類  
 位置との名前、**プロジェクトの種類**などのルート ノード、 **Visual c#** と**他の言語**、システム レジストリのエントリによって決定されます。 子ノードの組織など**データベース**と**スマート デバイス**、対応する .vstemplate ファイルを含むフォルダーの階層構造を反映します。 最初のルート ノードを見てみましょう。  
  
#### <a name="project-type-root-nodes"></a>プロジェクトの種類のルート ノード  
 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]はシステム レジストリ キーのルート ノードの名前をビルドする HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs のサブキーを通過する、初期化、**プロジェクトの種類**ツリー。 この情報は、後で使用できるキャッシュされます。 TemplateDirs 見て\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 キー。 各エントリは、VSPackage の GUID です。 サブキーの名前 (/1) は無視されますが、その存在は、これがあることを示します、**プロジェクトの種類**ルート ノード。 ルート ノードがありますでその外観を制御するいくつかのサブキーに、**プロジェクトの種類**ツリー。 これらのいくつかを見てみましょう。  
  
##### <a name="default"></a>(既定)  
 これは、ルート ノードの名前を示すローカライズされた文字列のリソース ID です。 文字列リソースがサテライト DLL の VSPackage の GUID が選択したにあります。  
  
 VSPackage の GUID は、例では、します。  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 ルート ノードのリソース ID (既定値) と (/1) は #2345  
  
 近くにあるパッケージのキーの GUID を検索して SatelliteDll サブキーを調べる場合は、文字列リソースを含むアセンブリのパスを確認できます。  
  
 \<Visual Studio インストール パス > \VC#\VCSPackages\1033\csprojui.dll  
  
 これを確認するには、ファイル エクスプ ローラーを開くし、csprojui.dll を Visual Studio のディレクトリにドラッグします. 文字列テーブル リソース #2345 にキャプションを示しています。 **Visual c#** します。  
  
##### <a name="sortpriority"></a>SortPriority  
 ルート ノードの位置を指定します、**プロジェクトの種類**ツリー。  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 、優先度の数が低いツリー内の位置を高くなります。  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 このサブキーが存在する場合、ルート ノードの位置は、開発者の設定 ダイアログ ボックスによって制御されます。 例えば以下のようにします。  
  
 DeveloperActivity REG_SZ VC #  
  
 されることを示します (Visual C#) はルート ノードの Visual Studio が設定されている場合[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]開発します。 それ以外の場合の子ノードであることが**他の言語**します。  
  
##### <a name="folder"></a>フォルダー  
 このサブキーが存在する場合は、ルート ノード、指定したフォルダーの子ノードになります。 キーの下の可能なフォルダーの一覧が表示されます。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 たとえば、データベース プロジェクトのエントリでは、PseudoFolders でその他のプロジェクトの種類のエントリと一致するフォルダーのキーがあります。 そのためで、**プロジェクトの種類**ツリー、**データベース プロジェクト**の子ノードになります**その他のプロジェクトの種類**。  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>プロジェクトの種類の子ノードと .vstdir ファイル  
 内の子ノードの位置、**プロジェクトの種類**ProjectTemplates フォルダー内のフォルダーの階層がツリーに依存します。 マシン テンプレート (**Visual Studio にインストールされたテンプレート**)、標準的な場所は、Visual Studio 14.0\Common7\IDE\ProjectTemplates\ \Program Files\Microsoft とユーザー テンプレートの (**マイ テンプレート**)、標準的な場所は \My Documents\Visual Studio 14.0\Templates\ProjectTemplates\\します。 これら 2 つの場所からのフォルダー階層をマージする、**プロジェクトの種類**ツリー。  
  
 C# 開発者向けの設定を使用して Visual Studio の**プロジェクトの種類**ツリーようになります。  
  
 ![プロジェクトの種類](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 対応する ProjectTemplates フォルダーのようになります。  
  
 ![プロジェクト テンプレート](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 ときに、**新しいプロジェクト** ダイアログ ボックスが開き、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates フォルダーを走査し、その構造を再作成、**プロジェクトの種類**ツリーにいくつかの変更。  
  
-   ルート ノード、**プロジェクトの種類**ツリーは、アプリケーション テンプレートによって決定されます。  
  
-   ノード名はローカライズできますが、特殊文字を含めることができます。  
  
-   並べ替え順序を変更することができます。  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>プロジェクトの種類のルート ノードの検索  
 Visual Studio では、ProjectTemplates フォルダーはスキャン、ときに、すべての .zip ファイルを開き、.vstemplate ファイルを抽出します。 .Vstemplate ファイルでは、XML を使用して、アプリケーション テンプレートについて説明します。 詳細については、次を参照してください。[新しいプロジェクトの生成: 内部、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)します。  
  
 \<ProjectType > タグは、アプリケーションのプロジェクトの種類を決定します。 たとえば、\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip ファイルには、このタグを含む EmptyProject.vstemplate ファイルが含まれています。  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > タグ、および、ProjectTemplates フォルダーのサブフォルダー内のアプリケーションのルート ノードを決定します。、**プロジェクトの種類**ツリー。 表示する例では、Windows CE アプリケーション、 **Visual c#** 、ルート ノードが、Windows CE アプリケーションが表示が WindowsCE フォルダーを visual Basic フォルダーに移動した場合でも、 **Visual c#** ルート ノード。  
  
##### <a name="localizing-the-node-name"></a>ノード名のローカライズ  
 Visual Studio では、ProjectTemplates フォルダーはスキャン、見つけた .vstdir ファイルを調査します。 .Vstdir ファイルは、プロジェクトの種類の外観を制御する XML ファイル、**新しいプロジェクト** ダイアログ ボックス。 .Vstdir ファイルで使用して、 \<LocalizedName > タグの名前を**プロジェクトの種類**ノード。  
  
 たとえば、\CSharp\Database\TemplateIndex.vstdir ファイルには、このタグが含まれています。  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 この場合、ルート ノードの名前を示すローカライズされた文字列のサテライト DLL およびリソース ID を指定します**データベース**します。 ローカライズされた名前では使用するフォルダーの名前などの特殊文字を含めることができます **.NET**します。  
  
 ない場合は\<LocalizedName > タグが存在する、フォルダー自体で、プロジェクトの種類の名前を付けます**smartphone 2003**します。  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>プロジェクトの種類の並べ替え順序の検索  
 .Vstdir ファイルを使用して、プロジェクトの種類の並べ替え順序を決定する、 \<SortOrder > タグです。  
  
 たとえば、\CSharp\Windows\Windows.vstdir ファイルには、このタグが含まれています。  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir ファイルより大きい値を伴うタグがあります。  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 番号が小さい、 \<SortOrder > タグ、ツリーで、位置より高いため、 **Windows**よりも高いノードが表示されます、**データベース**内のノード、**プロジェクトの種類**ツリー。  
  
 ない場合は\<SortOrder > が含まれているプロジェクトの種類を次の順に表示されるプロジェクトの種類のタグが指定されて\<SortOrder > 仕様。  
  
 マイ ドキュメント .vstdir ファイルがないことに注意してください (**マイ テンプレート**) フォルダー。 ユーザー アプリケーション プロジェクトの種類名がローカライズされていないと、順に表示されます。  
  
#### <a name="a-quick-review"></a>簡単な概要について  
 変更してみましょう、**新しいプロジェクト** ダイアログ ボックスし、新しいユーザー プロジェクト テンプレートを作成します。  
  
1. Visual Studio の \Program Files\Microsoft 14.0\Common7\IDE\ProjectTemplates\CSharp フォルダーに MyProjectNode サブフォルダーを追加します。  
  
2. 任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstdir ファイルを作成します。  
  
3. .Vstdir ファイルには、次の行を追加します。  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. 保存して .vstdir ファイルを閉じます。  
  
5. 任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstemplate ファイルを作成します。  
  
6. .Vstemplate ファイルには、次の行を追加します。  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. The.vstemplate ファイルを保存してエディターを閉じます。  
  
8. .Vstemplate ファイルを新しい圧縮 MyProjectNode\MyProject.zip フォルダーに送信します。  
  
9. Visual Studio のコマンド ウィンドウから次のように入力します。  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Visual Studio を開きます。  
  
10. 開く、**新しいプロジェクト** ダイアログ ボックスし、展開、 **Visual c#** プロジェクト ノード。  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **MyProjectNode** Visual c# の Windows ノードのすぐ下に子ノードとして表示されます。  
  
## <a name="see-also"></a>関連項目  
 [新しいプロジェクトの生成: 内部、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)