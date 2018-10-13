---
title: '[VC++ プロジェクトの設定][オプション] ダイアログ ボックス - [プロジェクトおよびソリューション] | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a1491d639ace0cba80530ea1613525480bad07f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238863"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>[VC++ プロジェクトの設定][オプション] ダイアログ ボックス - [プロジェクトおよびソリューション]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
このダイアログ ボックスを使用すると、ビルドのログおよびサポートするファイルの種類に関連する [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] プロジェクトの設定を定義できます。  
  
### <a name="to-access-this-dialog-box"></a>このダイアログ ボックスを表示するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[プロジェクトおよびソリューション]** をクリックし、**[VC++ プロジェクトの設定]** をクリックします。  
  
## <a name="build-customization-search-path"></a>[ビルドのカスタマイズの検索パス]  
 .rules ファイルを含むディレクトリの一覧を指定します。これは、プロジェクトのビルド ルールを定義するときに役立ちます。  
  
## <a name="build-logging"></a>[ビルドのログ]  
 **はい**  
 ビルド ログ ファイルの生成をオンにします。 このオプションを指定すると、プロジェクトの中間ファイル ディレクトリに BuildLog.htm ファイルが生成されます。 新しくビルドを実行するたびに、以前の BuildLog.htm ファイルは上書きされます。  
  
 **No**  
 ビルド ログ ファイルの生成をオフにします。  
  
## <a name="build-timing"></a>[ビルド時間]  
 **はい**  
 ビルドの時間測定をオンにします。 このオプションをオンにすると、ビルドが完了するまでに要した時間がアウトプット ウィンドウに表示されます。 詳細については、「[[出力] ウィンドウ](../../ide/reference/output-window.md)」を参照してください。  
  
 **No**  
 ビルドの時間測定をオフにします。  
  
## <a name="extensions-to-hide"></a>[表示しない拡張子]  
 **[すべてのファイルを表示]** が有効になっているときに**ソリューション エクスプローラー**に表示されないファイルのファイル名拡張子を指定します。  
  
## <a name="extensions-to-include"></a>[含める拡張子]  
 プロジェクトに移植できるファイルのファイル名拡張子を指定します。  
  
## <a name="maximum-concurrent-c-compilations"></a>[同時実行する C++ コンパイルの最大数]  
 C++ の並列コンパイルに使用する CPU コアの最大数を指定します。  
  
## <a name="show-environment-in-log"></a>[ログで環境を表示]  
 **はい**  
 ビルド ログ ファイルに環境変数をリストします。 このオプションを使用すると、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] プロジェクトのビルド中に、すべての環境変数がビルド ログ ファイルにエコーされます。  
  
 **No**  
 ビルド ログ ファイルから環境変数を除外します。  
  
## <a name="solution-explorer-mode"></a>[ソリューション エクスプローラー モード]  
 **[プロジェクト内のファイルのみ表示]**  
 プロジェクト内のファイルだけが表示されるように、**ソリューション エクスプローラー**を構成します。  
  
 **[すべてのファイルを表示]**  
 プロジェクト内のファイルとディスク上のファイルがプロジェクト フォルダー内に表示されるように、**ソリューション エクスプローラー**を構成します。  
  
## <a name="see-also"></a>関連項目  
 [C/C++ プログラムのビルド](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [C/C++ ビルドのリファレンス](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)



