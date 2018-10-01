---
title: '方法: インストルメント化前のコマンドおよびインストルメント化後のコマンドを指定する | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20cf4545a217adf07cc753a1d2ab190a00e3d4f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536796"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>方法 : インストルメント前のコマンドおよびインストルメント後のコマンドを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: コマンドおよびインストルメント化後のコマンドを指定](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-pre-and-post-instrument-commands)します。  
  
パフォーマンス セッションのバイナリがインストルメント化される前か後に実行されるコマンドを指定できます。 コマンド ラインから発行できるコマンドはすべて、インストルメント化前のイベントまたはインストルメント化後のイベントとして指定できます。 たとえば、バイナリのインストルメント化後に実行されるバッチ ファイルで、厳密な名前キーを持つアセンブリの再署名を自動化するコマンドを指定できます。  
  
 プロファイル実行におけるインストルメント化されたすべてのバイナリ、または個々のバイナリに対してコマンドを指定できます。 ただし、インストルメンテーション プロセスの前に実行するよう指定できるインストルメント化前のコマンドは 1 つだけであり、インストルメンテーション プロセスの後に実行するよう指定できるインストルメント化後のコマンドも 1 つだけです。 すべてのバイナリと個々のバイナリの両方に対してコマンドを指定することはできません。 すべてのバイナリに対してコマンドを指定すると、そのコマンドはセッションの各バイナリのインストルメンテーションの前または後に実行されます。  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 コマンドが実行される作業ディレクトリは、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] を実行しているオペレーティング システムと、プロファイリング対象アプリケーションの対象プラットフォームによって異なります。  
  
 **32 ビット コンピューター**  
  
 32 ビット コンピューターでの既定のプロファイリング ツール ディレクトリは、Drive\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools です。  
  
 **64 ビット コンピューター**  
  
 64 ビット コンピューターでは、プロファイリングするアプリケーションのターゲット プラットフォームに応じてパスを指定します。  
  
-   32 ビット アプリケーションの場合、既定のプロファイリング ツール ディレクトリは以下のとおりです。  
  
     *Drive*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools  
  
-   64 ビット アプリケーションの場合、既定のプロファイリング ツール ディレクトリは以下のとおりです。  
  
     *Drive*\Program Files (x86)\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\x64  
  
### <a name="to-specify-pre-instrument-commands"></a>インストルメント化前のコマンドを指定するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   パフォーマンス セッションのすべてのバイナリに対してインストルメント化前のコマンドを指定するには、**パフォーマンス エクスプローラー**でパフォーマンス セッション ノードを選択し、右クリックして **[プロパティ]** を選択します。  
  
    -   特定のバイナリにインストルメント化前のコマンドを指定するには、パフォーマンス セッションの **[ターゲット]** リストにあるバイナリの名前を右クリックし、**[プロパティ]** を選択します。  
  
2.  **[プロパティ ページ]** で、**[インストルメンテーション]** をクリックします。  
  
3.  **[インストルメント化前のイベント]** の **[コマンド ライン]** テキスト ボックスにコマンドを入力します。  
  
    > [!NOTE]
    >  **[コマンド ライン]** ボックスの横にある省略記号ボタン **(…)** をクリックし、適切な .exe、.cmd、または .bat ファイルを参照して選択できます。  
  
4.  **[OK]** をクリックします。  
  
     コマンドを削除することなくその実行を無効にするには、**[インストルメンテーションから除外]** チェック ボックスを選択します。 コンパイラまたはリンカーの設定を変更するには、プロジェクトのプロパティ ページを使用します。  
  
### <a name="to-specify-post-instrument-commands"></a>インストルメント化後のコマンドを指定するには  
  
1.  次のいずれかの操作を実行します。  
  
    -   パフォーマンス セッションのすべてのバイナリに対してインストルメント化後のコマンドを指定するには、**パフォーマンス エクスプローラー**でパフォーマンス セッション ノードを選択し、右クリックして **[プロパティ]** を選択します。  
  
    -   特定のバイナリにインストルメント化後のコマンドを指定するには、パフォーマンス セッションの **[ターゲット]** リストにあるバイナリの名前を右クリックし、**[プロパティ]** を選択します。  
  
2.  **[プロパティ ページ]** で、**[インストルメンテーション]** をクリックします。  
  
3.  **[インストルメント化後のイベント]** の **[コマンド ライン]** テキスト ボックスにコマンドを入力します。  
  
    > [!NOTE]
    >  **[コマンド ライン]** ボックスの横にある省略記号ボタン **(…)** をクリックし、適切な .exe、.cmd、または .bat ファイルを参照して選択できます。  
  
4.  **[OK]** をクリックします。  
  
     コマンドを削除することなくその実行を無効にするには、**[インストルメンテーションから除外]** チェック ボックスを選択します。 コンパイラまたはリンカーの設定を変更するには、プロジェクトのプロパティ ページを使用します。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス セッションの構成](../profiling/configuring-performance-sessions.md)



