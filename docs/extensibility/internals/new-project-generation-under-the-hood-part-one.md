---
title: "新しいプロジェクトの生成: 実際のところ、第 1 部します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio]、[新しいプロジェクト] ダイアログ"
  - "プロジェクト [Visual Studio] の新しいプロジェクトの生成"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 新しいプロジェクトの生成: 実際のところ、第 1 部します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトの種類を作成する方法について考えてみたことでしょうか。 新しいプロジェクトを作成するときに実際の動作でしょうか。 内部的なピーク シナリオと実際の状況を表示します。  
  
 Visual Studio によってコーディネートいくつかのタスクがあります。  
  
-   これには、すべての利用可能なプロジェクトの種類のツリーが表示されます。  
  
-   各プロジェクトの種類のアプリケーション テンプレートの一覧を表示し、いずれかを選択することができます。  
  
-   プロジェクトの名前とパスなど、アプリケーションのプロジェクト情報を収集します。  
  
-   プロジェクトの出荷時にこの情報を渡します。  
  
-   現在のソリューション、プロジェクト項目、およびフォルダーを生成します。  
  
## \[新しいプロジェクト\] ダイアログ ボックス  
 すべてを開始する新しいプロジェクトのプロジェクトの種類を選択します。 クリックして始めましょう **新しいプロジェクト** 上、 **ファイル** メニュー。**新しいプロジェクト** \] ダイアログ ボックスが表示されたら、次のように見える。  
  
 ![&#91;新しいプロジェクト&#93; ダイアログ ボックス](../../extensibility/internals/media/newproject.png "NewProject")  
  
 詳しく見てをいきましょう。**プロジェクトの種類** ツリーが作成できるさまざまなプロジェクトの種類を一覧表示します。 ようにプロジェクトの種類を選択すると **Visual c\# Windows**, 、開始するためのアプリケーション テンプレートの一覧が表示されます。**Visual Studio にインストールされたテンプレート** Visual Studio がインストールされており、コンピューターのユーザーが使用できます。 追加できる新しいテンプレートの作成や、収集を **マイ テンプレート** だけが使用するとします。  
  
 ようにテンプレートを選択すると **Windows アプリケーション**, 、ダイアログ ボックス。 この場合、アプリケーションの種類の説明が表示されます **Windows ユーザー インターフェイスを備えたアプリケーションを作成するためのプロジェクト**します。  
  
 下部にある、 **新しいプロジェクト** ダイアログ ボックスで、詳細情報を収集するいくつかのコントロールがわかります。 表示コントロールは、プロジェクトの種類によって異なりますが、一般に、プロジェクトが含まれます **名** テキスト ボックス、 **場所** テキスト ボックスおよび関連する **参照** \] ボタンと **ソリューション名** テキスト ボックスおよび関連する **ソリューションのディレクトリを作成** チェック ボックスをオンします。  
  
## \[新しいプロジェクト\] ダイアログ ボックスを設定します。  
 ここでは、 **新しいプロジェクト** \] ダイアログ ボックスから情報を取得するでしょうか。 ここでは、作業時間の非推奨に 1 つには、2 つのメカニズムがあります。**新しいプロジェクト** \] ダイアログ ボックスは、結合し、両方のメカニズムから取得した情報が表示されます。  
  
 以前の \(非推奨\) メソッドで、システム レジストリのエントリと .vsdir ファイルを使用します。 このメカニズムは、Visual Studio を開いたときに実行されます。 新しいメソッドでは、.vstemplate ファイルを使用します。 Visual Studio の初期化時に、たとえばを実行して、このメカニズムが実行されます。  
  
```  
devenv /setup  
```  
  
 または  
  
```  
devenv /installvstemplates  
```  
  
### プロジェクトの種類  
 位置との名前、 **プロジェクトの種類** などのルート ノード、 **Visual c\#** と **他の言語**, 、システム レジストリのエントリによって決定されます。 子ノードの構成など、 **データベース** と **スマート デバイス**, 、対応する .vstemplate ファイルを含むフォルダーの階層構造を反映します。 最初のルート ノードを見てみましょう。  
  
