---
title: '新しいプロジェクトの生成: フードのパート 1 |Microsoft ドキュメント'
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
ms.openlocfilehash: ac31f2866c6b69587f70775d5ed1245b1a2bb0a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133761"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>新しいプロジェクトの生成: フードのパート 1
プロジェクトの種類を作成する方法についてたいと思ったしますか。 新しいプロジェクトを作成するときに実際にはどうなりますか不思議にしますか。 フードの時間をかけてし、実際に起こっているを確認してみましょう。  
  
 Visual Studio によってコーディネートされるいくつかのタスクがあります。  
  
-   これには、すべての利用可能なプロジェクトの種類のツリーが表示されます。  
  
-   プロジェクトの種類ごとのアプリケーション テンプレートの一覧を表示し、いずれかを選択することができます。  
  
-   プロジェクトの名前とパスなど、アプリケーションのプロジェクト情報を収集します。  
  
-   この情報は、プロジェクト ファクトリに渡します。  
  
-   現在のソリューションにプロジェクト項目およびフォルダーを生成します。  
  
## <a name="the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックス  
 すべては、新しいプロジェクトのプロジェクトの種類を選択すると開始されます。 クリックして始めましょう**新しいプロジェクト**上、**ファイル**メニュー。 **新しいプロジェクト** ダイアログ ボックスが表示されたら、次のように見える。  
  
 ![[新しいプロジェクト] ダイアログ ボックス](../../extensibility/internals/media/newproject.gif "新しいプロジェクト")  
  
 詳しく見てをみましょう。 **プロジェクトの種類**ツリーが作成できるさまざまなプロジェクトの種類を一覧表示します。 同様に、プロジェクトの種類を選択すると**Visual c# Windows**、開始に役立つアプリケーション テンプレートの一覧が表示されます。 **Visual Studio にインストールされたテンプレート**Visual Studio がインストールされ、コンピューターのユーザーが使用できます。 追加できる新しいテンプレートを作成または収集**マイ テンプレート**だけが使用するとします。  
  
 ようにテンプレートを選択すると**Windows アプリケーション**、ダイアログ ボックスで以外の場合は、ここでは、アプリケーションの種類の説明が表示されます**Windows ユーザー インターフェイスを使用するアプリケーションを作成するためのプロジェクト**です。  
  
 下部にある、**新しいプロジェクト**ダイアログ ボックスで、詳細情報を収集するいくつかのコントロールが表示されます。 表示コントロールは、プロジェクトの種類によって異なりますが、一般に、プロジェクトが含まれます**名前**テキスト ボックス、**場所**テキスト ボックスおよび関連する**参照** ボタン、および、 **ソリューション名**テキスト ボックスおよび関連する**ソリューションのディレクトリを作成**チェック ボックスをオンします。  
  
## <a name="populating-the-new-project-dialog-box"></a>[新しいプロジェクト] ダイアログ ボックスを設定します。  
 ここでは、**新しいプロジェクト** ダイアログ ボックスからその情報を取得しますか? ここでは、作業時間非推奨のうちの 1 つには、2 つのメカニズムがあります。 **新しいプロジェクト** ダイアログ ボックスは結合し、両方のメカニズムから取得した情報が表示されます。  
  
 古い (非推奨) メソッドは、システム レジストリ エントリと .vsdir ファイルを使用します。 このメカニズムは、Visual Studio が開かれたときに実行されます。 新しいメソッドには、.vstemplate ファイルが使用されます。 Visual Studio は、たとえば、によって初期化を実行しているときに、このメカニズムが実行されます。  
  
```  
devenv /setup  
```  
  
 または  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>プロジェクトの種類  
 位置との名前、**プロジェクトの種類**などのルート ノード、 **Visual c#** と**他の言語**、システム レジストリのエントリによって決定されます。 子ノードの構成など、**データベース**と**スマート デバイス**.vstemplate の対応するファイルを含むフォルダーの階層構造を反映します。 最初のルート ノードを見てみましょう。  
  
