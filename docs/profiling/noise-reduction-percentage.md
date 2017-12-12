---
title: "不要項目の非表示の割合 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.filter
helpviewer_keywords: Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c5fe0e705441311a7d5bdade0e794729ae8f1d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="noise-reduction-percentage"></a>不要項目の非表示の割合
既定では、不要項目の非表示の割合の設定値は 2 です。 この設定値以上の包括時間の割合を持つエントリだけが、コール ツリーに表示されます。 設定を変更することによって、コール ツリーに表示されるエントリの数を制御できます。 たとえば、値を 10 に変更すると、10% 以上の包括時間を持つエントリだけがコール ツリーに表示されます。 この設定値を増やすと、プロセスのパフォーマンスに対する影響が大きいエントリに集中することができます。