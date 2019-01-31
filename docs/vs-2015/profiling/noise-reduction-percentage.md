---
title: 不要項目の非表示の割合 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c6407b40f58c3acc02705379768085793a2b79b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787710"
---
# <a name="noise-reduction-percentage"></a>不要項目の非表示の割合
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

既定では、不要項目の非表示の割合の設定値は 2 です。 この設定値以上の包括時間の割合を持つエントリだけが、コール ツリーに表示されます。 設定を変更することによって、コール ツリーに表示されるエントリの数を制御できます。 たとえば、値を 10 に変更すると、10% 以上の包括時間を持つエントリだけがコール ツリーに表示されます。 この設定値を増やすと、プロセスのパフォーマンスに対する影響が大きいエントリに集中することができます。