#### <a name="project-type-root-nodes"></a>プロジェクトの種類のルート ノード  
 ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が初期化されると、システムのレジストリ キーのルート ノードの名前をビルドする HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs のサブキーの走査、**プロジェクトの種類**ツリー。 この情報は、後で使用できるキャッシュされます。 TemplateDirs 見て\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 キー。 各エントリは、VSPackage GUID です。 サブキーの名前 (/1) は無視され、その存在は、これがあることを示しますが、**プロジェクトの種類**ルート ノードです。 ルート ノードがありますでその外観を制御するいくつかのサブキーさらに、**プロジェクトの種類**ツリー。 これらのいくつかを見てみましょう。  
  
##### <a name="default"></a>(既定)  
 これは、ルート ノードの名前を示すローカライズされた文字列のリソース ID です。 文字列リソースがサテライト VSPackage GUID によって選択されている DLL に配置されます。  
  
 VSPackage の GUID は、例では、します。  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 ルート ノードのリソース ID (既定値) と (/1) は、#2345  
  
 近くにあるパッケージ キーの GUID を検索して SatelliteDll サブキーを調べる場合は、文字列が含まれているアセンブリのパスを検索できます。  
  
 \<Visual Studio インストール パス > \VC#\VCSPackages\1033\csprojui.dll  
  
 これを確認し、ファイル エクスプ ローラーを開き、Visual Studio ディレクトリに csprojui.dll をドラッグ. 文字列テーブルはことがわかりますリソース #2345 キャプション**Visual c#** です。  
  
