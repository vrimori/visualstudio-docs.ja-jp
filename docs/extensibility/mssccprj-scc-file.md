---
title: "MSSCCPRJ です。SCC ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90a21ba6aafa0c5d06565c66531e2a6779aa419f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ です。SCC ファイル
IDE を使用してソース管理下にある、Visual Studio ソリューションまたはプロジェクトが配置されると、IDE は、文字列の形式でプラグイン ソース管理から 2 つの重要な情報を受信します。 これらの文字列では、"AuxPath"と"ProjName"は、IDE に不透明なは、バージョン管理でソリューションまたはプロジェクトを検索するが、プラグインで使用します。 IDE 通常取得これらの文字列を初めて呼び出すことによって、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)、それらを以降の呼び出しをソリューションまたはプロジェクト ファイルに保存し、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。 ソリューションとプロジェクト ファイルに埋め込まれているときに、"AuxPath"および"ProjName"文字列が自動的に更新されません、ユーザーは、分岐を分岐します。 または、バージョン管理では、ソリューションおよびプロジェクトのファイルをコピーします。 ソリューションとプロジェクト ファイルがバージョン管理で、正しい場所を指していることを確認するに、ユーザーは、文字列を手動で更新する必要があります。 文字列は不透明にすることを意図した、ので可能性がありますいない常に明確にあります更新方法です。  
  
 ソース管理プラグインは、MSSCCPRJ と呼ばれる特別なファイルで、"AuxPath"および"ProjName"文字列を格納することによってこの問題を回避できます。SCC ファイルです。 自分が所有し、プラグインによって保持されるローカルのクライアント側のファイルです。 このファイルはソース管理下に配置しないが、ソース管理ファイルを含むすべてのディレクトリのプラグインによって生成されます。 どのファイルは、Visual Studio ソリューションとプロジェクト ファイルを確認するのに、ソース管理プラグインは、標準またはユーザーが指定したリストに対してファイルの拡張機能を比較できます。 IDE では、プラグインをサポートしている、MSSCCPRJ が検出されます。"AuxPath"の埋め込みが行われなくなります SCC ファイルとソリューションとプロジェクト ファイル、およびそのにへの文字列の"ProjName"が、MSSCCPRJ からそれらの文字列を読み取ります。SCC ファイルの代わりにします。  
  
 ソース管理プラグイン、MSSCCPRJ をサポートします。SCC ファイルは、次のガイドラインに従う必要があります。  
  
-   1 つ MSSCCPRJ のみできます。1 つのディレクトリのファイルを SCC です。  
  
-   MSSCCPRJ です。SCC ファイルでは、複数のファイルのディレクトリ内のソース管理下にある"AuxPath"と"ProjName"を含めることができます。  
  
-   "AuxPath"文字列は、その中の引用符を持たないでください。 引用符区切り記号としてすることができます (たとえば、二重引用符のペアを空の文字列を示すために使用できます)。 IDE は、MSSCCPRJ から読み取られたときに"AuxPath"文字列からすべての引用符を削除します。SCC ファイルです。  
  
-   MSSCCPRJ"ProjName"文字列です。SCC ファイルはまったくから返される文字列と一致する必要があります、`SccGetProjPath`関数。 関数によって返される文字列に引用符で囲む、MSSCCPRJ 内の文字列がある場合。SCC ファイルには、引用符が必要です。 周り、またはその逆です。  
  
-   MSSCCPRJ です。SCC ファイルが作成またはファイルがソース管理下に配置されるたびに更新します。  
  
-   MSSCCPRJ 場合。SCC ファイルは削除されます、プロバイダーを再生成する、次回そのディレクトリに関連ソース管理操作を実行します。  
  
-   MSSCCPRJ です。SCC ファイルは、定義された書式を厳密に従う必要があります。  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>MSSCCPRJ を示しています。SCC ファイルの形式  
 MSSCCPRJ のサンプルを次に示します。SCC ファイルの形式 (行番号をガイドとして提供されておよびファイルの本文に含めないで):  
  
 [Line 1]`SCC = This is a Source Code Control file`  
  
 [Line 2]  
  
 [行 3]`[TestApp.sln]`  
  
 [行 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 5]`SCC_Project_Name = "$/TestApp"`  
  
 [行 6]  
  
 [Line 7]`[TestApp.csproj]`  
  
 [Line 8]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Line 9]`SCC_Project_Name = "$/TestApp"`  
  
 最初の行は、ファイルの目的の状態をこの種類のすべてのファイルの署名として機能します。 この線は正確に次のようにすべて MSSCCPRJ で表示されます。SCC ファイル:  
  
 `SCC = This is a Source Code Control file`  
  
 後に、角かっこで囲んで、ファイル名でマークされている、各ファイルの設定のセクションです。 このセクションでは、追跡されているファイルごとに繰り返されます。 この行は、ファイル名のサンプル、つまり、`[TestApp.csproj]`です。 IDE では、次の 2 行が必要です。 ただし、定義されている値のスタイルは定義しません。 変数は、`SCC_Aux_Path`と`SCC_Project_Name`です。  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 このセクションに末尾の区切り記号はありません。 ファイルに表示されるすべてのリテラルと同様に、ファイルの名前は、scc.h ヘッダー ファイルで定義されます。 詳細については、次を参照してください。[文字列はソース管理プラグインを検索するためのキーとして使用](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)です。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)