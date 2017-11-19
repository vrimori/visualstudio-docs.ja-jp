---
title: "ソリューション (です。Sln) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7be9b3bf7783980cfbbe1abfc44fe1748dd20a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="solution-sln-file"></a>ソリューション (です。Sln) ファイル
ソリューションは、Visual Studio でプロジェクトを整理するための構造体です。 ソリューションでは、(テキスト ベース、共有) .sln および .suo (バイナリ、ユーザー固有のソリューションのオプション) ファイル内のプロジェクトの状態情報を保持します。 .Suo ファイルについては、次を参照してください。[ソリューション ユーザー オプション (です。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)です。  
  
 環境を呼び出す場合は、.sln ファイルで参照されている結果として、VSPackage が読み込まれると、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln ファイルを読み取る。  
  
 .Sln ファイルには、環境を検索して読み込む永続化されたデータとプロジェクトを参照して Vspackage の名前と値パラメーターを使用して、テキスト ベースの情報が含まれています。 環境が繰り返し、ソリューションを開くと、ときに、 `preSolution`、 `Project`、および`postSolution`については、.sln ファイルをソリューションを読み込むには、ソリューション内でプロジェクトし、ソリューションに接続されているすべての永続化された情報です。  
  
 各プロジェクトのファイルには、そのプロジェクトの項目を含む階層を作成するための環境によって読み取られた追加の情報が含まれています。 階層データの永続性はプロジェクトによって制御されます。データは通常どおりに格納されません .sln ファイルが、意図的に書き込めることプロジェクト情報 .sln ファイルをそのように選択した場合。 永続化に関連する詳細については、次を参照してください。[プロジェクトの永続化](../../extensibility/internals/project-persistence.md)と[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)です。  
  
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
  
 ソリューションを読み込むには、環境は次の一連のタスクを実行します。  
  
1.  環境をマークされたすべてのセクションを処理読み取ったり .sln ファイルのグローバル セクション`preSolution`です。 この場合、このような 1 つのステートメントがあります。  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     環境を読み取るとき、`GlobalSection('name')`タグ名にマップ、VSPackage のレジストリを使用します。 キー名は、下のレジストリに存在する必要があります [HKLM\\< アプリケーション ID のレジストリ ルート\>\SolutionPersistence\AggregateGUIDs] です。 キーの既定値は、エントリを記述する VSPackage のパッケージ GUID (REG_SZ) です。  
  
2.  環境は、VSPackage では、呼び出しを読み込みます`QueryInterface`の VSPackage で、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>インターフェイス、および呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage は、データを格納できるようにセクション内のデータを持つメソッドです。 環境では、このプロセスを繰り返します各`preSolution`セクションです。  
  
3.  環境は、プロジェクトの永続化ブロックを反復処理します。 この例では、1 つのプロジェクトがあります。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     このステートメントには、GUID の一意のプロジェクトおよびプロジェクトの種類の GUID が含まれています。 この情報は、プロジェクト ファイルまたはソリューションに属しているファイルを検索する環境で使用し、各プロジェクトに必要な VSPackage します。 GUID が渡されるプロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>し、プロジェクトに関連する特定の VSPackage を読み込むは、プロジェクトは、VSPackage によってロードされます。 この場合、このプロジェクトに読み込まれている VSPackage では、Visual Basic です。  
  
     各プロジェクトは、必要に応じて、ソリューション内の他のプロジェクトによってアクセスできるように、一意のプロジェクトのインスタンス ID を保持できます。 理想的には、ソリューションとプロジェクトがソース コード管理下にある場合は、プロジェクトへのパスは、ソリューションへのパスを基準としたする必要があります。 ソリューションが最初に読み込まれたときに、プロジェクト ファイルは、ユーザーのコンピューターですることはできません。 ソリューション ファイルを基準としたサーバーに格納されているプロジェクト ファイルを用意することによって検出され、ユーザーのコンピューターにコピーするには、プロジェクト ファイルの比較的単純であります。 コピーにし、プロジェクトに必要なファイルの残りの部分を読み込みます。  
  
4.  .Sln ファイルのプロジェクト セクションに含まれている情報に基づいて、環境は、各プロジェクト ファイルを読み込みます。 プロジェクト自体が、プロジェクト階層を設定して、入れ子になったのすべてのプロジェクトの読み込みを担当します。  
  
5.  .Sln ファイルのすべてのセクションを処理した後、ソリューションはソリューション エクスプ ローラーで表示され、ユーザーによる変更の準備ができて。  
  
 ソリューションでプロジェクトを実装する任意の VSPackage に読み込むには、失敗した場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>メソッドが呼び出され、ソリューション内の他のすべてのプロジェクトの読み込み中に加えた可能性のある変更を無視する機会が与えられます。 解析エラーが発生した場合は、ソリューション ファイルで、できるだけ多くの情報が保存されてし、環境には、ソリューションが破損していることをユーザーに警告 ダイアログ ボックスが表示されます。  
  
 ソリューションが保存するか、閉じるときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>メソッドが呼び出され、.sln ファイルに入力する必要があるソリューションに変更が加えられたかどうかに表示する階層に渡されます。 渡される null 値を`QuerySaveSolutionProps`で<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>ソリューションの情報は保存されていることを示します。 ポインターによって決定されます、特定のプロジェクトの永続化された情報は、値が null でない場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>インターフェイスです。  
  
 保存する情報がある場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>インターフェイスがへのポインターと呼ばれる、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>メソッドです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>から名前/値ペアを取得するための環境でメソッドが呼び出されます`IPropertyBag`インターフェイスし、.sln ファイルに情報を書き込みます。  
  
 `SaveSolutionProps`および`WriteSolutionProps`再帰的にオブジェクトがから保存する情報を取得するための環境によって呼び出されます、`IPropertyBag`インターフェイスのすべての変更が、.sln ファイルに入力されるまでです。 この方法で、ソリューションと使用可能なソリューションを次回開いたときに、情報を保存することを確認できます。  
  
 .Sln ファイルを保存するものがあるかどうかをすべて読み込む VSPackage が列挙されます。 これは、レジストリ キーがクエリの読み込み時にのみです。 環境は、ソリューションが保存時にメモリにいるため、すべての読み込まれたパッケージについて認識しています。  
  
 だけ、.sln ファイル内のエントリが含まれる、`preSolution`と`postSolution`セクションです。 含まれないと同様のセクションでは .suo ファイル ソリューションには、正常に読み込むには、この情報が必要があるためです。 .Suo ファイルには、プライベート ノートについては、共有またはソース コード管理下に配置するのには意図されていないなど、ユーザー固有のオプションが含まれています。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [ソリューション ユーザー オプション (です。Suo) ファイル](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [ソリューション](../../extensibility/internals/solutions.md)