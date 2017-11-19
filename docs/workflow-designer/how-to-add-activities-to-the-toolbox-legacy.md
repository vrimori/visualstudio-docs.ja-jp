---
title: "方法: 活動ツールボックスに追加 (レガシ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b0dce8c2600d125a84044bef60957bd1bfa8b44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>方法: ツールボックスにアクティビティを追加する (レガシ)
従来のワークフロー ソリューションを構築するときに[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を対象とする、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]ワークフロー プロジェクトにカスタム活動項目を追加することができます、およびそのデザイナーに配置している、**ツールボックス**の簡単なアクセスします。 アクティビティを直接追加することも、**ツールボックス**ダイナミック リンク ライブラリ (DLL) からです。  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>DLL からツールボックスにアクティビティを追加するには  
  
1.  [ツールボックス] ウィンドウの画面を右クリックして**Windows ワークフロー**、順にクリック**アイテムの選択**です。  
  
2.  **ツールボックス アイテムの選択**ダイアログ ボックスで、をクリックして、 **[System.Activities コンポーネント**] タブをクリックして**参照**ウィンドウの下部の右側にします。  
  
3.  追加するカスタム アクティビティの実装が含まれているファイル ディレクトリから DLL を選択、**ツールボックス**、クリックして**開く**です。  
  
4.  をクリックして**OK**をツールボックスにアクティビティの追加を完了します。  
  
## <a name="see-also"></a>関連項目  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)