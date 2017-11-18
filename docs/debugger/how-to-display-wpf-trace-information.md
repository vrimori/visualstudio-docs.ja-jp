---
title: "方法: WPF トレース情報の表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe00aff9834d612702c61f06a1d0c924852c9462
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-display-wpf-trace-information"></a>方法: WPF トレース情報を表示する
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]WPF アプリケーションからデバッグ トレース情報を受信してでその情報を表示できます、**出力**ウィンドウです。 デバッグ トレース情報を表示するには、WPF トレースを有効にする必要があります。  
  
 WPF トレースは、App.Config ファイルで、または <xref:System.Diagnostics.PresentationTraceSources> クラスを使用してプログラムによって有効にすることができます。 WPF トレースを有効にする簡単な方法を使用して、**オプション**ウィンドウです。 Web アプリケーション用の WPF トレースはサポートされていません。  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF トレース情報を有効にする、またはカスタマイズするには  
  
1.  **[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **オプション**ダイアログ ボックスで、左側のボックスで、開く、**デバッグ**ノード。  
  
3.  **デバッグ**をクリックして**出力ウィンドウ**します。  
  
4.  **出力の全般設定****すべてのデバッグ出力**です。  
  
5.  右側のボックスで、検索**WPF トレース設定**です。  
  
6.  開く、 **WPF トレース設定**ノード。  
  
7.  **WPF トレース設定**を有効に設定のカテゴリをクリックして (たとえば、**データ バインディングの**)。  
  
     横に表示設定 列で、ドロップダウン リスト コントロール**データ バインディングの**クリックしたカテゴリまたはします。  
  
8.  ドロップダウン リストをクリックし、表示するトレース情報の種類の選択:**すべて**、**重大**、**エラー**、**警告**、 **情報**、 **Verbose**、または**ActivityTracing**です。  
  
     **重要な**重大なイベントのみの追跡を有効にします。  
  
     **エラー**重大なエラー イベントの追跡を有効にします。  
  
     **警告**致命的、エラーのトレースおよび警告イベントを有効にします。  
  
     **情報**"重大"、エラー、警告、および情報イベントの追跡を有効にします。  
  
     **Verbose** "重大"、エラー、警告、情報、および Verbose のイベントの追跡を有効にします。  
  
     **ActivityTracing**停止、開始、中断、転送、および再開イベントの追跡を有効にします。  
  
     これらのトレース情報レベルが持つ意味の詳細については、「<xref:System.Diagnostics.SourceLevels>」を参照してください。  
  
9. **[OK]** をクリックします。  
  
### <a name="to-disable-wpf-trace-information"></a>WPF トレース情報を無効にするには  
  
1.  **[ツール]** メニューの **[オプション]** を選択します。  
  
2.  **オプション**ダイアログ ボックスで、左側のボックスで、開く、**デバッグ**ノード。  
  
3.  **デバッグ**をクリックして**出力ウィンドウ**します。  
  
4.  右側のボックスで、検索**WPF トレース設定**です。  
  
5.  開く、 **WPF トレース設定**ノード。  
  
6.  **WPF トレース設定**を有効に設定のカテゴリをクリックして (たとえば、**データ バインディングの**)。  
  
     横に表示設定 列で、ドロップダウン リスト コントロール**データ バインディングの**クリックしたカテゴリまたはします。  
  
7.  ドロップダウン リストをクリックし、選択**オフ**です。  
  
8.  **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [WPF のデバッグ](../debugger/debugging-wpf.md)