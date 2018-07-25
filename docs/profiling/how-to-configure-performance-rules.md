---
title: '方法: パフォーマンス規則を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe6e10c42188cab23c75262d947c7deb9c28ea5
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816030"
---
# <a name="how-to-configure-performance-rules"></a>方法: パフォーマンス規則を構成する
Visual Studio プロファイリング ツールのパフォーマンスの警告は、プロファイリング対象のアプリケーションにおいてプログラムの実行速度が低下する問題を示します。 警告は、有用なデータを収集するために、収集メソッドを変更する必要があることを示している場合もあります。 パフォーマンスの警告は、プロファイル セッションで自動的に生成され、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] でプロファイル データ ファイルを開いたときに、**[エラー一覧]** ウィンドウに表示されます。 ただし、警告によっては、目的のシナリオに当てはまらないものや、誤って生成されるものもあります。 このため、特定の警告を表示または非表示にするよう、パフォーマンスの警告を構成できます。  
  
### <a name="to-configure-profiler-performance-warnings"></a>プロファイラーのパフォーマンス警告を構成するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[パフォーマンス ツール]** を展開し、**[規則]** をクリックします。  
  
3.  警告の **[ID]** および名前の隣にあるチェック ボックスをオンまたはオフにすることで、警告を有効または無効にすることができます。  
  
4.  規則の警告レベルを指定するには、規則の横の **[アクション]** セルをクリックして警告レベルをクリックします。  
  
    -   **[無効]** - 規則を無効にします (これは、規則 ID の横のチェック ボックスをオフにするのと同じです)。  
  
    -   **[警告]** - 規則を警告として表示します。  
  
    -   **[エラー]** - プロファイリングの実行を停止し、規則をエラーとして表示します。  
  
    -   **[情報]** - 規則を情報としてだけ表示します。