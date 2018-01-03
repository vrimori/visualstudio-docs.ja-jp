---
title: "方法: パフォーマンス データ ファイル名のオプションを設定する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 309cf7f8fe93cdfca355ff55f54e2247e80068cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-performance-data-file-name-options"></a>方法: パフォーマンス データ ファイル名のオプションを設定する
既定では、次の構文を使用してプロファイル データ (.vsp) ファイルを保存します。  
  
 *Path\VSP-File\YYMMDD(N)* **.vsp**  
  
 いずれの名前付けパラメーターも、パフォーマンス セッションのプロパティ ダイアログ ボックスの [全般] ページで変更できます。  
  
 **必要条件**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、 [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
|||  
|-|-|  
|*Path*|レポートを格納するディレクトリ。 既定の場所は、ソリューション フォルダーか、ユーザーのプロジェクトおよびソリューションの既定の場所です。|  
|*VSP-File*|プロファイル データ ファイルの名前。 既定の名前は、プロファイルされるソリューションまたは実行可能ファイルの名前です。|  
|*YYMMDD*|プロファイル データが収集された年月日を示す日付スタンプ。|  
|*(N)*|複数のプロファイル データ ファイルが存在する場合、かっこで囲まれたインクリメント数がファイル名に追加されます。|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>パフォーマンス セッションのプロファイル データ ファイルの名前付け構文を変更するには  
  
1.  **パフォーマンス エクスプローラー**で、パフォーマンス セッションの名前を右クリックして、**[プロパティ]** をクリックします。  
  
2.  **[全般]** をクリックします。  
  
3.  **[レポート]** で、以下のいずれかの設定を変更します。  
  
    |||  
    |-|-|  
    |**レポートの場所**|プロファイル データ ファイルを格納するディレクトリを指定します。|  
    |**レポート名**|ファイルの基本名を指定します。|  
    |**新しいレポートをセッションに自動的に追加**|パフォーマンス セッションにデータ ファイルを自動的に追加するには、チェック ボックスをオンにします。|  
    |**生成されたレポートにインクリメンタル数を追加**|同じ名前のファイルが複数存在する場合に、ファイル名にインクリメント数を追加するにはチェック ボックスを選択します。 既存のファイルを上書きするには、チェック ボックスをオフにします。|  
    |**番号にタイムスタンプを使用**|ファイル名に日付スタンプを追加するには、チェック ボックスをオンにします。|