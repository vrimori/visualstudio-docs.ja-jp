---
title: ワークフロー デザイナー - 方法。ワークフロー プロジェクトに新しい項目を追加する
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0e5df48d1c96905c022a6737d58f75d6c548ccb
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53738690"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>方法: ワークフロー プロジェクトへ新しい項目を追加します。

ワークフロー プロジェクトを作成したら、ワークフロー アクティビティ、デザイナー、およびその他の一般的な Visual Studio 項目をプロジェクトに追加できます。

次の表では、ワークフロー プロジェクトに追加できる Windows Workflow Foundation (WF) の項目を示します。


| 名前 | 説明 |
|-| - |
| アクティビティ | 他のアクティビティで構成されるアクティビティ。 この項目を選択を選択するときに取得される、プロジェクトに同じ XAML ファイルを追加、**アクティビティ ライブラリ**新しいプロジェクトのテンプレート。 この手順の詳細については、次を参照してください。[ワークフロー プロジェクトを作成する](creating-a-workflow-project.md)します。 |
| アクティビティ デザイナー | アクティビティのデザイン時の操作をカスタマイズするデザイナー。 この項目を選択を選択するときに取得される、プロジェクトに同じファイルを追加、**アクティビティ デザイナー ライブラリ**新しいプロジェクトのテンプレート。 |
| Code アクティビティ | コードに記述される実行ロジックを含むアクティビティ。 <xref:System.Activities.CodeActivity.Execute%2A> メソッドのオーバーライドを含むソース コード ファイルは既に自動的に生成されています。 |
| WCF ワークフロー サービス | ワークフロー アクティビティを使用して作成された [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] サービス。 この項目を選択を選択するときに取得される、プロジェクトに同じファイルを追加、 **WCF ワークフロー サービス アプリケーション**新しいプロジェクトのテンプレート。 この手順の詳細については、次を参照してください。[方法。WCF ワークフロー サービス アプリケーションの作成](/visualstudio/workflow-designer/creating-a-workflow-project)です。 |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには

1. **[プロジェクト]** メニューで **[新しい項目の追加]** を選択します。

   **[新しい項目の追加]** ダイアログ ボックスが開きます。

1. 左側のウィンドウで、選択、**ワークフロー**カテゴリ、およびワークフローの項目テンプレートを選択します。

   > [!NOTE]
   > 表示されない場合、**ワークフロー**カテゴリで、最初のインストール、 **Windows Workflow Foundation** Visual Studio 2017 のコンポーネント。 詳細については、次を参照してください。 [Windows Workflow Foundation のインストール](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)します。

1. 内の項目の名前を入力、**名前** ダイアログ ボックスの下部にあるボックス。

1. 選択**追加**をプロジェクトに項目を追加します。

## <a name="see-also"></a>関連項目

- [ワークフロー プロジェクトを作成します。](../workflow-designer/creating-a-workflow-project.md)