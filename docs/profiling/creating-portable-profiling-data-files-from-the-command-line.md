---
title: コマンド ラインからの移植可能なプロファイル データ ファイルの作成 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25f2faf1be7f2e8ff5c96eca16ef2de9be2514db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815846"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>コマンド ラインからの移植可能なプロファイル データ ファイルの作成
プロファイル データの共有を簡単に行うために、[VSPerfReport](../profiling/vsperfreport.md) コマンドライン ツールを利用し、プロファイリング実行用のシンボルを .*vsp* ファイル内に埋め込むことができます。  
  
 また、サイズが小さく、IDE にすばやく読み込むことのできる解析済みプロファイル データ (.*vsps*) ファイルを作成することもできます。  
  
> [!NOTE]
>  シンボル (.*pdb*) ファイルが **VSPerfReport** で利用できることを確認します。 詳細については、「[方法: コマンド ラインからシンボル ファイルの場所を指定する](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)」を参照してください。  
>   
>  **VSReport** のパスの詳細については、[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)に関するページをご覧ください。  
>   
>  .*vsps* ファイルのプロファイリング データはフィルター処理できません。  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>プロファイリング実行のシンボルをプロファイリング データ (.*vsp*) ファイルに組み込むには  
  
-   [コマンド プロンプト] ウィンドウで、次のコマンドを入力します。  
  
     \<Path>**VSPerfReport \<** VSP File> **/PackSymbols**  
  
     既定では、.*vsps* ファイルには、.*vsp* ファイルのベース名で名前が付けられます。 **Output** オプションを利用し、代替名を指定できます。  
  
### <a name="to-create-a-summary-profiling-data-file"></a>概要プロファイリング データ ファイルを作成するには  
  
-   [コマンド プロンプト] ウィンドウで、次のコマンドを入力します。  
  
     \<Path>**VSPerfReport \<** VSP File> **/SummaryFile** [**/Output:**\<File Name>]  
  
     既定では、.*vsps* ファイルには、.*vsp* ファイルのベース名で名前が付けられます。 **Output** オプションを利用し、代替名を指定できます。