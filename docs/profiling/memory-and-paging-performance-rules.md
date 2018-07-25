---
title: メモリとページングのパフォーマンス規則 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec1acb6763d408f9f13ec3044e2cd8137d34e634
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237654"
---
# <a name="memory-and-paging-performance-rules"></a>メモリとページングのパフォーマンス規則
メモリとページングのカテゴリのパフォーマンス規則は、アプリケーションのパフォーマンスと応答性に影響を与える可能性があるページング アクティビティをプロファイル実行で特定します。  
  
|||  
|-|-|  
|[DA0014: ディスクへのアクティブなメモリのページングが非常に高率で発生しています](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|ディスクへのアクティブなメモリのページングがプロファイリング実行全体において非常に高率で発生しています。 通常、このレベルのページング率は、アプリケーションのパフォーマンスと応答性に影響します。 アルゴリズムを修正してメモリの割り当てを減らすことを検討してください。 また、アプリケーションのメモリ要件も検討した方がよいでしょう。 より多くのメモリを備えたコンピューターでプロファイリングを再度実行してみてください。 この規則は、ページング アクティビティの量が規則 D0017 の上限のしきい値を超えた場合に適用されます。|  
|[DA0017: ディスクへのアクティブなメモリのページングが高率で発生しています](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|ディスクへのアクティブなメモリのページングがプロファイリング実行全体において比較的高率で発生しています。 通常、このレベルのページング率は、アプリケーションのパフォーマンスと応答性に影響します。 アルゴリズムを修正してメモリの割り当てを減らすことを検討してください。 また、アプリケーションのメモリ要件も検討した方がよいでしょう。 より多くのメモリを備えたコンピューターでプロファイリングを再度実行してみてください。|