---
title: "移植可能なプロファイル データ ファイルのコマンド ラインからの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 移植可能なプロファイル データ ファイルのコマンド ラインからの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロファイル データの共有を簡単に行うために、[VSPerfReport](../profiling/vsperfreport.md) コマンド ライン ツールを使用して、プロファイリング実行用のシンボルを .vsp ファイル内に埋め込むことができます。  
  
 また、容量が小さく、IDE への読み込みも速い解析済みプロファイル データ \(.vsps\) ファイルを作成することもできます。  
  
> [!NOTE]
>  シンボル \(.pdb\) ファイルが **VSPerfReport** から使用できる状態であることを確認してください。  詳細については、「[方法: コマンド ラインからシンボル ファイルの場所を指定する](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)」を参照してください。  
>   
>  **VSReport** へのパスの詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
>   
>  .vsps ファイル内のプロファイル データは、フィルター処理できません。  
  
### プロファイリング実行用のシンボルをプロファイル データ \(.vsp\) ファイルに埋め込むには  
  
-   コマンド プロンプト ウィンドウで、次のコマンドを入力します。  
  
     \<パスの\>**VSPerfReport \<**VSP ファイル\>**\/PackSymbols**  
  
     既定では、.vsps ファイルの名前は .vsp ファイルの基本名を使用して決定されます。  別の名前を指定するには、**Output** オプションを使用します。  
  
### サマリー プロファイル データ ファイルを作成するには  
  
-   コマンド プロンプト ウィンドウで、次のコマンドを入力します。  
  
     \<パスの\>**VSPerfReport \<**VSP ファイル\>のファイル名\>**\/Output:**\<**\/SummaryFile**\[\]  
  
     既定では、.vsps ファイルの名前は .vsp ファイルの基本名を使用して決定されます。  別の名前を指定するには、**Output** オプションを使用します。