#### プロジェクトの種類のルート ノード  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が初期化されると、システムのレジストリ キーのルート ノードの名前をビルドする HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs のサブキーを走査、 **プロジェクトの種類** ツリーです。 この情報は、後で使用するキャッシュされます。 TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC} \\\/1 キーを確認します。 各エントリは、VSPackage GUID です。 サブキーの名前 \(\/1\) は無視され、その存在は、これがあることを示しますが、 **プロジェクトの種類** ルート ノードです。 ルート ノードがありますでその外観を制御するいくつかのサブキーに、 **プロジェクトの種類** ツリーです。 これらのいくつかを見てみましょう。  
  
##### \(既定\)  
 これは、ルート ノードの名前を示すローカライズされた文字列のリソース ID です。 文字列リソースは、サテライト VSPackage GUID が選択した DLL に配置されます。  
  
 VSPackage の GUID は、例では、します。  
  
 {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC}  
  
 ルート ノードのリソース ID \(既定値\) と \(\/1\) は \# 2345年  
  
 近くにあるパッケージのキーの GUID を検索し、SatelliteDll サブキーを確認すると場合、は、文字列が含まれているアセンブリのパスを確認することができます。  
  
 \< visual Studio インストール パス \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 これを確認するには、ファイル エクスプ ローラーを開き、Visual Studio のディレクトリに csprojui.dll をドラッグして. 文字列テーブル リソース \# 2345年にキャプションを示しています。 **Visual c\#**します。  
  
##### SortPriority  
 これでルート ノードの位置が決まります、 **プロジェクトの種類** ツリーです。  
  
 SortPriority REG\_DWORD 0x00000014 \(20\)  
  
 優先度の数が低いツリーで、上位の位置。  
  
##### DeveloperActivity  
 このサブキーが存在する場合、ルート ノードの位置は、開発者向けの設定\] ダイアログ ボックスによって制御されます。 次に例を示します。  
  
 DeveloperActivity REG\_SZ VC \#  
  
 されることを示して Visual C\# の場合は、ルート ノードに設定されている Visual Studio [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 開発します。 子ノードであることはそれ以外の場合、 **他の言語**します。  
  
##### フォルダー  
 このサブキーが存在する場合、ルート ノードは、指定したフォルダーの子ノードになります。 キーの下に可能なフォルダーの一覧が表示されます。  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 たとえば、データベース プロジェクトのエントリには、PseudoFolders の他のプロジェクトの種類のエントリと一致するフォルダー キーがあります。 したがって、 **プロジェクトの種類** ツリーで、 **データベース プロジェクト** の子ノードになります **その他のプロジェクトの種類**。  
  
