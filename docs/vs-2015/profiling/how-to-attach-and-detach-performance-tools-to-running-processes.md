---
title: '方法 : 実行中のプロセスにパフォーマンス ツールをアタッチする/実行中のプロセスからパフォーマンス ツールをデタッチする | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ee38f210585124f8492f6aed9f062003602f287
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895320"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>方法 : 実行中のプロセスにパフォーマンス ツールをアタッチする/実行中のプロセスからパフォーマンス ツールをデタッチする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

実行中のプロセスに対してプロファイラーのアタッチまたはデタッチを行うことで、パフォーマンス データのサンプリングや収集を容易にすることができます。 この方法は、アプリケーションの読み込み時間に関するデータの収集を行わない場合や、プロセスが特定の状態に達した後にそのパフォーマンスを監視する場合に、プロセスのプロファイリングを行うために使用します。  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 統合開発環境 (IDE) の内部からプロセスのアタッチおよびデタッチを実行する手順を次に示します。 コマンド ライン ツールの使用方法の詳細については、「[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)」を参照してください。 サービスのプロファイリングの詳細については、「[コマンド ライン プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)」を参照してください。  
  
 プロファイルに使用できるプロセスは、コンピューターの管理者によって設定されたユーザーのアクセス許可によって異なります。 たとえば、ユーザー アカウントには、次のようなアクセス許可が設定されていることがあります。  
  
- 高度なプロファイリング機能 (管理者が起動用のドライバーとサービスを設定している場合)。  
  
- サンプル プロファイルのみ (ドメイン ユーザーの場合)。  
  
- ユーザーに対してプロファイルへのアクセスを拒否。  
  
  詳細については、「[プロファイルと Windows Vista のセキュリティ](../profiling/profiling-and-windows-vista-security.md)」および「[VSPerfCmd](../profiling/vsperfcmd.md)」の ADMIN オプションを参照してください。  
  
### <a name="to-attach-to-a-running-process"></a>実行中のプロセスにアタッチするには  
  
1.  **[分析]** メニューの **[プロファイラー]** をポイントし、**[アタッチ/デタッチ]** をクリックします。  
  
     \- または -  
  
     **パフォーマンス エクスプローラー**でパフォーマンス セッションを右クリックし、**[アタッチ/デタッチ]** をクリックします。  
  
     **[プロファイラーをプロセスにアタッチします]** ダイアログ ボックスが表示されます。  
  
2.  アタッチするプロセスの名前をクリックします。  
  
3.  **[アタッチ]** をクリックします。  
  
### <a name="to-detach-from-a-running-process"></a>実行中のプロセスからデタッチするには  
  
1.  **[分析]** メニューの **[プロファイラー]** をポイントし、**[アタッチ/デタッチ]** をクリックします。  
  
     \- または -  
  
     **パフォーマンス エクスプローラー**でパフォーマンス セッションを右クリックし、**[アタッチ/デタッチ]** をクリックします。  
  
     **[プロファイラーをプロセスにアタッチします]** ダイアログ ボックスが表示されます。  
  
2.  デタッチするイメージの名前をクリックします。  
  
3.  **[デタッチ]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [データ収集の制御](../profiling/controlling-data-collection.md)   
 [パフォーマンス セッションの概要](../profiling/performance-session-overview.md)   
 [方法: 開始と終了のパフォーマンス データの収集](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [プロファイルと Windows Vista のセキュリティ](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)



