---
title: '方法: ツールボックス (レガシ) にアクティビティを追加する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0bcd5f525dfb0794f06b5210287251feb883b340
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539067"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>方法: ツールボックスにアクティビティを追加する (レガシ)
従来のワークフロー ソリューションを構築するときに[!INCLUDE[wfd1](../includes/wfd1-md.md)]を対象とする、[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]または[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]、カスタム アクティビティをワークフロー プロジェクトに追加でき、そのデザイナーに配置、**ツールボックス**の簡単なアクセスします。 アクティビティを直接追加することも、**ツールボックス**ダイナミック リンク ライブラリ (DLL) から。  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>DLL からツールボックスにアクティビティを追加するには  
  
1.  ツールボックス ウィンドウの画面を右クリックして**Windows ワークフロー**、 をクリックし、**アイテムの選択**。  
  
2.  **ツールボックス アイテムの選択**ダイアログ ボックスで、 をクリックして、 **System.Activities コンポーネント** タブをクリックして**参照**ウィンドウの下部右側にあるからです。  
  
3.  追加するカスタム アクティビティの実装を格納するファイルのディレクトリから DLL を選択、**ツールボックス**、 をクリックし、**オープン**します。  
  
4.  クリックして**OK**をツールボックスにアクティビティの追加を完了します。  
  
## <a name="see-also"></a>関連項目  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)