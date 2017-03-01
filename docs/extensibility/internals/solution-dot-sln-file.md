---
title: "ソリューション (します。Sln) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
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
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>ソリューション (します。Sln) ファイル
ソリューションは、Visual Studio でプロジェクトを整理するための構造です。 ソリューションには、テキスト ベース (共有) .sln および .suo (バイナリ、ユーザー固有のソリューションのオプション) ファイル内のプロジェクトの状態情報が保持されます。 .Suo ファイルについては、次を参照してください。[ソリューション ユーザー オプション (します。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)します。  
  
 環境を呼び出す場合は、.sln ファイルで参照されている結果として、VSPackage が読み込まれると、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>.sln ファイルを読み取る</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>。  
  
 .Sln ファイルには、環境を検索して読み込む永続化されたデータおよび VSPackages を参照して、プロジェクトの名前と値パラメーターを使用して、テキスト ベースの情報が含まれています。 ユーザーがソリューションを開いたときに、環境が繰り返し、 `preSolution`、 `Project`、および`postSolution`ソリューションを読み込んだに .sln ファイル内の情報は、ソリューションに含まれるプロジェクトし、ソリューションに接続されているすべての永続化された情報です。  
  
 各プロジェクトのファイルには、そのプロジェクトの項目を含む階層を作成するための環境によって読み取られる追加の情報が含まれています。 階層データの永続性は、プロジェクトによって制御されます。データは通常格納されません .sln ファイルのように選択した場合 .sln ファイルをプロジェクトの情報に記述すること意図的にことができます。 永続化に関連する詳細については、次を参照してください。[プロジェクトの永続化](../../extensibility/internals/project-persistence.md)と[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
## <a name="solution-file-contents"></a>ソリューション ファイルの内容  
 .Sln ファイルは、次のコードに示すようにいくつかのセクションで構成されます。  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 ソリューションを読み込むには、環境は、次の一連のタスクを実行します。  
  
1.  環境が .sln ファイルのグローバル セクションに読み取ってマークされたすべてのセクションを処理`preSolution`します。 この場合、このような&1; つのステートメントがあります。  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     環境を読み取るとき、`GlobalSection('name')`タグ、レジストリを使用して VSPackage に名をマップしています。 キーの名前は、下のレジストリに存在する必要があります [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs] です。 キーの既定値は、エントリを記述した VSPackage のパッケージ GUID (REG_SZ) です。  
  
2.  環境が呼び出し、VSPackage を読み込みます`QueryInterface`の VSPackage に、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイス、および呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>VSPackage は、データを保存できるように、セクション内のデータを持つメソッドです</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>。 環境では、このプロセスを繰り返します各`preSolution`セクションです。  
  
3.  環境は、プロジェクトの持続性のブロックを反復処理します。 この場合は、1 つのプロジェクトがあります。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     このステートメントには、GUID の一意のプロジェクトおよびプロジェクトの種類の GUID が含まれています。 この情報は、プロジェクト ファイルまたはソリューションに属しているファイルを検索する環境で使用し、各プロジェクトに必要な VSPackage します。 プロジェクトの GUID に渡される<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>し、プロジェクトに関連する固有の VSPackage をロードするには、プロジェクトは VSPackage によって読み込ま</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>。 この場合、このプロジェクトに読み込まれる VSPackage は Visual Basic は。  
  
     各プロジェクトは、必要に応じて、ソリューション内の他のプロジェクトによってアクセスできるように、一意のプロジェクトのインスタンス ID を保持できます。 理想的には、ソリューションとプロジェクトがソース コード管理下にある場合は、プロジェクトへのパスは、ソリューションへのパスに対する相対する必要があります。 ソリューションが最初に読み込まれたときに、プロジェクト ファイルはユーザーのコンピューターにインストールすることはできません。 ソリューション ファイルに相対サーバーに格納されているプロジェクト ファイルを持つことで、検出し、ユーザーのコンピューターにコピーするには、プロジェクト ファイルの比較的単純なです。 コピーし、プロジェクトに必要なファイルの残りの部分をロードします。  
  
4.  .Sln ファイルの [プロジェクト] セクションに含まれている情報に基づいて、環境は、各プロジェクト ファイルを読み込みます。 プロジェクト自体は、プロジェクト階層を設定して、入れ子になったプロジェクトの読み込みを担当し、  
  
5.  .Sln ファイルのすべてのセクションを処理した後、ソリューションはソリューション エクスプ ローラーでが表示され、ユーザーによって変更のための準備ができました。  
  
 ソリューションにプロジェクトを実装するすべての VSPackage に読み込むには、失敗した場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>メソッドが呼び出され、ソリューションの他のすべてのプロジェクトには、読み込み中に加えた可能性のある変更を無視する機会が与えられます</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>。 解析エラーが発生した場合は、できるだけ多くの情報がソリューション ファイルを保持され、環境には、ソリューションが破損していることをユーザーに警告 ダイアログ ボックスが表示されます。  
  
 ソリューションを保存したり、閉じたりするときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>メソッドが呼び出され、.sln ファイルに入力する必要があるソリューションに変更が加えられたかどうかに表示する階層に渡されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>。 渡される null 値`QuerySaveSolutionProps`で<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>、ソリューションの情報は保存されていることを示します</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>。 永続化された情報は、特定のプロジェクトへのポインターによって決定される値が null でない場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。  
  
 保存する情報がある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>インターフェイスがへのポインターと呼ばれる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>から名前と値のペアを取得するための環境でメソッドが呼び出されます`IPropertyBag`インターフェイスし、.sln ファイルに情報を書き込む</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>。  
  
 `SaveSolutionProps``WriteSolutionProps`オブジェクトはから保存する情報を取得するための環境で再帰的と呼ばれる、`IPropertyBag`インターフェイスのすべての変更が .sln ファイルに入力されるまでです。 この方法で、ソリューションと利用可能な次に、ソリューションを開いたときに、情報を保存することを確認できます。  
  
 .Sln ファイルに保存するものがあるかどうかをすべて読み込む VSPackage が列挙されます。 レジストリ キーは、照会ロード時にのみになります。 環境を知ってすべての読み込まれたパッケージ ソリューションが保存時にメモリ内にあるためです。  
  
 だけ .sln ファイル内のエントリが含まれる、`preSolution`と`postSolution`セクションです。 含まれないと同様のセクションでは、.suo ファイル ソリューションには、正常に読み込むには、この情報が必要があるためです。 .Suo ファイルには、共有またはソース コード管理下に配置するのには意図されていないプライベート ノートなどのユーザー固有のオプションが含まれています。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [ソリューション ユーザー オプション (します。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [ソリューション](../../extensibility/internals/solutions.md)
