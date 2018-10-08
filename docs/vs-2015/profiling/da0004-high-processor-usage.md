---
title: 'DA0004: プロセッサ使用率が高くなっています | Microsoft Docs'
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
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 759ba305335c75591bf975e40f011f31edd1bdb5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548477"
---
# <a name="da0004-high-processor-usage"></a>DA0004: プロセッサ使用率が高くなっています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DA0004: 高のプロセッサ使用率](https://docs.microsoft.com/visualstudio/profiling/da0004-high-processor-usage)します。  
  
規則 Id |DA0004 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |インストルメンテーションのサンプリング |  
|メッセージ |プロセッサ使用率が 75% を超えるが一貫します。 CPU 主体のアプリケーションのサンプリング モードの使用を検討します |。  
|規則の種類 |情報 |  
  
 サンプリング、.NET メモリ、またはリソース競合メソッドを使用してプロファイリングを行うときは、この規則を呼び出すためのサンプルを少なくとも 10 個収集する必要があります。  
  
## <a name="cause"></a>原因  
 プロセッサ (CPU) 使用率の大きな割合を、インストルメンテーション メソッドを使用して収集されたプロファイル データが占めていました。 CPU 主体のアプリケーションをプロファイリングするときは、サンプリング プロファイリング方式の使用を検討してください。  
  
## <a name="rule-description"></a>規則の説明  
 このプロファイリングの実行中、プロセッサは常にビジー状態でした。 CPU 使用率はが高い場合、CPU 主体のアプリケーションであることを示している可能性があります。 インストルメント化によるプロファイリングは、通常、CPU 使用シナリオの調査には効果的ではありません。 ほとんどの時間をプロセッサ上の命令の実行に費やすアプリケーションをプロファイリングする場合、通常はサンプリングの方が効果的です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 関数のタイミングが必要な場合、またはプロセッサのボトルネックよりも入出力に関心がある場合以外は、インストルメンテーション メソッドではなく、サンプリング メソッドでアプリケーションのプロファイリングをやり直すことを検討してください。




