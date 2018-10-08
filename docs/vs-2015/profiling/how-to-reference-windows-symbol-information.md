---
title: '方法: Windows シンボル情報を参照する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385b9e4511c44c02a358eb88471cd8369971ed1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548401"
---
# <a name="how-to-reference-windows-symbol-information"></a>方法: Windows シンボル情報を参照する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: Windows シンボル情報を参照](https://docs.microsoft.com/visualstudio/profiling/how-to-reference-windows-symbol-information)します。  
  
Visual Studio プロファイリング ツールは、シンボル (.pdb) ファイルを使用して、プログラム バイナリの関数名などのシンボル名を解決します。 次の手順を使って、ローカル コンピューター上の Windows のバージョンに適切な .pdb ファイルを自動的にダウンロードし、更新することができます。  
  
> [!NOTE]
>  この設定は、既存のレポートには影響しません。 シンボル サーバーを指定した後に作成されたレポートだけにシンボル情報が含まれます。  
  
 詳細については、[シンボル (.pdb) ファイルとソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)に関する記事をご覧ください。  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft シンボル サーバーを使用するには  
  
1.  シンボル ファイルの情報を格納するフォルダーを作成します (例: C:\SymbolCache)。  
  
2.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
     **[オプション]** ダイアログ ボックスが表示されます。  
  
3.  **[デバッグ]** ツリーを展開し、**[シンボル]** をクリックします。  
  
4.  **[シンボル ファイル (.pdb) の場所]** で、**[Microsoft シンボル サーバー]** を選択します。  
  
5.  **[シンボル サーバーからシンボルをキャッシュするディレクトリ]** ボックスに、次に示すように、手順 1. で作成したフォルダーのパスを入力します。  
  
     **C:\SymbolCache**  
  
     あるいは省略記号ボタン (**...**) をクリックして、**[フォルダの参照]** ダイアログ ボックスでディレクトリを選択することもできます。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [方法: シンボル情報をシリアル化する](../profiling/how-to-serialize-symbol-information.md)