##### <a name="sortpriority"></a>SortPriority  
 ルート ノードの位置を指定、**プロジェクトの種類**ツリー。  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 、優先順位の番号が小さいツリーで、上の位置。  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 このサブキーが存在する場合、ルート ノードの位置は、開発者向けの設定 ダイアログ ボックスによって制御されます。 たとえば、オブジェクトに適用された  
  
 DeveloperActivity REG_SZ VC #  
  
 ことを示します (Visual C#) は、ルート ノードの Visual Studio が設定されている場合[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]開発します。 子ノードであること、それ以外の場合、**他の言語**します。  
  
##### <a name="folder"></a>フォルダー  
 このサブキーが存在する場合、ルート ノードは、指定したフォルダーの子ノードになります。 キーの下の可能なフォルダーの一覧が表示されます。  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 たとえば、データベース プロジェクトのエントリは、PseudoFolders の他のプロジェクトの種類のエントリと一致するフォルダー キーを持ちます。 したがって、**プロジェクトの種類**ツリーで、**データベース プロジェクト**の子ノードになる**その他のプロジェクトの種類**です。  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>プロジェクトの種類の子ノードおよび .vstdir ファイル  
 子ノードの位置、**プロジェクトの種類**ツリー ProjectTemplates フォルダー内のフォルダー階層に依存します。 マシン テンプレート (**Visual Studio にインストールされたテンプレート**)、標準的な場所は、Visual Studio 14.0\Common7\IDE\ProjectTemplates\ \Program Files\Microsoft とユーザーのテンプレート (**マイ テンプレート**)、標準的な場所は、\My Documents\Visual Studio 14.0\Templates\ProjectTemplates\\です。 これら 2 つの場所からフォルダー階層を結合して作成、**プロジェクトの種類**ツリー。  
  
 Visual Studio c# 開発者向けの設定との**プロジェクトの種類**ツリーは次のようになります。  
  
 ![プロジェクトの種類](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 ProjectTemplates の対応するフォルダーは、次のようになります。  
  
 ![プロジェクト テンプレート](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 ときに、**新しいプロジェクト** ダイアログ ボックスが開き、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates フォルダーを走査し、その構造を再作成、**プロジェクトの種類**ツリーの変更。  
  
-   ルート ノードで、**プロジェクトの種類**ツリーは、アプリケーション テンプレートによって決定されます。  
  
-   ノード名はローカライズできますが、特殊文字を含めることができます。  
  
-   並べ替え順序を変更することができます。  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>プロジェクトの種類のルート ノードを検索します。  
 Visual Studio では、ProjectTemplates フォルダーを走査、ときに、すべての .zip ファイルを開き、.vstemplate ファイルを抽出します。 .Vstemplate ファイルでは、XML を使用して、アプリケーション テンプレートについて説明します。 詳細については、次を参照してください。[新しいプロジェクトの生成: 短縮、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)です。  
  
 \<ProjectType > タグは、アプリケーションのプロジェクトの種類を決定します。 たとえば、\CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip ファイルには、このタグを含む EmptyProject.vstemplate ファイルが含まれています。  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType > タグ、および ProjectTemplates フォルダーのサブフォルダー内のアプリケーションのルート ノードを決定、**プロジェクトの種類**ツリー。 表示する例では、Windows CE アプリケーション、 **Visual c#** ルート ノードで、Windows CE アプリケーションが下にある表示は、WindowsCE フォルダーを VisualBasic フォルダーに移動した場合でも、 **Visual c#** ルート ノードです。  
  
##### <a name="localizing-the-node-name"></a>ノード名のローカライズ  
 Visual Studio では、ProjectTemplates フォルダーを走査、検出された任意の .vstdir ファイルを調査します。 .Vstdir ファイルは、プロジェクトの種類の外観を制御する XML ファイル、**新しいプロジェクト** ダイアログ ボックス。 .Vstdir ファイルで使用して、 \<LocalizedName > タグの名前を**プロジェクトの種類**ノード。  
  
 たとえば、\CSharp\Database\TemplateIndex.vstdir ファイルには、このタグが含まれています。  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 この場合、ルート ノードの名前を示すローカライズされた文字列のサテライト DLL とリソース ID を指定**データベース**です。 ローカライズされた名前が利用できないフォルダー名など、特殊文字を含めることができます **.NET**です。  
  
 ない場合は\<LocalizedName > タグがある、フォルダー自体によって、プロジェクトの種類が名前付き**smartphone 2003**です。  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>プロジェクトの種類の並べ替え順序を検索します。  
 .Vstdir ファイルを使用して、プロジェクトの種類の並べ替え順序を決定する、 \<SortOrder > タグです。  
  
 たとえば、\CSharp\Windows\Windows.vstdir ファイルには、このタグが含まれています。  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir ファイルより大きい値を持つタグがあります。  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 内の下位の数、 \<SortOrder > ツリーで、位置では高いほど、タグのため、 **Windows**よりも高いノードが表示されます、**データベース**内のノード、**プロジェクトの種類**ツリー。  
  
 ない場合は\<SortOrder > を含むプロジェクトの種類を次アルファベット順に表示されるプロジェクトの種類のタグが指定されて\<SortOrder > 仕様です。  
  
 マイ ドキュメント .vstdir ファイルがないことに注意してください (**マイ テンプレート**) フォルダー。 ユーザー アプリケーション プロジェクトの種類名はローカライズされていないとアルファベット順に表示します。  
  
#### <a name="a-quick-review"></a>簡単な概要について  
 変更してみましょう、**新しいプロジェクト** ダイアログ ボックスし、新しいユーザー プロジェクト テンプレートを作成します。  
  
1.  MyProjectNode サブフォルダーを \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp フォルダーに追加します。  
  
2.  任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstdir ファイルを作成します。  
  
3.  .Vstdir ファイルには、これらの行を追加します。  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  保存して .vstdir ファイルを閉じます。  
  
5.  任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstemplate ファイルを作成します。  
  
6.  .Vstemplate ファイルには、これらの行を追加します。  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  The.vstemplate ファイルを保存してエディターを閉じます。  
  
8.  .Vstemplate ファイルを新しい圧縮 MyProjectNode\MyProject.zip フォルダーに送信します。  
  
9. Visual Studio のコマンド ウィンドウから次のように入力します。  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Visual Studio を開きます。  
  
1.  開く、**新しいプロジェクト** ダイアログ ボックスし、展開、 **Visual c#** プロジェクト ノードです。  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** Visual c# の Windows ノードのすぐ下に子ノードとして表示されます。  
  
## <a name="see-also"></a>関連項目  
 [新しいプロジェクトの生成: 内部、パート 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)