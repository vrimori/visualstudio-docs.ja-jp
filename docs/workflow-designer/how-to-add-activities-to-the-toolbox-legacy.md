---
title: "方法: 活動ツールボックスに追加 (レガシ) |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d6d7e817ae34b3e39d617ad5d12802cabd5cedc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>方法: ツールボックスにアクティビティを追加する (レガシ)
対象とする従来の Windows ワークフロー デザイナーでワークフロー ソリューションを構築するときに、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]ワークフロー プロジェクトにカスタム活動項目を追加することができます、およびそのデザイナーに配置している、**ツールボックス**の簡単にアクセスできます。 アクティビティを直接追加することも、**ツールボックス**ダイナミック リンク ライブラリ (DLL) からです。

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>DLL からツールボックスにアクティビティを追加するには

1.  [ツールボックス] ウィンドウの画面を右クリックして**Windows ワークフロー**、順にクリック**アイテムの選択**です。

2.  **ツールボックス アイテムの選択**ダイアログ ボックスで、をクリックして、 **[System.Activities コンポーネント**] タブをクリックして**参照**ウィンドウの下部の右側にします。

3.  追加するカスタム アクティビティの実装が含まれているファイル ディレクトリから DLL を選択、**ツールボックス**、クリックして**開く**です。

4.  をクリックして**OK**をツールボックスにアクティビティの追加を完了します。

## <a name="see-also"></a>関連項目

- [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)