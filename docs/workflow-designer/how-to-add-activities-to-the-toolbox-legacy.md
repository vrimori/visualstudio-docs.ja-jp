---
title: 'ワークフロー デザイナー - 方法: 活動ツールボックスに追加 (レガシ)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>方法: ツールボックスにアクティビティを追加する (レガシ)

ワークフロー プロジェクトにカスタム活動項目を追加することができます、.NET Framework version 3.5、または、WinFX を対象とする従来の Windows ワークフロー デザイナーでワークフロー ソリューションをビルドするときにられ、そのデザイナーで、**ツールボックス**の簡単にアクセスできます。 アクティビティを直接追加することも、**ツールボックス**ダイナミック リンク ライブラリ (DLL) からです。

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>DLL からツールボックスにアクティビティを追加するには

1.  [ツールボックス] ウィンドウの画面を右クリックして**Windows ワークフロー**、順にクリック**アイテムの選択**です。

2.  **ツールボックス アイテムの選択**ダイアログ ボックスで、をクリックして、 **[System.Activities コンポーネント**] タブをクリックして**参照**ウィンドウの下部の右側にします。

3.  追加するカスタム アクティビティの実装が含まれているファイル ディレクトリから DLL を選択、**ツールボックス**、クリックして**開く**です。

4.  をクリックして**OK**をツールボックスにアクティビティの追加を完了します。

## <a name="see-also"></a>関連項目

- [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)