#### プロジェクトの種類の子ノードおよび .vstdir ファイル  
 子ノードの位置、 **プロジェクトの種類** ツリー ProjectTemplates フォルダー内のフォルダー階層に依存しています。 マシン テンプレートを \(**Visual Studio にインストールされたテンプレート**\)、標準的な場所は、Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\ \\Program Files\\Microsoft とユーザー テンプレート \(**自分のテンプレート**\)、一般的な場所は \\My Documents\\Visual Studio 14.0\\Templates\\ProjectTemplates\\ します。 これら 2 つの場所からフォルダー階層を結合して作成、 **プロジェクトの種類** ツリーです。  
  
 C\# 開発者向けの設定を使用して Visual Studio の **プロジェクトの種類** ツリーに次のようになります。  
  
 ![プロジェクトの種類](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 対応する ProjectTemplates フォルダーは、次のようになります。  
  
 ![プロジェクト テンプレート](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 ときに、 **新しいプロジェクト** \] ダイアログ ボックスが開き、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates フォルダーを走査し、その構造に再作成、 **プロジェクトの種類** ツリーにいくつかの変更。  
  
-   ルート ノードで、 **プロジェクトの種類** ツリーは、アプリケーション テンプレートによって決定されます。  
  
-   ノード名はローカライズできますが、特殊文字を含めることができます。  
  
-   並べ替え順序を変更できます。  
  
##### プロジェクトの種類のルート ノードを検索します。  
 Visual Studio は ProjectTemplates フォルダーをスキャンするときはすべての .zip ファイルが開かれ、.vstemplate ファイルを抽出します。 .Vstemplate ファイルでは、XML を使用して、アプリケーション テンプレートを説明します。 詳細については、「[新しいプロジェクトの生成: 実際のところ、第 2 部します。](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)」を参照してください。  
  
 \< ProjectType \> タグでは、アプリケーションのプロジェクトの種類を決定します。 たとえば、\\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip ファイルには、このタグを含む EmptyProject.vstemplate ファイルが含まれています。  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \< ProjectType \> タグと ProjectTemplates フォルダーのサブフォルダーで、アプリケーションのルート ノードを決定する、 **プロジェクトの種類** ツリーです。 例では、Windows CE アプリケーションが下に表示されます、 **Visual c\#** ルート ノードも Windows CE アプリケーションが下にある表示は WindowsCE フォルダーを visual Basic フォルダーに移動した場合でも、 **Visual c\#** ルート ノードです。  
  
##### ノード名をローカライズします。  
 Visual Studio は ProjectTemplates フォルダーをスキャンする際に、見つかった .vstdir ファイルを調べます。 .Vstdir ファイルは、プロジェクトの種類の外観を制御する XML ファイル、 **新しいプロジェクト** \] ダイアログ ボックス。 .Vstdir ファイルで \< LocalizedName \> タグの名前を使用して、 **プロジェクトの種類** ノードです。  
  
 たとえば、\\CSharp\\Database\\TemplateIndex.vstdir ファイルには、このタグが含まれています。  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 この場合、ルート ノードの名前を示すローカライズされた文字列のサテライト DLL とリソース ID を指定 **データベース**します。 ローカライズされた名前では利用できないフォルダー名など、特殊文字を含めることができます **.NET**します。  
  
 \< LocalizedName \> タグが存在しない場合、プロジェクトの種類はという名前で、フォルダー自体、 **smartphone 2003**します。  
  
##### プロジェクトの種類の並べ替え順序を検索します。  
 プロジェクトの種類の並べ替え順序を確認するのには、.vstdir ファイルは、\< SortOrder \> タグを使用します。  
  
 たとえば、\\CSharp\\Windows\\Windows.vstdir ファイルには、このタグが含まれています。  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \\CSharp\\Database\\TemplateIndex.vstdir ファイルより大きい値を持つタグがあります。  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 低い \< SortOrder \> 内の数値タグ、ツリーで、位置が大きいほどため、 **Windows** よりも高いノードが表示されます、 **データベース** 内のノード、 **プロジェクトの種類** ツリーです。  
  
 プロジェクトの種類に対する \< SortOrder \> タグが指定されていない場合は、次の \< SortOrder \> 仕様を含むプロジェクトの種類、アルファベット順に表示されます。  
  
 マイ ドキュメントに .vstdir ファイルがないことに注意してください \(**マイ テンプレート**\) フォルダーです。 ユーザー アプリケーション プロジェクトの種類名はローカライズされていないし、アルファベット順に表示します。  
  
#### 簡単な概要について  
 説明を変更、 **新しいプロジェクト** \] ダイアログ ボックスを新しいユーザー プロジェクト テンプレートを作成します。  
  
1.  Visual Studio の \\programfiles\\microsoft 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp フォルダ MyProjectNode サブフォルダーを追加します。  
  
2.  任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstdir ファイルを作成します。  
  
3.  .Vstdir ファイルに次の行を追加します。  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  保存して .vstdir ファイルを閉じます。  
  
5.  任意のテキスト エディターを使用して MyProjectNode フォルダー内には、MyProject.vstemplate ファイルを作成します。  
  
6.  .Vstemplate ファイルに次の行を追加します。  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  The.vstemplate ファイルを保存してエディターを閉じます。  
  
8.  .Vstemplate ファイルを新しい圧縮 MyProjectNode\\MyProject.zip フォルダーに送信します。  
  
9. Visual Studio のコマンド ウィンドウから次のように入力します。  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Visual Studio を開きます。  
  
1.  開いている、 **新しいプロジェクト** \] ダイアログ ボックスに展開し、 **Visual c\#** プロジェクト ノード。  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** Visual c\# の Windows ノードのすぐ下に子ノードとして表示されます。  
  
## 参照  
 [新しいプロジェクトの生成: 実際のところ、第 2 部します。](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)