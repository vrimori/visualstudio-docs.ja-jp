---
title: パフォーマンス データ ファイルの比較 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd1c93942282c8a5cb3baf9fdf007a0ba55e3ebe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546380"
---
# <a name="comparing-performance-data-files"></a>パフォーマンス データ ファイルの比較
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[パフォーマンス データ ファイルを比較する](https://docs.microsoft.com/visualstudio/profiling/comparing-performance-data-files)します。  
  
プロファイリング ツールのデータ ファイルの比較機能を使用すると、2 つのレポート ファイル (.VSP または .VSPS) を選択し、2 つのプロファイリング セッション間の違い、パフォーマンスの低下、および改善を示すレポートを生成できます。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールのデータ ファイルの比較レポートでは、あるプロファイリング データ ファイルの分析結果と、他のデータ ファイルの基準の分析結果を比較します。 両方のデータ ファイルは、同じプロファイリング メソッドで生成されている必要があります。 分析された比較のレポートは .vsps ファイル形式で保存されます。  
  
 比較レポート ビューには、変化したデータのテーブル ビューが表示されます。 テーブルは、差分、またはベースラインからの変化を表示します。 差分は、古い値、基準値と、新しい分析による結果の値との違いを測定して計算されます。  
  
 プロファイラーのデータの比較は、コード内の関数、アプリケーション内のモジュール、行、命令ポインター (IP)、および種類に基づいて作成できます。  
  
 比較に使用できるプロファイリング データには、列に表示される情報が含まれています。 これらの列名の定義については、「[プロファイル ツールのレポート ビュー](../profiling/performance-report-views.md)」を参照してください。  
  
 しきい値を設定して、ノイズを減らし、指定した量によって変更のない行の比較テーブル ビュー内のデータをフィルター処理することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: パフォーマンス データ ファイルを比較する](../profiling/how-to-compare-performance-data-files.md)



