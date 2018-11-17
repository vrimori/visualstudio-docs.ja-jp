---
title: MSSCCPRJ します。SCC ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a04429bafb7da0b3d4922905bd712e82ba16a4ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736154"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ.SCC File
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IDE を使用してソース管理下にある Visual Studio ソリューションまたはプロジェクトが配置されると、IDE は、文字列の形式でプラグインのソース管理から 2 つの重要な情報を受信します。 これらの文字列では、"AuxPath"と"ProjName"は、IDE に不透明ながプラグインによってバージョン管理でソリューションまたはプロジェクトを検索に使用されます。 IDE 通常取得これらの文字列を初めて呼び出すことによって、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)、し、それらを以降の呼び出しをソリューションまたはプロジェクト ファイルに保存し、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 ソリューションおよびプロジェクト ファイルに埋め込まれているときに、"AuxPath"および"ProjName"の文字列が自動的に更新されません、ユーザーは、分岐、フォーク、またはバージョン管理されているソリューションとプロジェクトのファイルをコピーします。 ソリューションおよびプロジェクト ファイルをバージョン管理での正しい場所を指していることを確認するに、ユーザーは、文字列を手動で更新する必要があります。 文字列は不透明になっているためにが必ずしもクリア更新方法です。  
  
 ソース管理プラグインは、MSSCCPRJ と呼ばれる特殊なファイルに、"AuxPath"および"ProjName"の文字列を格納することによってこの問題を回避できます。SCC ファイルです。 これはローカルのクライアント側のファイルが所有し、プラグインによって管理されます。 このファイルは、ソース管理下には格納されませんが、ソース管理ファイルを含むすべてのディレクトリのプラグインによって生成されます。 どのファイルは、Visual Studio のソリューションとプロジェクト ファイルを確認するには、ソース管理プラグインは、標準またはユーザーが指定したリストに対してファイルの拡張機能を比較できます。 IDE では、プラグインがサポートされている、MSSCCPRJ が検出されます。"AuxPath"を埋め込むなったら SCC ファイル、およびソリューションとプロジェクト ファイルへの文字列の"ProjName"が、MSSCCPRJ からこれらの文字列を読み取ります。SCC ファイルを代わりにします。  
  
 ソース管理プラグイン、MSSCCPRJ をサポートします。SCC ファイルは、次のガイドラインに従う必要があります。  
  
-   1 つ MSSCCPRJ のみできます。1 つのディレクトリのファイルを SCC です。  
  
-   MSSCCPRJ します。SCC ファイルでは、指定したディレクトリ内のソース管理下にある複数のファイルの"AuxPath"と"ProjName"を含めることができます。  
  
-   "AuxPath"文字列は、引用符の内部に必要ありません。 区切り記号として引用符で囲むが許可されます (たとえば、二重引用符のペアを空の文字列を示すために使用できます)。 IDE、MSSCCPRJ から読み取られるときに"AuxPath"文字列からすべての引用符が削除されます。SCC ファイルです。  
  
-   MSSCCPRJ"ProjName"文字列。SCC ファイルはまったくから返される文字列と一致する必要があります、`SccGetProjPath`関数。 関数によって返される文字列に引用符で囲む、MSSCCPRJ 内の文字列がある場合。SCC ファイルが引用符で囲み、その逆です。  
  
-   MSSCCPRJ します。SCC ファイルが作成または、ファイルがソース管理下に配置されるたびに更新します。  
  
-   MSSCCPRJ 場合。SCC ファイルが削除された、プロバイダーが再生成、次回そのディレクトリに関連のソース管理操作を実行します。  
  
-   MSSCCPRJ します。SCC ファイルには、定義済みの形式に厳密に従う必要があります。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ を示しています。SCC ファイルの形式  
 MSSCCPRJ のサンプルを次に示します。SCC ファイルの形式 (行番号は、ガイドとしてのみ提供されているし、ファイルの本文に含まれない):  
  
 [Line 1] `SCC = This is a Source Code Control file`  
  
 [Line 2]  
  
 [Line 3] `[TestApp.sln]`  
  
 [Line 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Line 6]  
  
 [Line 7] `[TestApp.csproj]`  
  
 [Line 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 9] `SCC_Project_Name = "$/TestApp"`  
  
 最初の行では、ファイルの目的の状態し、この種類のすべてのファイルの署名として機能します。 この線は、すべて MSSCCPRJ ようの正確に表示されます。SCC ファイル:  
  
 `SCC = This is a Source Code Control file`  
  
 次には、角かっこで囲んで、ファイル名でマークされている、各ファイルの設定のセクションです。 このセクションでは、追跡されているファイルごとに繰り返されます。 この行は、ファイル名の例を具体的が`[TestApp.csproj]`します。 IDE では、次の 2 つの行が必要です。 ただし、定義されている値のスタイルは定義しません。 変数は、`SCC_Aux_Path`と`SCC_Project_Name`します。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 このセクションに末尾の区切り記号はありません。 ファイルに表示されるすべてのリテラルと同様に、ファイルの名前は、scc.h ヘッダー ファイルで定義されます。 詳細については、次を参照してください。[文字列は、ソース管理プラグインを検索するためのキーとして使用](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

