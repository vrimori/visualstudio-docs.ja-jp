---
title: ワークフロー デザイナー - 方法。定義およびアクティビティ デリゲートの使用
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 95aede6217bca263be7edd7440cc5e9bb23e25ab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908463"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>方法: ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する

.NET framework 4.5 には用の既製のデザイナーが含まれています、<xref:System.Activities.Statements.InvokeDelegate>アクティビティ。 このデザイナーを使用すると、<xref:System.Activities.ActivityDelegate> や <xref:System.Activities.ActivityAction> など、<xref:System.Activities.ActivityFunc%601> から派生するアクティビティにデリゲートを割り当てることができます。

## <a name="define-an-activity-delegate"></a>アクティビティ デリゲートの定義

1. Visual Studio で、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

2. **新しいプロジェクト**ダイアログ ボックスで、**ワークフロー** 、左側のカテゴリを選び、**ワークフロー コンソール アプリケーション**プロジェクト テンプレート。 (必要な) 場合、プロジェクトの名前を指定し、をクリックして**Ok**します。

   > [!NOTE]
   > 表示されない場合、**ワークフロー**カテゴリで、最初のインストール、 **Windows Workflow Foundation** Visual Studio 2017 のコンポーネント。 詳細については、次を参照してください。 [Windows Workflow Foundation のインストール](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)します。

3. プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しい項目の**します。 選択、**ワークフロー**カテゴリ、および選択し、**アクティビティ**項目テンプレート。 新しいアクティビティの名前**MyForEach.xaml**選び**OK**します。

   アクティビティがワークフロー デザイナーで開きます。

4. ワークフロー デザイナーで、クリックして、**引数**タブ。

5. クリックして**引数の作成**です。 新しい引数を名前**項目**します。

6. **引数の型**列で、 **[T] の配列**します。

7. 型ブラウザーで次のように選択します。**オブジェクト**選び**OK**。

8. クリックして**引数の作成**もう一度です。 新しい引数を名前**本文**します。 **方向**選択、新しい引数は列**プロパティ**します。

9. 引数の型の列で、選択**型の参照**

10. 型ブラウザーで、入力**ActivityAction**で、**型名**フィールド。 選択**ActivityAction\<T >** ツリー ビュー。 選択**オブジェクト**タイプを割り当てるために表示されるドロップダウン リストで**ActivityAction\<オブジェクト >** 引数にします。

11. ドラッグ、<xref:System.Activities.Statements.While>からのアクティビティ、**制御フロー**デザイナー画面に、ツールボックスのセクション。

12. 選択、<xref:System.Activities.Statements.While>アクティビティ、および選択、**変数**タブ。

13. 選択**変数作成**です。 新しい変数の名前**インデックス**します。

14. **変数の型**列で、 **Int32**します。 ままに、**スコープ**として**中**、および**既定**列は空白です。

15. 設定、**条件**のプロパティ、<xref:System.Activities.Statements.While>アクティビティを**インデックス < Items.Length;** します。

16. ドラッグ、<xref:System.Activities.Statements.InvokeDelegate>からのアクティビティ、**プリミティブ**、ツールボックスのセクション、**本文**の<xref:System.Activities.Statements.While>アクティビティ。

17. 選択**本文**デリゲートのドロップダウンから。

18. **プロパティ**のグリッド、<xref:System.Activities.Statements.InvokeDelegate>アクティビティ、クリックして、 **.** ボタン、**デリゲート引数**プロパティ。

19. **値**という名前の引数の列**引数**、入力**Items [Index]** します。 クリックして**Ok**を閉じる、 **DelegateArguments**ダイアログ。

20. <xref:System.Activities.Statements.Assign> アクティビティを <xref:System.Activities.Statements.InvokeDelegate> アクティビティの下の水平線にドラッグします。 <xref:System.Activities.Statements.Assign>アクティビティを作成すると、および<xref:System.Activities.Statements.Sequence>で 2 つのアクティビティを格納するアクティビティが自動的に作成、**本文**のセクション、 **MyForEach**アクティビティ。 以降、シーケンスが必要な**本文**セクションがのみ 1 つのアクティビティを含めることができます。 自動的に新しいを作成する<xref:System.Activities.Statements.Sequence>アクティビティは、.NET Framework 4.5 の新機能です。

21. 設定、**に**のプロパティ、<xref:System.Activities.Statements.Assign>アクティビティを**インデックス**します。 設定、**値**のプロパティ、**割り当てる**アクティビティを**インデックス + 1**します。

    カスタム**MyForEach**アクティビティは、任意のアクティビティから渡される各値に対して 1 回を呼び出し、**項目**アクティビティの入力として、コレクション内の値のコレクション。

## <a name="use-the-custom-activity-in-a-workflow"></a>ワーク フローでのカスタム アクティビティの使用

1.  キーを押してプロジェクトをビルド**Ctrl**+**Shift**+**B**します。

2.  **ソリューション エクスプ ローラー**オープン**Workflow1.xaml**デザイナー。

3.  ドラッグ、 **MyForEach**アクティビティをツールボックスからデザイナー画面にします。 このアクティビティは、プロジェクトと同じ名前で、ツールボックスのセクションでは。

4.  設定、**項目**のプロパティ、 **MyForEach**アクティビティを**new object[] {1,"abc"}** します。

5.  ドラッグ、<xref:System.Activities.Statements.WriteLine>からのアクティビティ、**プリミティブ**、ツールボックスのセクション、 **Delegate:body**のセクション、 **MyForEach**アクティビティ。

6.  設定、**テキスト**のプロパティ、<xref:System.Activities.Statements.WriteLine>アクティビティを**Argument.ToString()** します。

ワークフローを実行すると、次の出力がコンソールに表示されます。

**1**
**abc**