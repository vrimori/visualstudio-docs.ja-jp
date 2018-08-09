---
title: MSSCCPRJ します。SCC ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc754437433124e033b0f0fb0feac79487664b51
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636072"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ します。SCC ファイル
Visual Studio ソリューションまたは IDE を使用してソース管理下にあるプロジェクトを配置すると、IDE は、2 つの重要な情報を受信します。 文字列の形式でプラグインのソース管理からの情報が取得されます。 これらの文字列では、"AuxPath"と"ProjName"は、IDE に不透明ながバージョン コントロール内でソリューションまたはプロジェクトを検索するプラグインで使用しています。 IDE は、通常取得これらの文字列を初めて呼び出すことによって、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)、し、それらを以降の呼び出しをソリューションまたはプロジェクト ファイルに保存し、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 ソリューションおよびプロジェクト ファイルに埋め込まれているときに、"AuxPath"および"ProjName"の文字列が自動的に更新されません、ユーザーは、分岐、フォーク、またはバージョン管理されているソリューションとプロジェクトのファイルをコピーします。 ソリューションおよびプロジェクト ファイルをバージョン管理での正しい場所を指していることを確認するに、ユーザーは、文字列を手動で更新する必要があります。 文字列は不透明になっているためにが必ずしもクリア更新方法です。  
  
 ソース管理プラグインはという特別なファイルで、"AuxPath"および"ProjName"の文字列を格納することによってこの問題を回避することができます、 *MSSCCPRJ.SCC*ファイル。 これはローカルのクライアント側のファイルが所有し、プラグインによって管理されます。 このファイルは、ソース管理下には格納されませんが、ソース管理ファイルを含むすべてのディレクトリのプラグインによって生成されます。 どのファイルは、Visual Studio のソリューションとプロジェクト ファイルを確認するには、ソース管理プラグインは、標準またはユーザーが指定したリストに対してファイルの拡張機能を比較できます。 IDE を検出するプラグインのサポート、 *MSSCCPRJ.SCC*ファイル、ソリューションおよびプロジェクトのファイルに、"AuxPath"および"ProjName"の文字列を埋め込むためになったらおよびからこれらの文字列を読み取り、 *MSSCCPRJ.SCC*ファイルを代わりにします。  
  
 ソース管理プラグインをサポートする、 *MSSCCPRJ.SCC*ファイルは、次のガイドラインに従う必要があります。  
  
-   存在できる 1 つだけ置く*MSSCCPRJ.SCC*ディレクトリごとのファイル。  
  
-   *MSSCCPRJ.SCC*ファイルは、特定のディレクトリ内のソース管理下にある複数のファイルの"AuxPath"と"ProjName"を含めることができます。  
  
-   "AuxPath"文字列は、引用符の内部に必要ありません。 区切り記号として引用符で囲むが許可されます (たとえば、二重引用符のペアを空の文字列を示すために使用できます)。 読み取られるときに、IDE で"AuxPath"文字列からすべての引用符は削除、 *MSSCCPRJ.SCC*ファイル。  
  
-   "ProjName"の文字列で、 *MSSCCPRJ します。SCC ファイル*まったくから返される文字列に一致する必要があります、`SccGetProjPath`関数。 関数によって返される文字列に引用符で囲むの文字列がある場合、 *MSSCCPRJ.SCC*ファイルに引用符が必要、その近くに、その逆です。  
  
-   *MSSCCPRJ.SCC*ファイルが作成されたか、ファイルがソース管理下に配置されるたびに更新します。  
  
-   場合、 *MSSCCPRJ.SCC*ファイルが削除された、プロバイダーが再生成、次回そのディレクトリに関連のソース管理操作を実行します。  
  
-   *MSSCCPRJ.SCC*ファイルは、定義済みの形式に厳密に従う必要があります。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ を示しています。SCC ファイルの形式  
 サンプルを次に、 *MSSCCPRJ.SCC*ファイル形式 (行番号は、ガイドとしてのみ提供されているし、ファイルの本文に含まれない)。  
  
 [Line 1] `SCC = This is a Source Code Control file`  
  
 [Line 2]  
  
 [Line 3] `[TestApp.sln]`  
  
 [Line 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Line 6]  
  
 [Line 7] `[TestApp.csproj]`  
  
 [Line 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 9] `SCC_Project_Name = "$/TestApp"`  
  
 最初の行では、ファイルの目的の状態し、この種類のすべてのファイルの署名として機能します。 この行はすべてこれとまったく同じ表示する必要があります*MSSCCPRJ.SCC*ファイル。  
  
 `SCC = This is a Source Code Control file`  
  
 次のセクションでは、角かっこで囲んで、ファイル名でマークされている、各ファイルの設定について説明します。 このセクションでは、追跡されているファイルごとに繰り返されます。 この行は、ファイル名の例を具体的が`[TestApp.csproj]`します。 IDE では、次の 2 つの行が必要です。 ただし、定義されている値のスタイルは定義しません。 変数は、`SCC_Aux_Path`と`SCC_Project_Name`します。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 このセクションに末尾の区切り記号はありません。 ファイルに表示されるすべてのリテラルと同様に、ファイルの名前は、scc.h ヘッダー ファイルで定義されます。 詳細については、次を参照してください。[ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)