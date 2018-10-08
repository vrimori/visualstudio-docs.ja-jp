---
title: パフォーマンス ツールに関する問題のトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 264e6cf75043c1a05784180a29526091fb4c66ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534585"
---
# <a name="troubleshooting-performance-tools-issues"></a>パフォーマンス ツールに関する問題のトラブルシューティング
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[パフォーマンス ツールに関する問題のトラブルシューティング](https://docs.microsoft.com/visualstudio/profiling/troubleshooting-performance-tools-issues)します。  
  
プロファイリング ツールを使用するときに、次の問題のいずれかが発生する場合があります。  
  
-   [プロファイリング ツールでデータが収集されない](#NoDataCollected)  
  
-   [パフォーマンス ビューとレポートに関数名ではなく番号が表示される](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> プロファイリング ツールでデータが収集されない  
 アプリケーションのプロファイリングを実行しても、プロファイリング データ (.vsp) ファイルが作成されず、出力ウィンドウまたはコマンド ウィンドウに次の警告が表示されます。  
  
 PRF0025: データは収集されませんでした。  
  
 この問題は、次の複数の問題が原因で発生することがあります。  
  
-   サンプリングまたは .NET メモリ メソッドを使用してプロファイリングしたプロセスによって、子プロセスが起動されます。この子プロセスは、アプリケーションの作業を実行するプロセスになります。 たとえば、一部のアプリケーションでは、コマンド ラインを読み取り、Windows アプリケーションまたはコマンド ライン アプリケーションのどちらとして起動したかを決定します。 Windows アプリケーションが要求された場合、元のプロセスは Windows アプリケーションとして構成された新しいプロセスを起動し、元のプロセスは終了します。 プロファイリング ツールは子プロセスのデータを自動的に収集しないため、データは収集されません。  
  
     この状況でプロファイリング データを収集するには、プロファイラーでアプリケーションを起動するのではなく、子プロセスにプロファイラーをアタッチします。 詳細については、「[方法 : 実行中のプロセスにパフォーマンス ツールをアタッチする/実行中のプロセスからパフォーマンス ツールをデタッチする](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)」および「[Attach (VSPerfCmd)](../profiling/attach.md)」を参照してください  
  
##  <a name="NoSymbols"></a>パフォーマンス ビューとレポートに関数名ではなく番号が表示される  
 アプリケーションのプロファイリング後、レポートとビューに関数名ではなく番号が表示されます。  
  
 この問題の原因は、ソース コード情報 (関数名や行番号) をコンパイル済みのファイルにマップするシンボル情報を含む .pdb ファイルが、プロファイリング ツールの解析エンジンによって見つけられなかったことです。 既定では、アプリケーション ファイルのビルド時に、コンパイラによって .pdb ファイルが作成されます。 .pdb ファイルのローカル ディレクトリへの参照は、コンパイル済みのアプリケーションに格納されます。 解析エンジンは、参照されるディレクトリで .pdb ファイルを探し、次にアプリケーション ファイルを現在含んでいるファイルを検索します。 .pdb ファイルが見つからない場合、解析エンジンは関数名ではなく関数のオフセットを使用します。  
  
 この問題は、2 つの方法のいずれかで修復できます。  
  
-   .pdb ファイルを検索し、アプリケーション ファイルと同じディレクトリに配置します。  
  
-   プロファイリング データ (.vsp) ファイルにシンボル情報を埋め込みます。 詳細については、「[パフォーマンス データ ファイルを使ったシンボル情報の保存](../profiling/saving-symbol-information-with-performance-data-files.md)」を参照してください。  
  
> [!NOTE]
>  解析エンジンを使用する場合、.pdb ファイルと、コンパイル済みのアプリケーション ファイルを同じバージョンにする必要があります。 古いビルドまたは新しいビルドのアプリケーション ファイルの .pdb ファイルは機能しません。



