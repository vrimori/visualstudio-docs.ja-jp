---
title: 'ワークフロー デザイナー - 方法: ワークフロー コンソール アプリケーションの作成'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6461a644bdedd3d391059cd8a3a17f887e77c6b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970901"
---
# <a name="how-to-create-a-workflow-console-application"></a>ワークフロー コンソール アプリケーションを作成する方法

Windows Workflow Foundation (WF) では、システムまたは有人のプロセスを実行するためのワークフローを作成することができます。 Windows ワークフロー デザイナーでは、これらのワークフローを作成するため、デザイン画面を提供します。 ワークフロー デザイナーは、Visual Studio 内からワークフローを作成するために使用できますか、デザイナーを再ホストする他のアプリケーションに統合できます。

このトピックでは、Visual Studio 2010 で、ワークフロー デザイナーを使用して、コンソール アプリケーションでワークフローを作成する方法について説明します。

## <a name="to-create-a-workflow-console-application"></a>ワークフロー コンソール アプリケーションを作成するには

1.  Visual Studio 2010 を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** を選択します。

     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3.  **インストールされたテンプレート**ペインで、**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**に応じてグループの場合、言語の設定。

4.  中央のペインで選択**ワークフロー コンソール アプリケーション**です。

5.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。

6.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。

7.  **ソリューション**ボックスで、新しいソリューションの名前を入力します。 をクリックして**OK**アプリケーションを作成します。

    > [!NOTE]
    > ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合は、Visual Studio 2010 でそのソリューションを開きで、ソリューションを右クリックして**ソリューション エクスプ ローラー**を選択して**追加**、し**新しいプロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。

8.  プロジェクト テンプレートで XAML のワークフロー定義が作成され、コンソール アプリケーション定義がソース コードに記述されます。 ワークフロー デザイナーが開き、作成したワークフローのキャンバスを表示します。

9. ワークフローを作成するには、アクティビティから、またはその他のワークフロー項目をドラッグ、**ツールボックス**で、ワークフロー デザイン サーフェイスにします。

## <a name="see-also"></a>関連項目

- [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)