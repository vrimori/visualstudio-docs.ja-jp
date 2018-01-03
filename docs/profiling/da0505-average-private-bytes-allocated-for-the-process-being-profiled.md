---
title: "DA0505: プロセスに割り当てられた平均プライベート バイト数がプロファイリングされています | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5d37ebd2ec296153eefdb08d52930cfc08614e96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: プロセスに割り当てられた平均プライベート バイト数がプロファイリングされています
|||  
|-|-|  
|規則 ID|DA0505|  
|カテゴリ|リソース管理|  
|プロファイル方法|すべて|  
|メッセージ|この情報は、情報提供のためにのみ収集されました。 Process Private Bytes カウンターは、プロファイリングを行っているプロセスによって割り当てられた仮想メモリを測定します。 報告される値は、全測定期間を通じて計算された平均値です。|  
|規則の種類|情報|  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="rule-description"></a>規則の説明  
 このメッセージにより、プロセスによって割り当てられた現在の仮想メモリ容量がバイト単位で報告されます (プライベート バイト)。 プライベート バイトは、プロセス内部で実行中のスレッドからのみアクセスできるプロセスによって割り当てられた仮想メモリの位置を表します。  
  
 32 ビット コンピューター上で実行されている 32 ビット プロセスの場合、プロセスのアドレス空間のプライベート領域の上限は 2 GB です。 [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831) Boot.ini スイッチを使用して、32 ビット プロセスは、最大 3 GB の仮想メモリを取得できます。 64 ビット コンピューター上で実行されている 32 ビット プロセスの場合、最大 4 GB のプライベート仮想メモリを取得できます。  
  
 64 ビット コンピューター上で実行されている 64 ビット プロセスの場合、最大 8 TB のプライベート仮想メモリを取得できます。  
  
 プロファイリング中のプロセスがアクティブな状態にあるすべての測定間隔を通じて取得された値の平均値が、このメッセージによって報告されます。  
  
 プロセス アドレス空間の詳細については、Windows のメモリ管理のドキュメントの「[Virtual Address Space](http://go.microsoft.com/fwlink/?LinkId=177832)」 (仮想アドレス空間) を参照してください。  
  
## <a name="how-to-use-rule-data"></a>規則データの使用方法  
 報告された値を使用して、特定のプログラムの異なるバージョンやビルドを比較したり、さまざまなプロファイリング シナリオにおけるアプリケーションのパフォーマンスを確認したりします。