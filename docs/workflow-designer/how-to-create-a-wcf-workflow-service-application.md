---
title: 'ワークフロー デザイナー - 方法: WCF ワークフロー サービス アプリケーションの作成'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>WCF ワークフロー サービス アプリケーションを作成する方法

ワークフロー サービス アプリケーションの Windows Communication Foundation (WCF) は、分散型の通信サービス プロセス境界を越えてクライアントとの間のメッセージを渡すことです。 サービス側でサービス コントラクトの実装は、.NET Framework 3.5 の従来のワークフロー サービスと同様の方法で .NET Framework 4 ワークフロー アクティビティを介して宣言によって行われます。

## <a name="to-create-a-wcf-workflow-service-application"></a>WCF ワークフロー サービス アプリケーションを作成するには

1.  Visual Studio 2010 を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  **インストールされたテンプレート**ペインで、 **WCF**または**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**任意の言語に応じてグループ化します。

4.  中央のペインで選択**WCF ワークフロー サービス アプリケーション**です。

5.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

6.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

7.  **ソリューション**ボックスで、新しいソリューションを作成し、をクリックし、いずれかを選択**OK**です。

    > [!NOTE]
    > ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合は、Visual Studio 2010 でそのソリューションを開きで、ソリューションを右クリックして**ソリューション エクスプ ローラー**を選択して**追加**、し**新しいプロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。

8.  プロジェクト テンプレートによって、サービス定義が XAML として作成されます。 Windows ワークフロー デザイナーがデザイン ビューが表示されます、<xref:System.Activities.Statements.Sequence>のセットを含むアクティビティ<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>アクティビティ。

## <a name="see-also"></a>関連項目

- [アクティビティを作成する方法](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)