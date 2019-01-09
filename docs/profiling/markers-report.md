---
title: マーカー レポート | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f85da57219d2912ddec1314ed7535b8270b9c50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931159"
---
# <a name="markers-report"></a>マーカー レポート
マーカー レポートには、表示されているタイム フレーム内のマーカーが一覧表示されます。  レーンをパン、ズーム、または非表示にすると、マーカーの表示/非表示が切り替わる場合があります。 レポートには、各マーカーに関する次の情報が含まれています。  
  
- それを開始したときの、トレースの開始からの相対時間。  
  
- 実行継続時間。 フラグとメッセージの場合には、瞬間を表すために実行継続時間はゼロです。  
  
- それを生成したスレッドの ID。  
  
- それを生成した Event Tracking for Windows (ETW) プロバイダー。  
  
- それが書き始められたマーカーの系列。  
  
- それが属しているイベントのカテゴリ。  
  
- その重要度レベル。  
  
- その種類 (スパン、フラグ、またはメッセージ)。  
  
- それが表すものについての概要  
  
  マーカー レポートを CSV ファイルとして保存するには、**[エクスポート]** ボタンを選択します。 CSV ファイル内のデータは、他のアプリやツールで使用することができます。  
  
> [!NOTE]
>  マーカー レポートでは 1,000 個のマーカーを表示できます。 すべてのマーカーを表示するには、レポート全体を CSV ファイルにエクスポートします。