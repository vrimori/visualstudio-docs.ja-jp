---
title: "MSSCCPRJ します。SCC ファイル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソースは、プラグイン、MSSCCPRJ を制御します。SCC ファイル"
  - "MSSCCPRJ します。SCC ファイル"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ します。SCC ファイル
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IDE を使用してソース管理下にある Visual Studio ソリューションまたはプロジェクトが配置されると、IDE は、文字列の形式でプラグインのソース管理から 2 つの重要な情報を受信します。 "AuxPath"と"ProjName"これらの文字列は、IDE に見えませんが、バージョン管理内で、ソリューションまたはプロジェクトを検索するプラグインで使用します。 IDE は通常取得これらの文字列を初めて呼び出すことによって、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md), 、それらを以降の呼び出しをソリューションまたはプロジェクト ファイルに保存し、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 ソリューションとプロジェクト ファイルに埋め込まれているときに、"AuxPath"および"ProjName"文字列が自動的に更新されません、ユーザーは、分岐、分岐、またはバージョン管理に含まれるソリューションおよびプロジェクトのファイルをコピーします。 ソリューションとプロジェクト ファイルがをバージョン コントロール内の正しい場所を指していることを確認するには、ユーザーは、文字列を手動で更新する必要があります。 いるため、文字列は不透明にするためのものを常にはありませんクリア更新方法です。  
  
 ソース管理プラグインでは、MSSCCPRJ と呼ばれる特殊なファイルに、"AuxPath"および"ProjName"文字列を格納することにより、この問題を回避できます。SCC ファイルです。 これは自分が所有し、プラグインによって管理されるローカルのクライアント側ファイルです。 このファイルは、ソース管理下に配置しないが、ソース管理の対象のファイルを含むすべてのディレクトリのプラグインによって生成されます。 ファイルを Visual Studio のソリューションとプロジェクト ファイルを確認するのには、ソース管理プラグインが標準またはユーザーが指定したリストに対してファイルの拡張機能を比較できます。 IDE では、プラグインがサポートされている、MSSCCPRJ を検出します。SCC ファイルを埋め込む"AuxPath"をしなくなり、ソリューションとプロジェクト ファイルへの文字列の"ProjName"が、MSSCCPRJ からこれらの文字列を読み取ります。SCC は、代わりにファイルです。  
  
 ソース管理プラグイン、MSSCCPRJ をサポートします。SCC ファイルは、次のガイドラインに従う必要があります。  
  
-   1 つ MSSCCPRJ のみできます。1 つのディレクトリのファイルを SCC です。  
  
-   MSSCCPRJ です。SCC ファイルでは、複数のファイルのディレクトリ内のソース管理下にある"AuxPath"と"ProjName"を含めることができます。  
  
-   "AuxPath"文字列は、引用符の内部に必要ありません。 許可されている引用符で囲む区切り記号として \(たとえば、二重引用符のペアを空の文字列を示すために使用できます\)。 IDE は、MSSCCPRJ から読み取られるときに"AuxPath"文字列からすべての引用符を削除します。SCC ファイルです。  
  
-   MSSCCPRJ"ProjName"文字列です。SCC ファイルはまったくから返される文字列と一致する必要があります、 `SccGetProjPath` 関数です。 関数によって返される文字列に引用符で囲む、MSSCCPRJ 内の文字列がある場合。SCC ファイルには、引用符が必要囲み、その逆です。  
  
-   MSSCCPRJ です。SCC ファイルを作成またはファイルがソース管理下に配置されるたびに更新します。  
  
-   MSSCCPRJ 場合。SCC ファイルが削除を取得すると、プロバイダーが再生成して、次回そのディレクトリをに関する、ソース管理操作を実行します。  
  
-   MSSCCPRJ です。SCC ファイルは、定義された書式を厳密に従う必要があります。  
  
## MSSCCPRJ を示しています。SCC ファイルの形式  
 MSSCCPRJ のサンプルを次に示します。SCC ファイルの形式 \(行番号をガイドとして提供されてされ、ファイルの本文に含まれない必要があります\)。  
  
 \[1 行目\] `SCC = This is a Source Code Control file`  
  
 \[2 行目\]  
  
 \[Line 3\] `[TestApp.sln]`  
  
 \[行 4\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Line 5\] `SCC_Project_Name = "$/TestApp"`  
  
 \[6 行目\]  
  
 \[Line 7\] `[TestApp.csproj]`  
  
 \[行 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[9 行目\] `SCC_Project_Name = "$/TestApp"`  
  
 最初の行では、ファイルの目的を示すし、この種類のすべてのファイルの署名として機能します。 この線は正確に次のようにすべて MSSCCPRJ で表示されます。SCC ファイル:  
  
 `SCC = This is a Source Code Control file`  
  
 後に、角かっこで、ファイル名でマークされている、各ファイルの設定のセクションです。 このセクションでは、追跡されているファイルごとに繰り返されます。 この行は、ファイル名の例、つまり、 `[TestApp.csproj]`です。 IDE では、次の 2 つの行が必要です。 ただし、定義されている値のスタイルは定義しません。 変数は、 `SCC_Aux_Path` と `SCC_Project_Name`です。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 このセクションに、終了の区切り記号はありません。 ファイルに表示されるすべてのリテラルと同様に、ファイルの名前は、scc.h ヘッダー ファイルで定義されます。 詳細については、「[ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)」を参照してください。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)