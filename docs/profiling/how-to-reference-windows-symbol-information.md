---
title: "方法: Windows シンボル情報を参照する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パフォーマンス ツール、シンボル サーバー"
  - "サーバー、シンボル サーバー"
  - "プロファイリング ツール、シンボル サーバー"
  - "シンボル サーバー"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# 方法: Windows シンボル情報を参照する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio のプロファイリング ツールには、プログラム バイナリの関数名などのシンボル名を解決するには、シンボル \(.pdb\) ファイルを使用します。  次の手順を実行すると、ローカル コンピューターにインストールされている Windows のバージョンに適切な .pdb ファイルを自動的にダウンロードして更新できます。  
  
> [!NOTE]
>  この設定は、既存のレポートには影響しません。  シンボル サーバーを指定した後に作成されたレポートだけにシンボル情報が含まれます。  
  
 詳細については、「[シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)」を参照してください。  
  
### Microsoft のシンボル サーバーを使用するには  
  
1.  C:\\SymbolCache など、シンボル ファイルの情報を格納するフォルダーを作成します。  
  
2.  \[ツール\] メニューの \[オプション\] をクリックします。  
  
     **\[オプション\]** ダイアログ ボックスが表示されます。  
  
3.  **\[デバッグ\]** ツリーを展開し、**\[シンボル\]** をクリックします。  
  
4.  **\[シンボル ファイル \(.pdb\) の場所\]** で、**\[Microsoft シンボル サーバー\]** を選択します  
  
5.  **\[シンボル サーバーからシンボルをキャッシュするディレクトリ\]** ボックスに、次に示すように、手順 1. で作成したフォルダーのパスを入力します。  
  
     C:\\SymbolCache  
  
     省略記号ボタン \(**...**\) をクリックし、**\[フォルダの参照\]** ダイアログ ボックスでディレクトリを選択できます。  
  
## 参照  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)   
 [方法: シンボル情報をシリアル化する](../profiling/how-to-serialize-symbol-information.md)